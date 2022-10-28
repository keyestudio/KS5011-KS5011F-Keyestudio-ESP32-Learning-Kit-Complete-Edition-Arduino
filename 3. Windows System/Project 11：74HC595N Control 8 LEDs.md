## Project 11：74HC595N Control 8 LEDs 

1.  **Introduction**

In previous projects, we learned how to light up an LED.

With only 32 IO ports on ESP32, how do we light up a lot of
leds? Sometimes it is possible to run out of pins on the ESP32, and you
need to extend it with the shift register.You can use the 74HC595N chip
to control 8 outputs at a time, taking up only a few pins on your
microcontroller. In addition, you can also connect multiple registers
together to further expand the output.

In this project, we will use a ESP32，a 74HC595 chip and LEDs to make a
flowing water light to understand the function of the 74HC595 chip.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/2a55dec25d757def2b46d5e9cd9c97e5.jpeg" style="width:1.75972in;height:0.85833in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.63889in;height:1.56667in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/f97e58ab51ec0a274ff3e72e08a7d55d.png" style="width:1.07847in;height:0.88611in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.98958in;height:0.95139in" /></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>74HC595N chip*1</td>
<td>Jumper Wires</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:1.22639in;height:0.49236in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/3ec5906fad2172708d449390140f55e6.png" style="width:0.28056in;height:1.19722in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
<td></td>
</tr>
<tr class="even">
<td>220ΩResistor*8</td>
<td>Red LED*8</td>
<td>USB Cable*1</td>
<td></td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**

![](/media/6921c6d60135e072ed4bd24564ec4a6d.png)

**74HC595N Chip:** To put it simply, 74HC595N chip is a combination of
8-digit shifting register, memorizer and equipped with tri-state output.
The shift register and the memorizer are synchronized to different
clocks, and the data is input on the rising edge of the shift register
clock SCK and goes into the memory register on the rising edge of the
memory register clock RCK.

If the two clocks are connected together, the shift register is always
one pulse earlier than the storage register. The shift register has a
serial shift input (SI) and a serial output (SQH) for cascading. The
8-bit shift register can be reset asynchronously (low-level reset), and
the storage register has an 8-bit Three-state parallel bus output, when
the output enable (OE) is enabled (active low), the storage register is
output to the 74HC595N pin (bus).

![](/media/858b189f06ad68afe051b15043b2affd.png)

**Pins**：

<table>
<tbody>
<tr class="odd">
<td>Pin13 OE</td>
<td>It is an output enable pin to ensure that the data of the latch is input to the Q0 to Q7 pins or not. When it is low, no high level is output. In this experiment, we directly connect to GND and keep the data output low.</td>
</tr>
<tr class="even">
<td>Pin14 SI</td>
<td>This is the pin for 74HC595 to receive data, i.e. serial data input, only one bit can be input at a time, then 8 times in a row, it can form a byte.</td>
</tr>
<tr class="odd">
<td>Pin10 SCLR</td>
<td>A pin to initialize the storage register pins. It initializes the internal storage registers at a low level. In this experiment, we connect VCC to maintain a high level.</td>
</tr>
<tr class="even">
<td>Pin11 SCK</td>
<td>The clock pin of the shift register. At the rising edge, the data in the shift register is shifted backward as a whole, and new data input is received.</td>
</tr>
<tr class="odd">
<td>Pin12 RCK</td>
<td>The clock input pin of the storage register . At the rising edge, the data is transferred from the shift register to the storage register. At this time, the data is output in parallel from the Q0 to Q7 ports.</td>
</tr>
<tr class="even">
<td>Pin9 SQH</td>
<td>It is a serial output pin dedicated for chip cascading to the SI terminal of the next 74HC595.</td>
</tr>
<tr class="odd">
<td>Q0--Q7(Pin 15,Pin1-7)</td>
<td>Eight-bit parallel output, can directly control the 8 segments of the digital tube.</td>
</tr>
</tbody>
</table>

**4.** **Wiring Diagram**

Note: Pay attention to the direction in which the 74HC595N chip is
inserted.

![](/media/a6d03617539b70d6d69fa7e9acb25be9.png)

![](/media/11a03579b6cf94599f00554bfe014a3b.png)

**5. Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//************************************************************************</p>
<p>/*</p>
<p>* Filename : 74HC595N Control 8 LEDs</p>
<p>* Description : Use 74HC575N to drive ten leds to display the flowing light.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>int dataPin = 14; // Pin connected to DS of 74HC595(Pin14)</p>
<p>int latchPin = 12; // Pin connected to ST_CP of 74HC595(Pin12)</p>
<p>int clockPin = 13; // Pin connected to SH_CP of 74HC595(Pin11)</p>
<p>void setup() </p>
<p>void loop() </p>
<p>delay(100);</p>
<p>x = 0x80; //0b 1000 0000</p>
<p>for (int j = 0; j &lt; 8; j++) </p>
<p>delay(100);</p>
<p>}</p>
<p>void writeTo595(int order, byte _data ) </p>
<p>//************************************************************************</p></td>
</tr>
</tbody>
</table>

6.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that the 8 LEDs
start flashing in flowing water mode.
