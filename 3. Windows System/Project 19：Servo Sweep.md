**Project 19：Servo Sweep**

1.  **Introduction**

Servo is an electric motor that can rotate very precisely. At present,
it has been widely used in toy cars，remote control
helicopters，airplanes，robots, etc. In this project, we will use a
ESP32 to control the rotation of the servo.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:2.17847in;height:1.0625in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.94722in;height:2.32014in" /></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/cd0bc424e9916881a1a903793821a042.png" style="width:1.25417in;height:1.04792in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.84722in;height:0.81389in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>Servo*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**

**Servo：**

![](/media/99830768916233a9c5900ac399006c17.png)

The servo is a kind of position servo driver, which is mainly composed
of housing、circuit board、coreless motor、gear and position detector. Its
working principle is that the receiver or microcontroller sends a signal
to the servo which has an internal reference circuit that generates a
reference signal with a period of 20ms and a width of 1.5ms, and
compares the DC bias voltage with the voltage of the potentiometer to
output voltage difference.

The IC on the circuit board determines the direction of rotation, and
then drives the coreless motor to start rotation and transmits the power
to the swing arm through the reduction gear, while the position detector
sends back a signal to determine whether it has reached the positioning.

It is suitable for those control systems that require constant change of
angle and can be maintained. When the motor rotates at a certain speed,
the potentiometer is driven by the cascade reduction gear to rotate so
that the voltage difference is 0 and the motor stops rotating. The angle
range of general servo rotation is 0 to 180 degrees.

The pulse period for controlling the servo is 20ms, the pulse width is
0.5ms to 2.5ms, and the corresponding position is -90 degrees to +90
degrees. The following is an example of a 180 degree servo：

![](/media/708316fde05c62113a3024e0efb0c237.jpeg)

Servo motors have many specifications, but they all have three
connecting wires, which are brown, red, and orange (different brands may
have different colors). The brown is GND, the red is the positive power
supply, and the orange is the signal line.

![](/media/3f5bc31305e64108bed3b3619d602891.jpeg)

4.  **Wiring Diagram**
    
    When supplying the servo, please note that the power supply voltage
    should be 3.3V-5V. Make sure there are no errors when connecting the
    servo to the power supply.

![](/media/39621cc861e5f7c189a047b7f0bbd0be.png)

5.  **Adding the ESP32Servo library**

This code uses a library named "**ESP32Servo**", if you haven't
installed it yet, please do so before learning. The steps to add
third-party libraries are as follows:

How to install the library？

There are two ways to add libraries:

The first way, open the Arduino IDE, click“Sketch”→“Include
Library”→“Manage Libraries”. Enter “ESP32Servo” in the search box,
select “ESP32Servo” and click “Update” to install. Please refer to the
following operations :

![](/media/3dbaa07966c4e0c4af5ce69afc03e467.png)

![](/media/a2ab8810ac2488ef30eded7c24bf69af.png)

The second way，open the Arduino IDE，click “Sketch”→“Include
Library”→“Add .ZIP Library...”. In the pop-up window, find the
file named**“2. Windows System\\2.
C\_Tutorial\\3.Libraries\\****ESP32Servo-0.8.0.ZIP”**which locates in
this directory. Select the **ESP32Servo-0.80.ZIP** file，and then
click“Open”.

![](/media/e177162e1796490825aa7b44999a59dc.png)

![](/media/f5db0a244df656b0fd9b2d5b8d42c1a5.png)

6.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//*****************************************************************************</p>
<p>/*</p>
<p>* Filename : Servo Sweep</p>
<p>* Description : Control the servo motor for sweeping</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;ESP32Servo.h&gt;</p>
<p>Servo myservo; // create servo object to control a servo</p>
<p>int posVal = 0; // variable to store the servo position</p>
<p>int servoPin = 15; // Servo motor pin</p>
<p>void setup() </p>
<p>void loop() </p>
<p>for (posVal = 180; posVal &gt;= 0; posVal -= 1) </p>
<p>}</p>
<p>//*****************************************************************************</p></td>
</tr>
</tbody>
</table>

7.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that the servo
will rotate from 0 degrees to 180 degrees and then reverse the direction
to make it rotate from 180 degrees to 0 degrees and repeat these actions
in an endless loop.

![](/media/c5250405a4290ecb2d758ff1097310c7.png)
