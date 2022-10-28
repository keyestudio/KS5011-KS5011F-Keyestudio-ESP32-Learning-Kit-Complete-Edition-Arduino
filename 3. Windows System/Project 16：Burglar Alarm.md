**Project 16：Burglar Alarm**

1.  **Introduction**

The PIR motion sensor measures the thermal infrared (IR) light emitted
by moving objects. The sensor can detect the movement of people、animals
and cars to trigger safety alarms and lighting. They are used to detect
movement and ideal for security such as burglar alarms and security
lighting systems.

In this project, we will use the ESP32 control the PIR motion
sensor、buzzer and LED to simulate burglar alarm.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e62993d4915fff7d0f1a7653313b03dc.jpeg" style="width:1.34097in;height:0.65486in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/51dc6a366ebb066960c32263c37e0244.png" style="width:1.08472in;height:0.81458in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/4b4f653a76a82a3b413855493cc58fba.png" style="width:0.95694in;height:0.81944in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/ef77f5a64c382157fc2dea21ec373fef.png" style="width:0.29514in;height:1.25903in" /></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>PIR Motion Sensor*1</td>
<td>Active Buzzer*1</td>
<td>Red LED*1</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.51736in;height:1.26806in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/849dad1bcb5c3177310976501fbc96c9.png" style="width:0.75903in;height:0.64097in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/845d05a6108b1662b828610ba9dcb788.png" style="width:0.25833in;height:1.13681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c4015c5c1b99b2eb674777c1e0dde82b.png" style="width:0.6375in;height:0.64444in" /></td>
</tr>
<tr class="even">
<td>Breadboard*1</td>
<td>M-F Dupont Wires</td>
<td>220ΩResistor*1</td>
<td>USB Cable*1</td>
<td>Jumper Wires</td>
</tr>
</tbody>
</table>

2.  **Component Knowledge**

![](/media/51dc6a366ebb066960c32263c37e0244.png)

**PIR Motion Sensor :** Its principle is that when some crystals, such
as lithium tantalate and triglyceride sulfate are heated, the two ends
of the crystal will generate an equal number of charges with opposite
signs. These charges can be converted into voltage output by an
amplifier.

Due to the human body will release infrared light, although relatively
weak, can still be detected. When the Human Body Infrared Sensor detects
the movement of a nearby person, the sensor signal terminal outputs a
high level 1, otherwise, it outputs low level 0.

Special attention should be paid to the fact that this sensor can detect
people、animals and cars in motion, which cannot be detected in static,
and the maximum detection distance is about 7 meters.

**Note:** Since vulnerable to radio frequency radiation and temperature
changes, the PIR motion sensor should be kept away from heat sources
like radiators, heaters and air conditioners, as well as direct
irradiation of sunlight, headlights and incandescent light.

**Features:**

Maximum input voltage: DC 3.3 \~ 5V

Maximum operating current: 50MA

Maximum power: 0.3W

Operating temperature: -20 \~ 85℃

Output high level is 3V, low level is 0V.

Delay time: about 2.3 to 3s

Detection Angle: about 100 degrees

Maximum detection distance: about 7m

Indicator light output (when the output is high, it will light up)

Pin limiting current: 50MA

**Schematic diagram:**

![](/media/9e1ec604aa6f9d4a3c1fe41d4bccd699.png)

3.  **Wiring Diagram**

![](/media/67fd78fc542f0e7c232d96a23fb90120.png)

4.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : Burglar Alarm</p>
<p>* Description : Human infrared sensor buzzer and LED to simulate burglar alarm.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#define buzzerPin 2 // the pin of the buzzer</p>
<p>#define ledPin 0 // the pin of the PIR motion sensor</p>
<p>#define pirPin 15 // the pin of the PIR motion sensor</p>
<p>byte pirStat = 0; // the state of the PIR motion sensor</p>
<p>void setup() </p>
<p>void loop()</p>
<p></p>
<p>else </p>
<p>}</p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

5.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that if the PIR
motion sensor detects someone moving nearby, the buzzer will
continuously
[raise ](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/9.0.1.1/resultui/html/index.html#/javascript:;)an
alarm and the LED will continuously flash.
