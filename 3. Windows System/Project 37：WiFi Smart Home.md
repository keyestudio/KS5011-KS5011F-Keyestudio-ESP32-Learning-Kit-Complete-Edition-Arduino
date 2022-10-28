## Project 37：WiFi Smart Home

1.  **Introduction**

In the previous experiment, we have learned the WiFi Station mode, WiFi
AP mode and WiFi AP+Station mode of the ESP32. In this project, we will
use ESP32's WiFi Station mode to control the work of multiple
sensors/modules via APP connection with WiFi to achieve the effect of
WiFi smart home.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/f4be217034b7f60027b51e90b55adf95.png" style="width:1.05278in;height:0.48819in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.56319in;height:1.38194in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/8a6ed6668f0d1812d09dd361388ae087.png" style="width:1.05694in;height:0.57292in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/1886ee7e1faeea2c093ae626e1b8baaf.png" style="width:1.05764in;height:0.82014in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/85df6831220dec7d43a68bfc9b7382cb.png" style="width:1.45764in;height:0.96319in" /></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>5V Relay Module*1</td>
<td>Servo*1</td>
<td>HC-SR04 Ultrasonic Sensor*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/ba1d8f61328a0e474b423e826279dbb7.png" style="width:0.88472in;height:0.66875in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e60372bcdadcf0edfe497f31aaf1a3e9.png" style="width:1.16667in;height:0.97361in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:0.90694in;height:0.90139in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/0617c92e06f8ca1ebeaca24bdf692875.png" style="width:1.07361in;height:0.42778in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e3cf4510b86b7e0fd5b2880cd433cc25.png" style="width:0.40278in;height:0.80347in" /><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c607c1042325f6c2fa3db027e8611351.png" style="width:0.84236in;height:0.50139in" /></td>
</tr>
<tr class="even">
<td>Temperature and Humidity Sensor*1</td>
<td>M-F Dupont Wires</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
<td>Smart phone/Tablet*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/559e43bc8a25731e5be966c02d6798e6.jpeg" style="width:1.14514in;height:0.82708in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/a815c48437199c6ab79d74cd2d583de0.png" style="width:0.28125in;height:1.29792in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/412d874475de346d56b39cfb041ffc4c.png" style="width:1.19167in;height:0.51458in" /></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Battery Holder*1</td>
<td>No.5 Battery(self-provided)*6</td>
<td>Keyestudio breadboard special power module*1</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

**3. Wiring Diagram**

<table>
<tbody>
<tr class="odd">
<td>Relay Module</td>
<td>ESP32</td>
<td></td>
<td>Temperature and Humidity Sensor</td>
<td>ESP32</td>
</tr>
<tr class="even">
<td>G</td>
<td>G</td>
<td></td>
<td>G</td>
<td>G</td>
</tr>
<tr class="odd">
<td>V</td>
<td>5V</td>
<td></td>
<td>V</td>
<td>3V3</td>
</tr>
<tr class="even">
<td>S</td>
<td>IO32</td>
<td></td>
<td>S</td>
<td>IO15</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Ultrasonic Sensor</td>
<td>ESP32</td>
<td></td>
<td>Servo</td>
<td>ESP32</td>
</tr>
<tr class="odd">
<td>Vcc</td>
<td>5V</td>
<td></td>
<td>Red line</td>
<td>5V</td>
</tr>
<tr class="even">
<td>Trig</td>
<td>IO14</td>
<td></td>
<td>Brown line</td>
<td>G</td>
</tr>
<tr class="odd">
<td>Echo</td>
<td>IO27</td>
<td></td>
<td>Orange line</td>
<td>IO4</td>
</tr>
<tr class="even">
<td>Gnd</td>
<td>G</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

![](/media/cfdc653a7cee518bfebab38767c73a94.png)

4.  **Install APP**

Android system (Smartphone/Tablet) APP:

We have provided the Android APP installation package：

![](/media/9932f96b4cbfe94b9f1895e8479ad068.png)

**Installation steps：**

Now transfer the **keyes wifi.apk** file in the folder to android phone
or tablet, click **keyes wifi.apk** file to enter the installation page,
and click“ALLOW”, then click“INSTALL”, after a while, click“OPEN”after
the installation is completed to enter the APP interface.

![](/media/9932f96b4cbfe94b9f1895e8479ad068.png)

![](/media/d620452a9d6188cb3946269510df5ae0.png)

![](/media/b311329042f5bbd2880841127b91ebf8.png)

![](/media/7c5cfc935371c8e2ab30e999775d5f8f.png)

![](/media/d48c065ebaf1c5ca652eb72b15d3e596.png)

![](/media/78c89b91c0af2268f6267813e7923a9b.png)

IOS system (Smartphone/Tablet) APP:

a.Open App Store.

![](/media/27924fdb3d67692df7c63d8d0fb72287.png)

b. Enter keyes link in the search box and click Search, then the
download interface appears. Click“![](/media/962a57f92b78eea1f0e3e81463497a9c.png)”to download
and install the APP of keyes link. The following operations are similar
to those of Android system, you can refer to the steps of Android system
above for operation.

**5.** **Add the xht11 and** **ESP32Servo libraries**

This code uses two libraries named "**xht11**" and "**ESP32Servo**" , if
you haven't installed them yet, please do so before learning. The steps
to add third-party libraries are as follows:

Add the xht11 library first:

Open the Arduino IDE，click“Sketch”→“Include Library”→“Add .zip
Library...”. In the pop-up window, find the file named **“2 Windows
System\\2. C\_Tutorial\\3.Libraries\\xht11.ZIP”,** which locates in the
directory. Select the **xht11.ZIP** file and then click“Open”.

![](/media/6d5fd3d8d64babe41ac578eef18f5f0a.png)

![](/media/ea997b4f20ab15414fb9fe53fe419bed.png)

Then Add the ESP32Servo library:

Open the Arduino IDE，click “Sketch”→“Include Library”→“Add .ZIP
Library...”. In the pop-up window, find the file named**“2. Windows
System\\2. C\_Tutorial\\3.Libraries\\ESP32Servo-0.8.0.ZIP”,** which
locates in this directory. Select the **ESP32Servo-0.80.ZIP** file，and
then click“Open”.

![](/media/6d5fd3d8d64babe41ac578eef18f5f0a.png)

![](/media/d110371144d2afa0cb8aa9e45a084fc3.png)

**6. Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : WiFi Smart Home.</p>
<p>* Description : WiFi APP controls Multiple sensors/modules work to achieve the effect of WiFi smart home.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Arduino.h&gt;</p>
<p>#include &lt;WiFi.h&gt;</p>
<p>#include &lt;ESPmDNS.h&gt;</p>
<p>#include &lt;WiFiClient.h&gt;</p>
<p>#include "xht11.h"</p>
<p>//gpio15</p>
<p>xht11 xht(15);</p>
<p>unsigned char dht[4] = ;</p>
<p>#include &lt;ESP32Servo.h&gt;</p>
<p>Servo myservo;</p>
<p>int servoPin = 4;</p>
<p>#define Relay 32</p>
<p>#define trigPin 14</p>
<p>#define echoPin 27</p>
<p>int distance1;</p>
<p>String dis_str;</p>
<p>int ip_flag = 1;</p>
<p>int ultra_state = 1;</p>
<p>int temp_state = 1;</p>
<p>int humidity_state = 1;</p>
<p>String item = "0";</p>
<p>const char* ssid = "ChinaNet-2.4G-0DF0"; //the name of user's wifi</p>
<p>const char* password = "ChinaNet@233"; //the password of user's wifi</p>
<p>WiFiServer server(80);</p>
<p>String unoData = "";</p>
<p>void setup() </p>
<p>Serial.println("");</p>
<p>Serial.print("Connected to ");</p>
<p>Serial.println(ssid);</p>
<p>Serial.print("IP address: ");</p>
<p>Serial.println(WiFi.localIP());</p>
<p>server.begin();</p>
<p>Serial.println("TCP server started");</p>
<p>MDNS.addService("http", "tcp", 80);</p>
<p>digitalWrite(Relay, LOW);</p>
<p>pinMode(trigPin, OUTPUT);</p>
<p>pinMode(echoPin, INPUT);</p>
<p>}</p>
<p>void loop() </p>
<p>while(client.connected() &amp;&amp; !client.available())</p>
<p>String req = client.readStringUntil('\r');</p>
<p>int addr_start = req.indexOf(' ');</p>
<p>int addr_end = req.indexOf(' ', addr_start + 1);</p>
<p>if (addr_start == -1 || addr_end == -1) </p>
<p>req = req.substring(addr_start + 1, addr_end);</p>
<p>item=req;</p>
<p>Serial.println(item);</p>
<p>String s;</p>
<p>if (req == "/")</p>
<p></p>
<p>else if(req == "/btn/0")</p>
<p></p>
<p>else if(req == "/btn/1")</p>
<p></p>
<p>else if(req == "/btn/2")</p>
<p></p>
<p>else if(req == "/btn/3")</p>
<p></p>
<p>else if(req == "/btn/6")</p>
<p></p>
<p>while(ultra_state&gt;0)</p>
<p></p>
<p>}</p>
<p>else if(req == "/btn/7")</p>
<p></p>
<p>else if(req == "/btn/8")</p>
<p></p>
<p>while(temp_state&gt;0)</p>
<p></p>
<p>temp_state = 0;</p>
<p>}</p>
<p>}</p>
<p>else if(req == "/btn/9")</p>
<p></p>
<p>else if(req == "/btn/10")</p>
<p></p>
<p>while(humidity_state &gt; 0)</p>
<p></p>
<p>humidity_state = 0;</p>
<p>}</p>
<p>}</p>
<p>else if(req == "/btn/11")</p>
<p></p>
<p>//client.print(s);</p>
<p>client.stop();</p>
<p>}</p>
<p>int checkdistance() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**Note:** You need to change the user's Wifi name and Wifi password in
the project code

![](/media/9ddee42d7e41abd8a6db60d447cd9f68.png)to your own Wifi name and Wifi password.

**7.****Test Result**

Ensure that the code is correct, connect the external power, and switch
the DIP switch on the ESP32 expansion board to ON and power on, and then
compile and upload the code to ESP32.（**Note:** If uploading the code
fails, you can press the Boot button on ESP32 after
click![](/media/d09c4a31563f04a42d451e7bc1a5fb8a.png), and release the Boot
button![](/media/dc77bfcf5851c8f43aab6cbe7cec7920.png) after the percentage of uploading progress
appears）.

Open the serial monitor and set baud rate to 115200, then the monitor
prints the detected WiFi IP address.(If open the serial monitor and set
the baud rate to 115200, the information is not displayed, please press
the RESET button of the ESP32)

![](/media/1fd21fafd84d2b529931a89d21a03d6a.png)

![](/media/ffef6aa96cc6bb3949a735ddc9b91128.png)

Then open the WiFi APP and enter the detected WiFi IP address in the
text box in front of the WiFi button (for example, the IP address
detected by the monitor is below :192.168.0.156).

Then click the WiFi button, “Hello from ESP32 at 192.168.0.156”will be
displayed in the text box next to the WiFi IP address, which indicates
that the APP is already connected to WiFi.(WiFi IP address sometimes
changes, if the original IP address doesn't work, you need to re-check
the WiFi IP address)

![](/media/ac1bd20a153c3abc5c0c62a416446f52.jpeg)

After the APP has been connected to WiFi, please do the following steps:

1)  Click![](/media/5b9754cb6ec4f995c9eada1da89a8969.png)button, the relay will be opened, the
    APP will display![](/media/505b00b0e23f6498c5d51d5d775c8fcb.png)，and the indicator lights up
    on the module. Click![](/media/5b9754cb6ec4f995c9eada1da89a8969.png)again, the relay will be
    closed, the APP will display ![](/media/deb54a77cdcc87d7569e8b8e46de129f.png)，and the
    indicator on the module is off.

2)  Click![](/media/c54f78d819d4e6a8310eaeb79ff66910.png)button，the servo rotates 180°，the APP
    will display
    ![](/media/c54f78d819d4e6a8310eaeb79ff66910.png)again，the APP
    will display ![](/media/dee12bee3866542bfe5d70a539f79f0b.png)，the servo rotates 0°.

3)  Click![](/media/95bfbe879d2391e4e48dcae085abe5a6.png)button，the ultrasonic sensor detects the
    distance, put an object in front of the ultrasonic sensor, the APP
    will display
    
    ![](/media/e431e1b9c95bed37b053ae9617f93676.png)（different distances show different numbers）,
    the distance between the object and the ultrasonic sensor is
    6cm；click ![](/media/95bfbe879d2391e4e48dcae085abe5a6.png) again, turn off the sensor, the
    APP will display ![](/media/b1df35af68601022e54b7e575b0a07c7.png).

4)  Click![](/media/08c8a35841b31fa4b5327fb7b23a7af5.png)button，the temperature and humidity
    sensor measures the temperature in the environment, the APP will
    display ![](/media/0aafd0af43f80b692eca3d6732b551b2.png)（different temperatures show
    different temperature values），the ambient temperature is 30°C,
    click![](/media/08c8a35841b31fa4b5327fb7b23a7af5.png) again, turn off the sensor，the APP will
    display ![](/media/82887a1385bc7411ecbdc41f60ebd450.png).

5)  Click ![](/media/d8e3463ab2f644b3300cdeaa2a68e4c2.png) button，the temperature and humidity
    sensor measures the humidity in the environment,，the APP will
    display ![](/media/320b86323631e095db330a22ca97bad7.png)（different humidity show different
    humidity values）, the ambient humidity is
    55%；click![](/media/d8e3463ab2f644b3300cdeaa2a68e4c2.png)again，turn off the sensor, the APP
    will display ![](/media/adc18d06e626af067286da9040c20252.png).
