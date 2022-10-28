**Project 10：8×8 Dot-matrix Display**

1.  **Introduction**

Dot matrix display is an electronic digital display device that can
display information on machine, clocks, public transport departure
indicators and many other devices. In this project, we will use ESP32 to
control 8x8 LED dot matrix to display digits.

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
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/d226a1f3c801ac78321f0692143c853e.png" style="width:1.09375in;height:1.05208in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:0.90833in;height:0.23681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:1.03333in;height:1.02708in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>8*8 dot matrix module*1</td>
<td>220Ω Resistor*8</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**

**8\*8 dot matrix module：**The 8\*8 dot matrix is composed of 64 LEDs,
including row common anode and row common cathode. Our module is row
common anode, each row has a line connecting the positive pole of the
LED, and the column is connecting the negative pole of the LED lamp, as
shown in the following figure :

![](/media/69c719a7898907ab32f089f0cbbaff13.png)

![](/media/bcfa2498367eaf9c7733da15af32eae7.png)

4.  **Wiring Diagram**
    
    ![](/media/af4d73ef798a933228f16dedc6578b8e.png)

5.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : 8×8 Dot-matrix Display</p>
<p>* Description : 8×8 Dot-matrix displays numbers from 0 to 9.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>int R[] = ;</p>
<p>int C[] = ;</p>
<p>unsigned char data_0[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_1[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_2[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_3[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_4[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_5[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_6[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_7[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_8[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>unsigned char data_9[8][8] =</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>void Display(unsigned char dat[8][8])</p>
<p></p>
<p>delay(1);</p>
<p>Clear();</p>
<p>}</p>
<p>}</p>
<p>void Clear()</p>
<p></p>
<p>}</p>
<p>void setup()</p>
<p>}</p>
<p>void loop()</p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>for (int i = 1; i &lt;= 100; i = i + (1)) </p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

6.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that the 8\*8
dot matrix displays the numbers 0\~9 respectively.
