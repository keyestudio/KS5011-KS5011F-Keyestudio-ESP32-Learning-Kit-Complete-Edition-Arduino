**Project 13：Passive Buzzer**

1.  **Introduction**

In a previous project, we studied an active buzzer, which can only make
a sound and may make you feel very monotonous. In this project, we will
learn a passive buzzer and use the ESP32 control it to work. Unlike the
active buzzer, the passive buzzer can emit sounds of different
frequencies.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/b8f46441af8a96464075d155e6ff7610.jpeg" style="width:1.29375in;height:0.63125in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.59306in;height:1.45486in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/d1ea1bb2b2749820cab389d5b85b838b.png" style="width:0.52708in;height:0.63333in" /></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>Passive Buzzer *1</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/9197d4aff9356c585b7ef68e33a6881d.png" style="width:0.27986in;height:1.08819in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:0.90833in;height:0.23681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/fa38b2e3964d342d0a5c446490ff4811.png" style="width:0.59236in;height:0.57014in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>NPN Transistor(S8050)*1</td>
<td>1kΩResistor*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

**3. Component Knowledge**

![](/media/8d0020e53824072cbe9d4f7d2f8acb4f.png)

**Passive buzzer:** A passive buzzer is an integrated electronic buzzer
with no internal vibration source and it has to be driven by 2K-5K
square waves, not DC signals. The two buzzers are very similar in
appearance, but one buzzer with a green circuit board is a passive
buzzer and the other buzzer with black tape is an active buzzer. Passive
buzzers cannot distinguish between positive polarity while active
buzzers can.

![](/media/fc42c5ed014609ff0b290ee5361bb2fd.png)

**Transistor:** Please refer to project 12.

**4. Wiring Diagram**

![](/media/9c12d89ce3f10c838e63f1334f41fc9e.png)

5.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : Passive Buzzer</p>
<p>* Description : Passive Buzzer sounds the alarm.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#define LEDC_CHANNEL_0 0</p>
<p>// LEDC timer uses 13 bit accuracy</p>
<p>#define LEDC_TIMER_13_BIT 13</p>
<p>// Define tool I/O ports</p>
<p>#define BUZZER_PIN 15</p>
<p>//Create a musical melody list, Super Mario</p>
<p>int melody[] = ;</p>
<p>//Create a list of tone durations</p>
<p>int noteDurations[] = ;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>}</p>
<p>//**********************************************************************</p></td>
</tr>
</tbody>
</table>

6.  **Test Result**
    
    Compile and upload the code to ESP32, after the code is uploaded
    successfully, power up with a USB cable and you will see that the
    passive buzzer plays music.
