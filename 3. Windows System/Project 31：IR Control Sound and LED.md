**Project 31：IR Control Sound and LED**

1.  **Introduction**

IR remote control is a low-cost and easy-to-use wireless communication
technology. IR light is very similar to visible light, except that its
wavelength is slightly longer. This means that infrared rays cannot be
detected by the human eyes, which is perfect for wireless communication.

For example, when you press a button on the TV remote control, an
infrared LED will be on and off repeatedly at a frequency of 38,000
times per second, transmitting information (such as volume or channel
control) to the infrared sensor on the TV.

We'll start by explaining how common infrared communication protocols
work. Then we will start the project with a remote control and an
infrared receiver component.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/146cead9d42f214abdbcd383a95eb998.jpeg" style="width:1.41458in;height:0.69097in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.55278in;height:1.35486in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/88e6b057fb4b0c576c9b2111d15b26e5.png" style="width:1.14861in;height:0.48403in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/f1a86fc81ab4b043263ce7e01e14d470.png" style="width:0.23056in;height:1.27847in" /></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>IR Receiver *1</td>
<td>RGB LED*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/8a6fb37dedef748e6c2609bff5c64906.png" style="width:0.69792in;height:1.45764in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/4b4f653a76a82a3b413855493cc58fba.png" style="width:0.86111in;height:0.70069in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/a22dac8c5edbe90e867cbb04769d1816.png" style="width:0.23194in;height:1.04028in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:1.22639in;height:0.49236in" /></td>
</tr>
<tr class="even">
<td>IR Remote Control*1</td>
<td>Active Buzzer*1</td>
<td>10KΩResistor*1</td>
<td>220ΩResistor*3</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/9197d4aff9356c585b7ef68e33a6881d.png" style="width:0.27986in;height:1.08819in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:0.90833in;height:0.23681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:0.90694in;height:0.90139in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:0.99028in;height:0.52986in" /></td>
</tr>
<tr class="even">
<td>NPN Transistor(S8050)*1</td>
<td>1kΩResistor*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**

**IR Remote Control** ：It is a device with a certain number of buttons.
Pressing different buttons will cause the IR transmitter tubes in the
front of the remote control to send IR signals in different codes.

IR remote control technology is widely used in electronic products such
as TVs and air
[conditioner](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/9.0.1.1/resultui/html/index.html#/javascript:;)s,
etc, making it more accessible for you to switch TV programs and adjust
the temperature of the air
[conditioner](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/9.0.1.1/resultui/html/index.html#/javascript:;)s.
The remote control we use is shown below:

The IR remote control adopts NEC code and the signal cycle is 110ms.

![](/media/3c9d76cb0d24d9861811ce2cb0bb6ae4.png)

**IR Receiver：**It is a component that can receive IR light, so we can
use it to detect the signals emitted by the IR remote control.

The IR receiver demodules the received IR signals and converts them back
to binary, then passes the information to the microcontroller.

**IR signal modulation process diagram**

![](/media/3da1969e509f53706643c77d0534eb73.png)

**NEC Infrared communication protocol：**

**NEC Protocol:**

To my knowledge the protocol I describe here was developed by NEC (Now
Renesas). I've seen very similar protocol descriptions on the internet,
and there the protocol is called Japanese Format.

I do admit that I don't know exactly who developed it. What I do know is
that it was used in my late VCR produced by Sanyo and was marketed under
the name of Fisher. NEC manufactured the remote control IC.

This description was taken from my VCR's service manual. Those were the
days, when service manuals were filled with useful information\!

**Features:**

  - > \* 8 bit address and 8 bit command length.

  - > \* Extended mode available, doubling the address size.

  - > \* Address and command are transmitted twice for reliability.

  - > \* Pulse distance modulation.

  - > \* Carrier frequency of 38kHz.

  - > \* Bit time of 1.125ms or 2.25ms.

**Modulation:**

![](/media/da33571c6f0afb94b1ec1d91caba3edb.png)

The NEC protocol uses pulse distance encoding of the bits. Each pulse is
a 560µs long 38kHz carrier burst (about 21 cycles). A logical "1" takes
2.25ms to transmit, while a logical "0" is only half of that, being
1.125ms. The recommended carrier duty-cycle is 1/4 or 1/3.

**Protocol:**

![](/media/f970404e7bbfb5711fea5c776f689f3a.png)

The picture above shows a typical pulse train of the NEC protocol. With
this protocol the LSB is transmitted first. In this case Address $59 and
Command $16 is transmitted. A message is started by a 9ms AGC burst,
which was used to set the gain of the earlier IR receivers. This AGC
burst is then followed by a 4.5ms space, which is then followed by the
Address and Command. Address and Command are transmitted twice.

The second time all bits are inverted and can be used for verification
of the received message. The total transmission time is constant because
every bit is repeated with its inverted length. If you're not interested
in this reliability you can ignore the inverted values, or you can
expand the Address and Command to 16 bits each\!

Keep in mind that one extra 560µs burst has to follow at the end of the
message in order to be able to determine the value of the last bit.

![](/media/63364daf21e5522c64eb8dfa82f2cef2.png)

A command is transmitted only once, even when the key on the remote
control remains pressed. Every 110ms a repeat code is transmitted for as
long as the key remains down. This repeat code is simply a 9ms AGC pulse
followed by a 2.25ms space and a 560µs burst.

![](/media/afea92a3b5cc1aa2457d2b118b157c84.png)

**Extended NEC protocol:**

The NEC protocol is so widely used that soon all possible addresses were
used up. By sacrificing the address redundancy the address range was
extended from 256 possible values to approximately 65000 different
values. This way the address range was extended from 8 bits to 16 bits
without changing any other property of the protocol.

By extending the address range this way the total message time is no
longer constant. It now depends on the total number of 1's and 0's in
the message. If you want to keep the total message time constant you'll
have to make sure the number 1's in the address field is 8 (it
automatically means that the number of 0's is also 8). This will reduce
the maximum number of different addresses to just about 13000.

The command redundancy is still preserved. Therefore each address can
still handle 256 different commands.

![](/media/2f78d1ce7f001926f6b90ad966796e91.png)

Keep in mind that 256 address values of the extended protocol are
invalid because they are in fact normal NEC protocol addresses. Whenever
the low byte is the exact inverse of the high byte it is not a valid
extended address.

4.  **Decoded IR signals**

We connect the IR receiver element to the ESP32 according to the wiring
diagram below:

![](/media/700496cb1e0d5d23fd63c28469dd3fd0.png)

**How to add the IRremoteESP8266 library**

There are two ways to add libraries:

The first way, open the Arduino IDE, click“Sketch”→“Include
Library”→“Manage Libraries...”. Enter“IRremoteESP8266”in the
search box, select“IRremoteESP8266”and click“Update”to install. Please
refer to the following operations :

![](/media/70504b2794644c45ba7d440a79879795.png)

![](/media/71b05cd3f81dae4b7efcf7ffc65920f9.png)

The second way，open the“Sketch”→“Include Library”→“Add .ZIP Library...”.
In the pop-up window, find the file named**“2. Windows System\\2.
C\_Tutorial\\3.Libraries\\IRremoteESP8266-2.7.4.ZIP”,** which locates in
this directory. Select the file and then click“Open”.

![](/media/15d3058196199ee96d8e40451d88e8c7.png)

![](/media/bb7986711410b92c1fbcc153230162bc.png)

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************</p>
<p>/*</p>
<p>* Filename : Decoded IR Signal</p>
<p>* Description : Decode the infrared remote control and print it out through the serial port.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Arduino.h&gt;</p>
<p>#include &lt;IRremoteESP8266.h&gt;</p>
<p>#include &lt;IRrecv.h&gt;</p>
<p>#include &lt;IRutils.h&gt;</p>
<p>const uint16_t recvPin = 0; // Infrared receiving pin</p>
<p>IRrecv irrecv(recvPin); // Create a class object used to receive class</p>
<p>decode_results results; // Create a decoding results class object</p>
<p>void setup() </p>
<p>void loop() </p>
<p>delay(1000);</p>
<p>}</p>
<p>//*************************************************************************</p></td>
</tr>
</tbody>
</table>

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable, and open the serial monitor and
then set baud rate to 115200 and press the reset button first. You will
see that aim the IR remote control transmitter at the IR receiver head,
press the button on the IR remote control, and the monitor prints the
current received key code values.

![](/media/c8eaa6c1894aaebf907903cc0240bec8.png)

Write down the code associated with each button, because you will need
that information later.

![](/media/ebcf0cb2055f7784505f76ceeaef9f47.jpeg)

**5. Wiring diagram of the IR remote control**

![](/media/4912c1622e0eaedb76ea3a9b8ed969c0.png)

**6. Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//********************************************************************</p>
<p>/*</p>
<p>* Filename : IR Control Sound And LED</p>
<p>* Description : Remote control RGB and Passive buzzer with infrared remote control.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Arduino.h&gt;</p>
<p>#include &lt;IRremoteESP8266.h&gt;</p>
<p>#include &lt;IRrecv.h&gt;</p>
<p>#include &lt;IRutils.h&gt;</p>
<p>const uint16_t recvPin = 0; // Infrared receiving pin</p>
<p>IRrecv irrecv(recvPin); // Create a class object used to receive class</p>
<p>decode_results results; // Create a decoding results class object</p>
<p>int ledPins[] = ; //define red, green, blue led pins</p>
<p>const byte chns[] = ; //define the pwm channels</p>
<p>int buzzerPin = 15; // the number of the buzzer pin</p>
<p>void setup() </p>
<p>}</p>
<p>void loop() </p>
<p>}</p>
<p>void handleControl(unsigned long value) </p>
<p>else if (value == 0xFF9867) // Receive the number '2'</p>
<p></p>
<p>else if (value == 0xFFB04F) // Receive the number '3'</p>
<p></p>
<p>else if (value == 0xFF30CF) // Receive the number '4'</p>
<p></p>
<p>else if (value == 0xFF18E7) // Receive the number '5'</p>
<p></p>
<p>else if (value == 0xFF7A85) // Receive the number '6'</p>
<p></p>
<p>else if (value == 0xFF10EF) // Receive the number '7'</p>
<p></p>
<p>else</p>
<p>}</p>
<p>//********************************************************************</p></td>
</tr>
</tbody>
</table>

7.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that press the
1 to 7 keys of the IR remote control, the buzzer will sound once, and
the RGB will be red, green, blue, yellow,
[carmine](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/9.0.1.1/resultui/html/index.html#/javascript:;),
blue and green and white respectively. Press another key (except 1 to 7
key), and the RGB will be off.

(**Note:** Before use, we need to remove the plastic sheet from the
bottom of the IR remote control.)

![](/media/3c9d76cb0d24d9861811ce2cb0bb6ae4.png)
