**Project 18：Small Fan**

1.  **Introduction**

In hot summer, we need electric fans to cool us down, so in this
project, we will use a ESP32 to control a DC motor and small fan blades
to make a small electric fan.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:2.17847in;height:1.0625in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.94722in;height:2.32014in" /></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/5fe5f8cd6e75e7f8d4ec71f54a4ac2f5.png" style="width:0.87292in;height:0.37083in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/5eba8bae9e1d18b959ca425a9cc83fd2.jpeg" style="width:1.07569in;height:0.43472in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/655e6c465cb423279e0908513a983711.png" style="width:0.85694in;height:0.75347in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/df3db6765ee8c86beafa8410e87dd50d.png" style="width:0.77361in;height:0.76944in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
</tr>
<tr class="even">
<td>L293D Chip*1</td>
<td>DC Motor*1</td>
<td>Fan*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/b65d826ca481982fed0212dba2957c7c.jpeg" style="width:1.57361in;height:1.13611in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/6734084c96238569a513a5ff3190621d.png" style="width:1.15486in;height:0.49861in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5011-KS5011F-Keyestudio-ESP32-Learning-Kit-Complete-Edition-Arduino/master/media/a815c48437199c6ab79d74cd2d583de0.png" style="width:0.24722in;height:1.14097in" /></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Battery Holder*1</td>
<td>Keyestudio Breadboard special power module*1</td>
<td>No.5 Battery (self-provided)*6</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

3.  **Component Knowledge**

![](/media/5fe5f8cd6e75e7f8d4ec71f54a4ac2f5.png)

**L293D Chip:** The L293D is a DC motor driver IC that can be used to
drive dc motors or stepper motors in some robotics projects.  It has 16
pins and can drive 2-channel DC motors at the same time.  Its input
voltage range is 4.5V \~ 36V, and each channel output current is MAX
600mA, which can drive the inductive load, especially its input terminal
can be directly connected with the single chip microcomputer.

Therefore, it is very convenient to be controlled by the single chip
microcomputer.  When driving a small DC motor, 2-channel motors can be
directly controlled, and the motor can be positive and reverse.

In order to achieve this function we solely need to change the input
high and low level. There are many motor driver boards of L293D chips in
the market, of course, we can also use them through simple connection. 

**Diagram of the L293D pins**

![](/media/2e5e0bd5b4577ac159d0568404dc21b5.png)

<table>
<tbody>
<tr class="odd">
<td>#</td>
<td>Name</td>
<td>Description</td>
</tr>
<tr class="even">
<td>1</td>
<td>Enable1</td>
<td>Input 1(2) and 2(7)</td>
</tr>
<tr class="odd">
<td>2</td>
<td>In1</td>
<td>Control output pin1</td>
</tr>
<tr class="even">
<td>3</td>
<td>Out1</td>
<td>Connect to one end of motor 1</td>
</tr>
<tr class="odd">
<td>4</td>
<td>0V</td>
<td>Connect to grounding (0V) of the circuit</td>
</tr>
<tr class="even">
<td>5</td>
<td>0V</td>
<td>Connect to grounding (0V) of the circuit</td>
</tr>
<tr class="odd">
<td>6</td>
<td>Out2</td>
<td>Connect to the other end of motor 1</td>
</tr>
<tr class="even">
<td>7</td>
<td>In2</td>
<td>Control output pin2</td>
</tr>
<tr class="odd">
<td>8</td>
<td>+V motor</td>
<td>Connect to the voltage pins of the running motor(4.5V to 36V)</td>
</tr>
<tr class="even">
<td>9</td>
<td>Enable2</td>
<td>Input 3(10) and 4(15)</td>
</tr>
<tr class="odd">
<td>10</td>
<td>In3</td>
<td>Control output pin3</td>
</tr>
<tr class="even">
<td>11</td>
<td>Out3</td>
<td>Connect to one end of motor 2</td>
</tr>
<tr class="odd">
<td>12</td>
<td>0V</td>
<td>Connect to grounding (0V) of the circuit</td>
</tr>
<tr class="even">
<td>13</td>
<td>0V</td>
<td>Connect to grounding (0V) of the circuit</td>
</tr>
<tr class="odd">
<td>14</td>
<td>Out4</td>
<td>Connect to the other end of motor 2</td>
</tr>
<tr class="even">
<td>15</td>
<td>In4</td>
<td>Control output pin4</td>
</tr>
<tr class="odd">
<td>16</td>
<td>+V</td>
<td>Connect to+ 5V to enable IC function</td>
</tr>
</tbody>
</table>

**Keyestudio Breadboard Power Supply Module**

![](/media/7ff03f4506988f1ce99c5757892fc6de.jpeg)

**Introduction**

This breadboard power supply module is compatible with 5V and 3.3V,
which can be applied to MB102 breadboard. The module contains two
channels of independent control, powered by the USB all the way.

The output voltage is constant for the DC5V, and another way is powered
by DC 7-12V, output controlled by the slide switch, respectively for
DC5V and DC3.3V.

If the other power supply is DC 7-12v, when the slide switch is switched
to +5V, the output voltages of the left and right lines of the module
are DC 5V. When the slide switch is switched to +3V, the output voltage
of the USB power supply terminal of the module is DC5V , and the output
voltage of the DC 7-12V power supply terminal of the other power supply
is DC3.3V.

**Specification**

  - Applied to MB102 breadboard

  - Input voltage：DC 7-12V or powered by USB

  - Output voltage：3.3V or 5V

  - Max output current：\<700mA

  - Up and down two channels of independent control, one of which can be
    switched to 3.3V or 5V

Comes with two sets of DC output pins, easy for external use

4.  **Wiring Diagram**
    
    ![](/media/b7a0a9defecdb20f2d070aa9920dfe69.png)

(Note: Connect the wirings and then install a small fan blade on the DC
motor. )

5.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Small Fan</p>
<p>* Description : Fan clockwise rotation,stop,counterclockwise rotation,stop,cycle.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#define IN1 2 // the IN1 pin of the L293D</p>
<p>#define IN2 15 //the IN2 pin of the L293D</p>
<p>#define ENA_pwm 0 //the ENA-pwm pin of the L293D</p>
<p>void setup()</p>
<p></p>
<p>void loop()</p>
<p></p>
<p>//********************************************************************************</p></td>
</tr>
</tbody>
</table>

6.  **Test Result**
    
    Compile and upload the code to ESP32, after the code is uploaded
    successfully, power on the external power supply and power up, then
    you will see that the small fan turns counterclockwise for 5s and
    stops for 2s, and then turns clockwise for 5s and stops for 2s,
    which repeats in an endless loop.
