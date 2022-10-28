**Project 07: Flowing Water Light**

1.  **Introduction**

In our daily life, we can see many billboards composed of different
colors of LED. They constantly change the light (like water) to attract
customers' attention. In this project, we will use ESP32 to control 10
leds to achieve the effect of flowing water.

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
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7eb361d680dfa351f07f8527aeb37abd.png" style="width:0.275in;height:1.17361in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:1.22639in;height:0.49236in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.66736in;height:0.64097in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>Red LED*1</td>
<td>220Ω Resistor*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Wiring Diagram**

![](/media/548f889607bdb0ce017c58f323c85dfa.png)

**Note:**

How to connect a LED

![](/media/42ff6f405dfa128593827de5aa03e94b.png)

How to identify the 220Ω Five-band resistor

![](/media/55c0199544e9819328f6d5778f10d7d0.png)

4.  **Test Code**

This project is designed to make a flowing water lamp. Actions: First
turn LED \#1 on, then turn it off. Then turn LED \#2 on, and then turn
it off... and repeat the same to all 10 LEDs until the last LED turns
off. This process is repeated to achieve the“movements”of flowing water.

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : Flowing Water Light</p>
<p>* Description : Using ten leds to demonstrate flowing lamp.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>byte ledPins[] = ;</p>
<p>int ledCounts;</p>
<p>void setup() </p>
<p>}</p>
<p>void loop() </p>
<p>for (int i = ledCounts - 1; i &gt; -1; i--) </p>
<p>}</p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

5.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that 10 LEDs
will light up from left to right and then back from right to left.

![](/media/912e2c3f88b522b89b9935548bae3bd9.png)
