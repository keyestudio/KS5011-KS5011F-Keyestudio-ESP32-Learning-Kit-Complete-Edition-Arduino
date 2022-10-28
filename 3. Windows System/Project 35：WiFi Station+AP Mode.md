**Project 35：WiFi Station+AP Mode**

1.  **Introduction**

In this project, we are going to learn the AP+Station mode of the ESP32.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/729232b0c2d2c01984808289b222890c.png" style="width:1.8125in;height:0.86458in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg" style="width:2.43681in;height:1.13472in" /></td>
</tr>
<tr class="even">
<td> USB Cable*1</td>
<td>ESP32*1</td>
</tr>
</tbody>
</table>

**3. Wiring Diagram**

Plug the ESP32 mainboard to the USB port of your PC

![](/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

**4. Component Knowledge**

**AP+Station mode:**

In addition to the AP mode and the Station mode, **AP+Station mode** can
be used at the same time. Turn on the Station mode of the ESP32, connect
it to the router network, and it can communicate with the Internet
through the router. Then turn on the AP mode to create a hotspot
network. Other WiFi devices can be connected to the router network or
the hotspot network to communicate with the ESP32.

**5. Test Code**

![](/media/36aee3408e3fbc8b4fbd19e6696f4adb.jpeg)

Before running the code, you need to modify the
ssid\_Router、password\_Router、ssid\_AP and password\_AP, as shown in
the box below:

![](/media/cc9e876b5694953686ed453c23d3c512.jpeg)

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : WiFi AP+Station</p>
<p>* Description : ESP32 connects to the user's router, turning on an access point</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;WiFi.h&gt;</p>
<p>const char *ssid_Router = "ChinaNet-2.4G-0DF0"; //Enter the router name</p>
<p>const char *password_Router = "ChinaNet@233"; //Enter the router password</p>
<p>const char *ssid_AP = "ESP32_WiFi"; //Enter the router name</p>
<p>const char *password_AP = "12345678"; //Enter the router password</p>
<p>void setup()else</p>
<p>Serial.println("\nSetting Station configuration ... ");</p>
<p>WiFi.begin(ssid_Router, password_Router);</p>
<p>Serial.println(String("Connecting to ")+ ssid_Router);</p>
<p>while (WiFi.status() != WL_CONNECTED)</p>
<p>Serial.println("\nConnected, IP address: ");</p>
<p>Serial.println(WiFi.localIP());</p>
<p>Serial.println("Setup End");</p>
<p>}</p>
<p>void loop() </p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Ensure that the code in the program has been modified correctly, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Open the serial monitor and set the baud
rate to 115200 and press the reset button, then monitor will display as
follows: (If open the serial monitor and set the baud rate to 115200,
the information is not displayed, please press the RESET button of the
ESP32)

![](/media/1fd21fafd84d2b529931a89d21a03d6a.png)

![](/media/68aa510490b2ef48ec0ac087d1b763a9.png)

Open the WiFi scanning function of the mobile phone, you can see the
ssid\_AP.

![](/media/3e0ad895bea7f5100cc02a415adcace7.png)
