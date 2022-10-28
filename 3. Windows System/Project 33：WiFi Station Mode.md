**Project 33：WiFi Station Mode**

1.  **Introduction**

ESP32 has three different WiFi operating modes : Station mode，AP mode
and AP+Station mode. All WiFi programming projects must be configured
with WiFi operating mode before using, otherwise WiFi cannot be used. In
this project, we are going to learn the WiFi Station mode of the ESP32.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/729232b0c2d2c01984808289b222890c.png" style="width:1.8125in;height:0.86458in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg" style="width:2.43681in;height:1.13472in" /></td>
</tr>
<tr class="even">
<td>USB Cable*1</td>
<td>ESP32*1</td>
</tr>
</tbody>
</table>

**3. Wiring Diagram**

Plug the ESP32 to the USB port of your PC

![](/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

**4. Component Knowledge**

**Station mode：**

When setting Station mode, the ESP32 is taken as a WiFi client. It can
connect to the router network and communicate with other devices on the
router via a WiFi connection. As shown in the figure below, the PC and
the router have been connected. If the ESP32 wants to communicate with
the PC, the PC and the router need to be connected.

![](/media/f74baff97695aa2ee33a8c19370d2547.png)

5.  **Test Code**
    
    ![](/media/22a26c178a15b7a862b15bdbb89cc708.jpeg)

Since WiFi names and passwords vary from place to place, thereby users
need to enter the correct WiFi names and passwords in the box shown
below before running the program code.  

![](/media/b5c10b88e8b3527a7c1c552280c5f869.jpeg)

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : WiFi Station</p>
<p>* Description : Connect to your router using ESP32</p>
<p> * Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;WiFi.h&gt; //Include the WiFi Library header file of ESP32.</p>
<p>//Enter correct router name and password.</p>
<p>const char *ssid_Router = "ChinaNet-2.4G-0DF0"; //Enter the router name</p>
<p>const char *password_Router = "ChinaNet@233"; //Enter the router password</p>
<p>void setup()</p>
<p>Serial.println("\nConnected, IP address: ");</p>
<p>Serial.println(WiFi.localIP());//Serial monitor prints out the IP address assigned to ESP32.</p>
<p>Serial.println("Setup End");</p>
<p>}</p>
<p>void loop() </p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

After making sure the router name and password are entered correctly,
compile and upload the code to ESP32, open serial monitor and set baud
rate to 115200 then press the reset button first. When ESP32
successfully connects to “ssid\_Router”, serial monitor will print out
the IP address, then monitor will display as follows: (If open the
serial monitor and set the baud rate to 115200, the information is not
displayed, please press the RESET button of the ESP32)

![](/media/1fd21fafd84d2b529931a89d21a03d6a.png)

![](/media/efc6081aa00e0ce19df5501de76482da.png)
