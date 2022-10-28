**Project 24：Night Lamp**

**1.Introduction**

Sensors or components are ubiquitous in our daily life. For example,
some public street lamps will automatically turn on at night and turn
off during the day. In fact, this make use of a photosensitive element
that senses the intensity of external ambient light. When the outdoor
brightness decreases at night, the street lights will turn on
automatically. In the daytime, the street lights will automatically turn
off.

In this project, we use a ESP32 to control a LED to achieve the effect
of the street light.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/d8beaf7391033a5f6ba4600791f8c348.jpeg" style="width:1.38681in;height:0.67708in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.6in;height:1.47083in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/ef77f5a64c382157fc2dea21ec373fef.png" style="width:0.29514in;height:1.25903in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/b395b1cd2678f87b3a34dec15659efbc.png" style="width:0.22431in;height:1.00556in" /></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>Red LED*1</td>
<td>10KΩResistor*1</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/9e553e75b6f976f33438171eb2f2e775.png" style="width:0.19097in;height:1.26597in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/845d05a6108b1662b828610ba9dcb788.png" style="width:0.25833in;height:1.13681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:0.77222in;height:0.77986in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:0.99028in;height:0.52986in" /></td>
<td></td>
</tr>
<tr class="even">
<td>Photoresistor*1</td>
<td>220ΩResistor*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
<td></td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**

![](/media/9e553e75b6f976f33438171eb2f2e775.png)

**Photoresistor :** It is a kind of photosensitive resistor, its
principle is that the photoresistor surface receives brightness (light)
to reduce the resistance, the resistance value will change with the
detected intensity of the ambient light . With this characteristic, we
can use the photoresistor to detect the light intensity. Photoresistor
and its electronic symbol are as follows：

![](/media/7d575da675a2f6cb511d28b801e2abaa.png)

The following circuit is used to detect changes in resistance values of
photoresistors：

![](/media/5a7f7e641eb78007760a94151c1d80a5.png)

In the circuit above, when the resistance of the photoresistor changes
due to the change of light intensity, the voltage between the
photoresistor and resistor R2 will also change.  Thus, the intensity of
light can be obtained by measuring this voltage.

4.  **Read the values of the photoresistor**

We first use a simple code to read the ADC value, DAC value and voltage
value of the photoresistor and print them out. Please refer to the
following wiring diagram：

![](/media/b762098c798beb08e4d433137c317dc7.png)

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : Read Photosensitive Analog Value</p>
<p>* Description : Basic usage of ADC</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 36 //the pin of the photosensitive sensor</p>
<p>void setup() </p>
<p>//In loop()，the analogRead() function is used to obtain the ADC value,</p>
<p>//and then the map() function is used to convert the value into an 8-bit precision DAC value.</p>
<p>//The input and output voltage are calculated according to the previous formula,</p>
<p>//and the information is finally printed out.</p>
<p>void loop() </p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable, open the serial monitor and set
the baud rate to 115200 and press the reset button first.

You will see that the serial monitor window will print out the ADC
value、DAC value and voltage value of the photoresistor. When the light
intensity around the photoresistor is gradually reduced, the ADC value,
DAC value and voltage value will gradually increase. On the contrary,
the ADC value, DAC value and voltage value decrease gradually.

![](/media/36d48be9ba9a78c2e1ce41fb0c35cd46.png)

5.  **Wiring diagram of the light-controlled lamp：**

Now we will make a light controlled lamp. The principle is the same as
the small dimming lamp , that is, the ESP32 takes the analog values of
the sensor, and then adjusts the brightness of the LED.

![](/media/77a0c534501f51e7fe7aa221e4db71d9.png)

6.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Night Lamp</p>
<p>* Description : Controlling the brightness of LED by photosensitive sensor.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 36 // the pin of the photosensitive sensor</p>
<p>#define PIN_LED 15 // the pin of the LED</p>
<p>#define CHAN 0</p>
<p>#define LIGHT_MIN 372</p>
<p>#define LIGHT_MAX 2048</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

7.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that when the
intensity of light around the photoresistor is reduced, the LED will be
bright, on the contrary, the LED will be dim.
