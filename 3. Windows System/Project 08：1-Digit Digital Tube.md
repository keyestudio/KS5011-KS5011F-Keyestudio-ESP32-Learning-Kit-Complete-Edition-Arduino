**Project 08：1-Digit Digital Tube**

1.  **Introduction**

The 1-Digit 7-Segment display is an device that displays decimal
numbers, which is widely used in digital clocks, electronic meters,
basic calculators and other electronic devices that display digital
information. In this project, we will use ESP32 to control 1-Digit
7-segment display to display numbers.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:2.17847in;height:1.0625in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.95208in;height:2.33472in" /></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/f52aeaa1de53c2e89338b2f42da4b029.png" style="width:0.52847in;height:0.58958in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:1.22639in;height:0.49236in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.66736in;height:0.64097in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>1-Digit 7-Segment Display*1</td>
<td>220Ω Resistor*8</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

**3. Component Knowledge**

![](/media/e44a0f27beec739ee13e68c04865989f.png)

**1-Digit 7-Segment Display:** It is a semiconductor light emitting
device, and its basic unit is a light-emitting diode (LED). The digital
tube display can be divided into 7-segment display and 8-segment display
according to the number of segments.

The 8-segment display has one more LED unit than the 7-segment display
(used for decimal point display). Each segment of the 7-segment display
is a separate LED. According to the connection mode of the LED unit, the
digital tube can be divided into a common anode digital tube and a
common cathode digital tube.

In the common cathode 7-segment display, all the cathodes (or negative
pole) of the segmented LEDs are connected together, so you should
connect the common cathode to GND. If you are about to light up a
segmented LED, you can set its associated pin to“HIGH”.

In the common anode 7-segment display, the LED anodes (positive pole) of
all segments are connected together, so you should connect the common
anode to“+5V”. If you are about to light up a segmented LED, you can set
its associated pin to“LOW”.

![](/media/28fd057848fbe0e8c8e3362768e7aa44.png)

Each part of the digital tube is composed of an LED. So when you use it,
you also need to use a current limiting resistor. Otherwise, the LED
will be damaged. In this experiment, we will use an ordinary common
cathode one-digit digital tube. As we mentioned above, you should
connect the common cathode to GND. If you are about to light up a
segmented LED, you can set its associated pin to“HIGH”.

**4.****Wiring Diagram**

Note:The direction of the 7-segment display inserted into the breadboard
is consistent with the wiring diagram, with one more point in the lower
right corner.

![](/media/631ee0861da60ed02d191de0e0e210d9.png)

![](/media/5f01d1eea2bb207f19dee4f437f93bc8.png)

5.  **Test Code**

The digital display is divided into 7 segments, and the decimal point
display is divided into 1 segment. When certain numbers are displayed,
the corresponding segment will be lit. For example, when the number 1 is
displayed, segments b and c will be turned on.

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : 1-Digit Digital Tube</p>
<p>* Description : One Digit Tube displays numbers from 9 to 0.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>// sets the IO PIN for every segment</p>
<p>int a=16; // digital PIN 16 for segment a</p>
<p>int b=4; // digital PIN 4 for segment b</p>
<p>int c=5; // digital PIN 5 for segment c</p>
<p>int d=18; // digital PIN 18 for segment d</p>
<p>int e=19; // digital PIN 19 for segment e</p>
<p>int f=22; // digital PIN 22 for segment f</p>
<p>int g=23; // digital PIN 23 for segment g</p>
<p>int dp=17; // digital PIN 17 for segment dp</p>
<p>void digital_0(void) // displays number 0</p>
<p></p>
<p>void digital_1(void) // displays number 1</p>
<p></p>
<p>void digital_2(void) // displays number 2</p>
<p></p>
<p>void digital_3(void) // displays number 3</p>
<p></p>
<p>void digital_4(void) // displays number 4</p>
<p></p>
<p>void digital_5(void) // displays number 5</p>
<p></p>
<p>void digital_6(void) // displays number 6</p>
<p></p>
<p>void digital_7(void) // displays number 7</p>
<p></p>
<p>void digital_8(void) // displays number 8</p>
<p></p>
<p>void digital_9(void) // displays number 9</p>
<p></p>
<p>void setup()</p>
<p></p>
<p>void loop()</p>
<p>}</p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

6.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that the
1-Digit 7-Segment display will display numbers from 9 to 0.
