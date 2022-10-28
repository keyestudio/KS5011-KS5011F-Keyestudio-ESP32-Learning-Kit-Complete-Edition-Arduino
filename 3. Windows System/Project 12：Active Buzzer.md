**Project 12：Active Buzzer**

1.  **Introduction**

Active buzzer is a sound component that is widely used as a sound
component for computers、printers、alarms、electronic toys and
phones、timers etc. It has an internal vibration source, just by
connecting to a 5V power supply, it can continuously buzz. In this
project, we will use ESP32 to control the active buzzer to beep.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/b8f46441af8a96464075d155e6ff7610.jpeg" style="width:1.29375in;height:0.63125in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.59306in;height:1.45486in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/4b4f653a76a82a3b413855493cc58fba.png" style="width:0.86111in;height:0.70069in" /></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>Active buzzer*1</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/9197d4aff9356c585b7ef68e33a6881d.png" style="width:0.27986in;height:1.08819in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/098a2730d0b0a2a4b2079e0fc87fd38b.png" style="width:0.90833in;height:0.23681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/c801a7baee258ff7f5f28ac6e9a7097b.png" style="width:0.80833in;height:0.77778in" /></td>
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

**3.** **Component Knowledge**

![](/media/11ec5ddc982db9928341e858aab94652.png)

**Active buzzer:** Active buzzer inside has a simple oscillator circuit,
which can convert constant direct current into a certain frequency pulse
signal. Once active buzzer receives a high level, it will produce sound.
Passive buzzer is an internal without vibration source integrated
electronic buzzer, it must be driven by 2k to 5k square wave, rather
than a DC signal. The two buzzers are very similar in appearance, but
one buzzer with a green circuit board is a passive buzzer, while the
other buzzer with black tape is an active buzzer. Passive buzzers don't
have positive polarity, but active buzzers have. As shown below:

![](/media/0f9825969867ac2d65bb1a19ed0ad2ab.png)

**Transistor:**

![](/media/9197d4aff9356c585b7ef68e33a6881d.png)

Since the buzzer requires such large current that GPIO of ESP32 output
capability cannot meet the requirement, a transistor of NPN type is
needed here to amplify the current.

Transistor, the full name: semiconductor transistor, is a semiconductor
device that controls current. Transistor can be used to amplify weak
signal, or work as a switch. It has three electrodes(PINs): base (b),
collector (c) and emitter (e).

When there is current passing between "be", "ce" , which will allow
several-fold current (transistor magnification) pass, at this point,
transistor works in the amplifying area. When current between "be"
exceeds a certain value, "ce" , which will not allow current to increase
any longer, at this point, transistor works in the saturation area.
Transistor has two types as shown below: PNP and NPN,

![](/media/02dad9f2fcac0d7bfe4cc135d2301aa6.png)

PNP transistor NPN transistor

In our kit, the PNP transistor is marked with 8550, and the NPN
transistor is marked with 8050.

Based on the transistor's characteristics, it is often used as a switch
in digital circuits. As micro-controller's capacity to output current is
very weak, we will use a transistor to amplify current and drive
large-current components.

When using the NPN transistor to drive a buzzer, we often adopt the
following method. If GPIO outputs high level, current will flow through
R1, the transistor will get conducted, and the buzzer will sound. If
GPIO outputs low level, no current flows through R1, the transistor will
not be conducted, and buzzer will not sound.

When using the PNP transistor to drive a buzzer, we often adopt the
following method. If GPIO outputs low level, current will flow through
R1, the transistor will get conducted, and the buzzer will sound. If
GPIO outputs high level, no current flows through R1, the transistor
will not be conducted, and buzzer will not sound.

![](/media/2a9755ec14ab58c67d7d8341601d8dbc.png)

4.  **Wiring Diagram**
    
    ![](/media/5c215684c8945622441478edb6f16e30.png)

Note: The buzzer power supply in this circuit is 5V. On a 3.3V power
supply, the buzzer can work, but it will reduce the loudness.

5.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//***********************************************************************/*</p>
<p>* Filename : Active Buzzer</p>
<p>* Description : Active buzzer beeps.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#define buzzerPin 15 //define buzzer pins</p>
<p>void setup ()</p>
<p></p>
<p>void loop ()</p>
<p></p>
<p>//***********************************************************************</p></td>
</tr>
</tbody>
</table>

6.  **Test Result**
    
    Compile and upload the code to ESP32, after the code is uploaded
    successfully, power up with a USB cable and you will see that the
    active buzzer beeps.
