**Project 17： I2C 128×32 LCD**

1.  **Introduction**
    
    In everyday life, we can do a host of experiments with the display
    module and also DIY a broad menu of small objects. For example, you
    can make a temperature meter with a temperature sensor and a
    display, or make a distance meter with an ultrasonic module and a
    display. 
    
    In this project, we will use the LCD\_128X32\_DOT module as the
    display and connect it to the ESP32, which will be used to control
    the LCD\_128X32\_DOT display to show various English words, common
    symbols and numbers.

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
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/2c2645e94a00867ac23e8a022f0a631a.png" style="width:1.59236in;height:0.76736in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/ece3c38dc9a9e6428b122481d6bb0d4d.png" style="width:1.19028in;height:1.00556in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>LCD_128X32_DOT*1</td>
<td>M-F Dupont Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

**3.Component Knowledge**

![](/media/2c2645e94a00867ac23e8a022f0a631a.png)

**LCD\_128X32\_DOT**: It is an LCD module with 128\*32 pixels and its
driver chip is ST7567A. The module uses the IIC communication mode,
while the code contains a library of all alphabets and common symbols
that can be called directly.

When using, we can also set it in the code so that the English letters
and symbols show different text sizes. To make it easy to set up the
pattern display, we also provide a mold capture software that converts a
specific pattern into control code and then copies it directly into the
test code for use.

**Schematic diagram of LCD\_128X32\_DOT**

![](/media/5451aed32bc5b7b30fbd5613ad09a65b.png)

**Features:**

Pixel: 128\*32 character

Operating voltage(chip)：4.5V to 5.5V

Operating current：100mA (5.0V)

Optimal operating voltage(module):5.0V

**4. Wiring Diagram**

![](/media/072d954dac310add077688398ad59af2.png)

5.  **Adding the lcd128\_32\_io library**

This code uses a library named "**lcd128\_32\_io**", if you haven't
installed it yet, please do so before learning. The steps to add
third-party libraries are as follows:

Open the Arduino IDE，click “Sketch”→“Include Library”→“Add .ZIP
Library...”. In the pop-up window, find the file named **“2. Windows
System\\2. C\_Tutorial\\3. Libraries\\LCD\_128X32.ZIP”** ， which locates
in this directory. Select the **LCD\_128X32.ZIP** file and then click
“Open”.

![](/media/aa01fe2a906b78af82efc217cf44af63.png)

![](/media/fca2fbe4f48a7b216d1c5a84a74d850a.png)

6.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//***********************************************************************</p>
<p>/*</p>
<p>* Filename : LCD 128*32</p>
<p>* Description : LCD 128*32 display string</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include "lcd128_32_io.h"</p>
<p>//Create lCD128 *32 pin，sda---&gt;21， scl---&gt;22</p>
<p>lcd lcd(21, 22);</p>
<p>void setup() </p>
<p>void loop() :;'|?,.~\\[]");</p>
<p>}</p>
<p>//***********************************************************************</p></td>
</tr>
</tbody>
</table>

7.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that the
128X32LCD module display will show“KEYESTUDIO”at the first
line，“ABCDEFGHIJKLMNOPQR”will be displayed at the second
line，“123456789+-\*/\<\>=$@”will be shown at the third line
and“%^&(){}:;'|?,.\~\\\\\[\]”will be displayed at the fourth line.
