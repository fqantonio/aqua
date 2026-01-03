![](Photos/banner-772x250.png)

This is not completed...

Using a pixwack pin to control sommething with the radio channels, like a light or a gimball, there are two things you must know in advance:

1. There are two groups of pins, MAIN and AUX;
2. And, if you are using a SAFETY SWITCH, you must turn it on to test because, pixwack only activate those pins when it's on.

Its very easy: after version ardurover 4.2, you have to assign the SERVOx_function to a RCINx channel, just that!!! x is the channel/pin you want to use.

Material you need: a driver (mosfet) powered not by the pixwack, because it doesn't accept high currents;

STEPS

Connect Your Receiver: Ensure your RC receiver is correctly connected to the Pixhawk. 
Open Ground Control Software: Launch Mission Planner (for ArduPilot) or QGroundControl (for PX4). 
Access Parameter List: Navigate to the full parameter list or tree. 
Find Servo Parameters: Locate the SERVOx_FUNCTION parameter that corresponds to the AUX output you want to use; example: SERVO9_FUNCTION for AUX output 9). 
Assign RC Input Channel: Use the RCx_FUNCTION parameter (e.g., RC9_FUNCTION) to assign the input RC channel that will control this function. 

Important Considerations

    Low Current Bus:
    The AUX outputs are on a low-current bus, so it's best to power servos from a separate alternate source to avoid overloading it. 

