**Project 30：Keypad Door**

1.  **Introduction**
    
    Commonly used digital button sensor, a button uses an IO port.
    However, it will occupy many IO ports when we need a lot of buttons.
    In order to save the IO ports, multiple buttons are made into a
    matrix type. In this project, we will use a ESP32 and a 4\*4 matrix
    keyboard to control a servo and a buzzer.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:1.59722in;height:0.77986in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.68056in;height:1.66944in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/cd0bc424e9916881a1a903793821a042.png" style="width:1.25417in;height:1.04792in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/4b4f653a76a82a3b413855493cc58fba.png" style="width:0.86111in;height:0.70069in" /></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>Servo*1</td>
<td>Active Buzzer*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/fcd187eb009098d691927511606c991b.jpeg" style="width:1.70972in;height:0.74931in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:0.90694in;height:0.90139in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:0.99028in;height:0.52986in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:0.90833in;height:0.23681in" /></td>
</tr>
<tr class="even">
<td>4*4 Membrane Matrix Keyboard*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
<td>1kΩResistor*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/9197d4aff9356c585b7ef68e33a6881d.png" style="width:0.27986in;height:1.08819in" /></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>NPN Transistor(S8050)*1</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**

**4\*4 Matrix keyboard：**It is a device that integrates a number of keys
in a package. As shown below, a 4x4 keypad matrix integrates 16 keys:

![](/media/fcd187eb009098d691927511606c991b.jpeg)

Similar to the integration of an LED matrix, the 4x4 keypad matrix’s
each row of keys is connected with a pin and it is the same in columns,
which can reduce the required numbers of processor ports. The internal
circuit of the keypad matrix is shown below.

![](/media/5ebdacba906622079e0ef41dc1ea3fdf.png)

The method of usage is similar to the LED matrix , we can scan rows and
columns to detect the state of each key. We take the column scanning
method as an example, we need to send low level to the fourth column
(Pin4), and detect the level state of row 1, 2, 3, 4 to judge whether
the key A, B, C, D are pressed. Then we can send low level to column 3,
2, 1 in turn to detect whether other keys are pressed. By this means,
you can get the state of all keys.

4.  **Read the key values of the 4\*4 matrix keyboard：**
    
    We start with a simple code to read the values of the 4\*4 matrix
    keyboard and print them in the serial monitor. Its wiring diagram is
    shown below：

![](/media/8bfa0e1b1a0f53598f51341d51bc7601.png)

**How to add the Keypad library：**

There are two ways to add libraries:

The first way, open the Arduino IDE, click“Sketch”→“Include
Library”→“Manage Libraries...”. Enter“Keypad”in the search box,
select“Keypad”and click“Update”to install. Please refer to the following
operations :

![](/media/923515e12b3de3743204ae217f5b051f.png)

![](/media/4b6e1251a79e68ec7f3bbc512ba7fbdd.png)

The second way，open the Arduino IDE，click “Sketch”→“Include
Library”→“Add .ZIP Library...”. In the pop-up window, find the
file named**“2. Windows System\\****2.
C\_Tutorial\\3.Libraries\\****Keypad-3.1.1.ZIP”,** which locates in this
directory. Select the file，and then click“Open”.

![](/media/59ad80016abb0ea494f3209d0d0889eb.png)

![](/media/475971df4edc86d0f7e6bf7a2294f9da.png)

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : 4x4 Matrix Keypad Display</p>
<p>* Description : Get the value for the matrix keyboard</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Keypad.h&gt;</p>
<p>// define the symbols on the buttons of the keypad</p>
<p>char keys[4][4] = ,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>byte rowPins[4] = ; // connect to the row pinouts of the keypad</p>
<p>byte colPins[4] = ; // connect to the column pinouts of the keypad</p>
<p>// initialize an instance of class NewKeypad</p>
<p>Keypad myKeypad = Keypad(makeKeymap(keys), rowPins, colPins, 4, 4);</p>
<p>void setup() </p>
<p>void loop() </p>
<p>}</p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable, and open the serial monitor and
then set baud rate to 115200 and press the reset button first. You will
see that press the keyboard and the monitor will print the corresponding
key values, as shown below.

![](/media/a35e94a442c20325472043ab62589258.png)

5.  **Wiring diagram of the Keypad Door**

In the last experiment, we have known the key values of the 4\*4 matrix
keyboard. Next, we use it as the keyboard to control a servo and a
buzzer.

![](/media/862e840117a46c1174522a734e28e2f0.png)

6.  **Adding the Keypad and ESP32Servo** **libraries：**

First, add the **ESP32Servo** library：

Open the Arduino IDE，click“Sketch”→“Include Library”→“Add .ZIP
Library...”. In the pop-up window, find the file named **“2. Windows
System\\2. C\_Tutorial\\3.Libraries\\ESP32Servo-0.8.0.ZIP”,** which
locates in this directory. Select the file and then click“Open”.

![](/media/710e5782c37ff2a65ddde368470ce1c5.png)

![](/media/0a64efa8b54f1c881fc162235e7c5f85.png)

Then, add the **Keypad** library：

Open the Arduino IDE，click “Sketch”→“Include Library”→“Add .ZIP
Library...”. In the pop-up window, find the file named **“2. Windows
System\\2. C\_Tutorial\\3.Libraries\\Keypad-3.1.1.ZIP”,** which locates
in this directory. Select the file and then click“Open”.

![](/media/710e5782c37ff2a65ddde368470ce1c5.png)

![](/media/475971df4edc86d0f7e6bf7a2294f9da.png)

7.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : Keypad_Door</p>
<p>* Description : Make a simple combination lock.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Keypad.h&gt;</p>
<p>#include &lt;ESP32Servo.h&gt;</p>
<p>// define the symbols on the buttons of the keypad</p>
<p>char keys[4][4] = ,</p>
<p>,</p>
<p>,</p>
<p></p>
<p>};</p>
<p>byte rowPins[4] = ; // connect to the row pinouts of the keypad</p>
<p>byte colPins[4] = ; // connect to the column pinouts of the keypad</p>
<p>// initialize an instance of class NewKeypad</p>
<p>Keypad myKeypad = Keypad(makeKeymap(keys), rowPins, colPins, 4, 4);</p>
<p>Servo myservo; // Create servo object to control a servo</p>
<p>int servoPin = 15; // Define the servo pin</p>
<p>int buzzerPin = 2; // Define the buzzer pin</p>
<p>char passWord[] = ; // Save the correct password</p>
<p>void setup() </p>
<p>void loop() </p>
<p>if (isRight) </p>
<p>else </p>
<p>keyInNum = 0; // Reset the number of the input characters to 0</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

8.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that press the
keypad to input password with 4 characters. If the input is
correct(Correct password :1234), the servo will move to a certain
degree, and then return to the original position. If the input is wrong,
an input error alarm will be generated.
