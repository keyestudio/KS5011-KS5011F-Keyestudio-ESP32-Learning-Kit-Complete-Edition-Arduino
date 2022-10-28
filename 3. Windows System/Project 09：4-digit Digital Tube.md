**Project 09：4-Digit Digital Tube**

1.  **Introduction**

The 4-digit 7-segment display is a very practical display device and it
is used for devices such as electronic clocks, score counters and the
number of people in the park. Because of the low price, easy to use,
more and more projects will use the 4 Digit 7-segment display. In this
project, we use ESP32 to control the 4-digit 7-segment display to
display digits.

2.  **Components**

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
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/ee7a4ecd35ef268149e31fb9d62c8227.png" style="width:0.94792in;height:0.71736in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:1.22639in;height:0.49236in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:0.90694in;height:0.90069in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>4-digit 7-segment display Module*1</td>
<td>220Ω Resistor*8</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**
    
    ![](/media/ce987bf9a2ab398945c98b34d3f8a003.png)

**4-digit 7-segment display：**It is a device with common cathode and
anode, its display principle is similar to the 1-Digit digital tube
display. Both of them have eight GPIO ports to control the digital tube
display, that is 8 leds. However, here is 4-digit, so it needs four GPIO
ports to control the bit selection end. Our 4 - digit digital tube is
common cathode. 

The following figure shows the pin diagram of the 4-digit digital tube.
G1, G2, G3 and G4 are the control pins. 

![](/media/37113fa53213973132086c285d67686b.png)

[**Schematic
Diagram**](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/9.0.1.1/resultui/html/index.html#/javascript:;)

![](/media/c210e9899274cdf79ffd44db1e250fb5.png)

![](/media/ea75d1b7414bf6f8c187fb32fea9bc83.png)

4.  **Wiring Diagram**
    
    ![](/media/313c429f670cd000b61cd3aeee0fef92.png)

5.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : 4-Digit Digital Tube</p>
<p>* Description : Four Digit Tube displays numbers from 0 to 9999.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#define d_a 18 //Define nixie tube a to pin 18</p>
<p>#define d_b 13</p>
<p>#define d_c 2</p>
<p>#define d_d 16</p>
<p>#define d_e 17</p>
<p>#define d_f 19</p>
<p>#define d_g 0</p>
<p>#define d_dp 4</p>
<p>#define G1 21 //Define the first set of nixtube G1 to pin 21</p>
<p>#define G2 22</p>
<p>#define G3 14</p>
<p>#define G4 15</p>
<p>//Nixie tube 0-F code value</p>
<p>unsigned char num[17][8] =</p>
<p>, //0</p>
<p>, //1</p>
<p>, //2</p>
<p>, //3</p>
<p>, //4</p>
<p>, //5</p>
<p>, //6</p>
<p>, //7</p>
<p>, //8</p>
<p>, //9</p>
<p>, //A</p>
<p>, //B</p>
<p>, //C</p>
<p>, //D</p>
<p>, //E</p>
<p>, //F</p>
<p>, //.</p>
<p>};</p>
<p>void setup()</p>
<p></p>
<p>void loop()</p>
<p></p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>//Display functions: g ranges from 1 to 4,num ranges from 0 to 9</p>
<p>void Display(unsigned char g,unsigned char n)</p>
<p></p>
<p>digitalWrite(d_a,num[n][0]); //a Queries the code value table</p>
<p>digitalWrite(d_b,num[n][1]);</p>
<p>digitalWrite(d_c,num[n][2]);</p>
<p>digitalWrite(d_d,num[n][3]);</p>
<p>digitalWrite(d_e,num[n][4]);</p>
<p>digitalWrite(d_f,num[n][5]);</p>
<p>digitalWrite(d_g,num[n][6]);</p>
<p>digitalWrite(d_dp,num[n][7]);</p>
<p>}</p>
<p>//**********************************************************************</p></td>
</tr>
</tbody>
</table>

6.  **Test Result**

Compile and upload the code to ESP32, after the code is uploaded
successfully, power up with a USB cable and you will see that the
4-digit 7-segment display displays 0-9999，and repeat these actions in an
infinite loop.
