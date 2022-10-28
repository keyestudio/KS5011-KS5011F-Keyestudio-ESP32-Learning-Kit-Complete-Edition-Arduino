**Project 29：Temperature Instrument**

1.  **Introduction**
    
    Thermistor is a kind of resistor whose resistance depends on
    temperature changes, which is widely used in gardening, home alarm
    systems and other devices. Therefore, we can use the features to
    make a temperature instrument.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:1.59722in;height:0.77986in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.69306in;height:1.7in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/b45bb81bb3763377c63accce606ac5f2.png" style="width:0.25in;height:1.11597in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/b395b1cd2678f87b3a34dec15659efbc.png" style="width:0.22431in;height:1.00556in" /></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>Thermistor*1</td>
<td>10KΩResistor*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/74ca4fa6d49dbd04de6a603c6e55a9ee.png" style="width:1.15347in;height:0.9625in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/9232141f8a3166a8a6cdd43b78edd4e3.png" style="width:1.52014in;height:0.73264in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:1.10139in;height:1.03472in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:0.99028in;height:0.52986in" /></td>
</tr>
<tr class="even">
<td>M-F Dupont Wires</td>
<td>LCD 128X32 DOT*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**

**Thermistor:** It is a temperature sensitive resistor. When it senses a
change in temperature, the resistance of the thermistor will change. We
can take advantage of this characteristic to detect temperature
intensity. The thermistor and its electronic symbol are shown below:

![](/media/809b8634747fb295021f12e3b92b7894.png)

The relationship between resistance and temperature of the thermistor
is：

**Rt** is the thermistor resistance under T2 temperature;

**R** is the nominal resistance of thermistor under T1 temperature;

**EXP\[n\]** is nth power of e;

**B** is temperature index;

**T1, T2** is Kelvin temperature (absolute temperature). Kelvin
temperature=273.15 + Celsius temperature.

**Parameters** : B=3950, R=10k, T1=25.

The circuit connection method of the thermistor is similar to the
photoresistor, as shown below：

![](/media/b0f80e9bd350a8b7390a73756ac1ac8c.jpeg)

We can use the value measured by the ADC converter to obtain the
resistance of thermistor, and then we can use the formula to obtain the
temperature value.

Therefore, the temperature formula can be derived as:：

4.  **Read the value of the thermistor**

First we will learn the thermistor reading the current ADC value,
voltage value and temperature value and print them out. Please connect
the wirings according to the wiring diagram below：

![](/media/806fd81bf8a761b4ae1a638489c426ce.png)

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : Thermomter</p>
<p>* Description : Making a thermometer by thermistor.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 36</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable, open the serial monitor and set
the baud rate to 115200 and press the reset button first.

You will see that the monitor prints out the thermistor's current ADC
value, voltage value and temperature value. Try pinching the thermistor
with your index finger and thumb (don't touch wires) for a while, and
you will see the temperature increasing.

![](/media/0e4350465e1899e6eeee27b899a7f140.png)

5.  **Wiring diagram of the temperature instrument**

![](/media/5a437bfdcad012211e15cab54e35dad7.png)

**6. Adding the lcd128\_32\_io library**

Open the Arduino IDE，click “Sketch”→“Include Library”→“Add .ZIP
Library...”. In the pop-up window, find the file named **“2. Windows
System\\2. C\_Tutorial\\3. Libraries\\LCD\_128X32.ZIP”,** which locates
in this directory. Select the **LCD\_128X32.ZIP** file and then click
“Open”.

![](/media/f1dbbf38e15881e76873e72dbb13dbd7.png)

![](/media/883132fcf9c54c91ba496ffe7491170c.png)

**7. Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : Temperature Instrument</p>
<p>* Description : LCD displays the temperature of thermistor.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include "lcd128_32_io.h"</p>
<p>#define PIN_ANALOG_IN 36</p>
<p>lcd lcd(21, 22); //Create lCD128 *32 pin，sda-&gt;21， scl-&gt;22</p>
<p>void setup() </p>
<p>char string[10];</p>
<p>void loop() </p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

8.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that the LCD
128X32 DOT displays the voltage value of the thermistor and the
temperature value in the current environment.
