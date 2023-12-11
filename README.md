# Security-Motion-Sensor-Lights
In this repository, the user can create a security motion sensor that will covertly alert the user of any movement in unmonitored locations by turning on an LED light. The user can then press the button to turn the light off. 

To create this game, you will need:
- Raspberry Pi
- breadboard
- PIR HC-SR501
- Red LED light
- Button
- Jumper Wires

Step 1:
The user will first attach the PIR HC-SR501 to the Breadboard. Below, I have for you an example using Tinkercad.   
<img width="637" alt="Step 1" src="https://github.com/GCastillo1775/Motion-Sensor-Lights/assets/150841918/7a3649a0-4cfd-45ed-af6a-73a641b182db">

The PIR has three output pins: VCC, Output, and Ground. The VCC connects to the 5-volt port on the Raspberry Pi; The output pin will connect to the GP10 14 port on the Raspberry Pi. The ground pin will connect to the ground port. The user will utilize jumper wires to connect all the PIR pins to the Raspberry Pi.

Step 2:
In the next step, the user will connect the LED light. Since this is a security system the LED light color should be red to limit its visibility. 
<img width="677" alt="Step 2" src="https://github.com/GCastillo1775/Motion-Sensor-Lights/assets/150841918/e869f7a1-f49e-41d3-9f5a-66d210c19639">

For the light, the user needs to use a 330-ohm resistor to limit the supply that the LED light will draw from the Raspberry Pi. Failure to use the resistor can result in damage to your Raspberry Pi. The user must ensure that they place the resistor between the anode and the jumper wire that connects the breadboard to the GP10 23 pin on the Raspberry Pi. The shorter leg of the LED, known as the cathode, will be connected to the ground.

Step 3:
The user will connect the button to the breadboard in this final step.
<img width="583" alt="Step 3" src="https://github.com/GCastillo1775/Motion-Sensor-Lights/assets/150841918/273a30b1-811f-4c0c-ba34-29c4c30c598c">

The button in this tool is used to reset the security system. Since this is a security system, if there was motion while the user was away, having an automatic shutoff could potentially prevent the user from being aware of the alert.

Code:
Since the user is using a Raspberry Pi, they will be able to use the "thonny" application located at the top left of their screen. 

<img width="416" alt="step 4" src="https://github.com/GCastillo1775/Motion-Sensor-Lights/assets/150841918/2a72c3e3-9e41-42c0-ade1-eca7d45c4f49">

Once opened, it should look similar to this:

<img width="623" alt="step 5" src="https://github.com/GCastillo1775/Motion-Sensor-Lights/assets/150841918/c6446c27-a8a7-4039-9e09-8f89134ef4a3">

In the Upper screen, the user will then paste the following code:

```
from gpiozero import LED, Button, MotionSensor
from signal import pause

led = LED(23)
button = Button(16)
pir = MotionSensor(14)

pir.when_motion = led.on 
button.when_pressed = led.off 
pause()
```
