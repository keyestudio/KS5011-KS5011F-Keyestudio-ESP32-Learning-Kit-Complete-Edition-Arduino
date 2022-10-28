## Project 06: RGB LED

1.  **Introduction**

![](/media/94bdff69e438989d8e0934e57f2e5c00.png)

RGB is composed of three colors (red, green and blue), which can emit
different colors by mixing these three colors.

In this project, we will introduce the RGB and show you how to use ESP32
to control the RGB to emit different color lights.

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
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/f1a86fc81ab4b043263ce7e01e14d470.png" style="width:0.23056in;height:1.27847in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:1.22639in;height:0.49236in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.66736in;height:0.64097in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>RGB LED*1</td>
<td>220Ω Resistor*3</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

**3. Component Knowledge**

Most monitors adopt the RGB color standard, and all colors on a computer
screen are a mixture of red, green and blue in varying proportions.

![](/media/8bf1339719a922f2fbc1e01a4347b4ab.png)

This RGB LED has 4 pins, with each color (red, green, blue) and a common
cathode. To change its brightness, we can use the PWM of the ESP32 pins,
which can give different duty cycle signals to the RGB to produce
different colors of light.

If we use three 10-bit PWM to control the RGB, in theory, we can create
2 <sup>10</sup>\*2<sup>10</sup>\*2<sup>10</sup> =1,073,741,824(1billion)
colors through different combinations.

4.  **Wiring Diagram**

![](/media/f3deb3502985ac8d66e99e4f27b3de1e.png)

**Note:**

The longest pin of RGB LED (common cathode) is connected to GND.

![](/media/1584356c63bf99934ae0810ee02dced3.png)

How to identify the 220Ω Five-band resistor

![](/media/55c0199544e9819328f6d5778f10d7d0.png)

5.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//*****************************************************************************/*</p>
<p>* Filename : RGB LED</p>
<p>* Description : Use RGBLED to show random color.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>int ledPins[] = ; //define red, green, blue led pins</p>
<p>const byte chns[] = ; //define the pwm channels</p>
<p>int red, green, blue;</p>
<p>void setup() </p>
<p>}</p>
<p>void loop() </p>
<p>void setColor(byte r, byte g, byte b) </p>
<p>//*****************************************************************************</p></td>
</tr>
</tbody>
</table>

6.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that the RGB
LED starts to display random colors.
