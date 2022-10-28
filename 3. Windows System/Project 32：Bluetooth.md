**Project 32：Bluetooth**

This chapter mainly introduces how to make simple data transmission
through bluetooth of ESP32 and mobile phones. Project 32.1 is classic
Bluetooth while project 32.2 is Bluetooth control LED.

**Project 32.1：Classic Bluetooth**

1.  **Components**

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

In this tutorial we need to use a Bluetooth APP called serial Bluetooth
terminal to assist in the experiment.

Download link: <https://www.appsapk.com/serial-bluetooth-terminal/> .

Here is its
[sign](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;)

![](/media/7b98d6708888b0a6f38f85ffca484857.png)

2.  **Component Knowledge**

Bluetooth is a short-distance communication system that can be divided
into two types, namely low power bluetooth (BLE) and classic bluetooth.
There are two modes for simple data transfer: master mode and slave
mode. 

**Master Mode**: In this mode, work is done on the master device and can
be connected to the slave device. When the device initiates a connection
request in the main mode, information such as the address and pairing
password of other bluetooth devices are required.  Once paired, you can
connect directly to them.  

**Slave Mode**: A bluetooth module in the slave mode can only accept
connection requests from the host, but cannot initiate connection
requests. After being connected to a host device, it can send and
receive data through the host device.

Bluetooth devices can interact with each other, when they interact, the
bluetooth device in the main mode searches for nearby devices. While a
connection is established, they can exchange data. For example, when a
mobile phone exchanges data with ESP32, the mobile phone is usually in
master mode and the ESP32 is in slave mode.  

![](/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

**Master Slave**

3.  **Wiring Diagram**

We can use a USB cable to connect ESP32 mainboard to the USB port on a
computer.

![](/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

4.  **Test Code**
    
    ![](/media/aa241f4ce7d3301bef81e01681dc6fa3.jpeg)

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Classic Bluetooth--SerialToSerialBT</p>
<p>* Description : ESP32 communicates with the phone by bluetooth and print phone's data via a serial port</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include "BluetoothSerial.h"</p>
<p>BluetoothSerial SerialBT;</p>
<p>String buffer;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>if (SerialBT.available()) </p>
<p>delay(20);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Test Result**

Compile and upload the code to the ESP32. After uploading
successfully，we will use a USB cable to power on. Open the serial
monitor and set the baud rate to **115200 then press the reset button
first**. When you see the serial monitor prints out the character string
as below, it indicates that the Bluetooth of ESP32 is ready and waiting
for connection with a phone. (If open the serial monitor and set the
baud rate to 115200, the information is not displayed, please press the
RESET button of the ESP32)

![](/media/1fd21fafd84d2b529931a89d21a03d6a.png)

![](/media/35c5986d34a01d74bac62e6f6ade7e54.png)

Make sure that the Bluetooth of your phone has been turned on and
“Serial Bluetooth Terminal” has been installed.

![](/media/382529edef3989e60264cad217d88e6f.png)

Click“Search”，search for the nearby bluetooth and select to connect
the“ESP32 test”.

![](/media/0608c9a78b5f56d4c8f1994c55c9cd46.png)

Turn on software APP, click the left of the terminal. Select
"**Devices**" .

![](/media/32b8c3abd51fc538ba854b1d72e1165e.png)

Select ESP32test in classic Bluetooth mode, and a successful connecting
prompt will appear as shown below.

![](/media/00f9b335cb512704763e3621e7c598b2.png)

Data can be transferred between your phone and a computer via ESP32 now.
 

Send “Hello！”, When the computer receives it, which will reply with
"Hi\!".

![](/media/10f1f806f03e3651b3f2779f91aba2fe.png)

![](/media/4f4e6b4e45996ccbde4da17219f02d00.png)

**Project 32.2：Bluetooth Control LED**

1.  **Components**

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
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7eb361d680dfa351f07f8527aeb37abd.png" style="width:0.275in;height:1.17361in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:1.22639in;height:0.49236in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.66736in;height:0.64097in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>Red LED*1</td>
<td>220ΩResistor*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

2.  **Wiring Diagram**
    
    ![](/media/0735997593c8858ad6441d8e9867206f.png)

3.  **Test Code**
    
    ![](/media/4ba1e09b9ac5ee6b53b55655d49abfde.jpeg)

<table>
<tbody>
<tr class="odd">
<td><p>//*******************************************************************</p>
<p>/*</p>
<p>* Filename : Bluetooth Control LED</p>
<p>* Description : The phone controls esp32's led via bluetooth.</p>
<p>When the phone sends "LED_on," ESP32's LED lights turn on.</p>
<p>When the phone sends "LED_off," ESP32's LED lights turn off.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include "BluetoothSerial.h"</p>
<p>#include "string.h"</p>
<p>#define LED 15</p>
<p>BluetoothSerial SerialBT;</p>
<p>char buffer[20];</p>
<p>static int count = 0;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>if(count&gt;0)</p>
<p>if(strncmp(buffer,"led_off",7)==0)</p>
<p>count=0;</p>
<p>memset(buffer,0,20);</p>
<p>}</p>
<p>}</p>
<p>//*******************************************************************</p></td>
</tr>
</tbody>
</table>

**4. Test Result**

Compile and upload the code to the ESP32. After uploading
successfully，we will use a USB cable to power on. The APP operation is
the same as the project 32.1. To make the external LED on and off,
simply change the sending content to "led\_on" and "led\_off". Moving
the APP to send data:

![](/media/21ec63e3abe43a119ab8a3d4634894f0.png)

The serial monitor will display as follows:

![](/media/f5d5d544d23177674a0b206254fa645b.png)

**LED Circumstance**

![](/media/a1e66d46e5797995a1b66a761c7857f8.png)

**Note:** If the sent content is not "led-on 'or" led-off ", the status
of the LED will not change. If the LED is on, it remains on when
irrelevant content is received; Conversely, if the LED is off, it
continues to be off when irrelevant content is received.
