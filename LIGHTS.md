Este documento foi escrito pelo GEMINI depois de uma pergunta especifica

Pixhawk uses an RC passthrough mechanism where a parameter is set to enable an AUX output to pass through the value of a specific RC input channel, allowing direct control of accessories like gimbals or lights by a switch or knob on the RC transmitter. You can configure this by setting the SERVOx_FUNCTION parameter to 1 (RC Passthrough) for the desired AUX port in the Mission Planner or QGroundControl, then assigning an RC input channel to it. 
Understanding RC Passthrough 

    Purpose:
    RC passthrough allows a specific RC channel's PWM value to be directly outputted by a Pixhawk's AUX port, which can then control a connected device like a servo for a camera gimbal or a light.
    Direct Control:
    The servo output will exactly match the incoming RC input, ignoring any trim, min, or max settings on the servo function. 

Configuration Steps

    Connect Your Receiver: Ensure your RC receiver is correctly connected to the Pixhawk. 

Open Ground Control Software: Launch Mission Planner (for ArduPilot) or QGroundControl (for PX4). 
Access Parameter List: Navigate to the full parameter list or tree. 
Find Servo Parameters: Locate the SERVOx_FUNCTION parameter that corresponds to the AUX output you want to use (e.g., SERVO9_FUNCTION for AUX output 9). 
Set Function to RC Passthrough: Change the value of this parameter to 1. 

Servo6_function = 1 (RC Passthrough) 

Assign RC Input Channel: Use the RCx_FUNCTION parameter (e.g., RC9_FUNCTION) to assign the input RC channel that will control this function. 
Map to Auxiliary Function (If Needed): For some airframes or applications, you may also need to set an auxiliary function (e.g., RC_MAP_MOUNT to map RC9 to mount yaw control) in the mount or RC mapping section of the software.

RC6_option = 28 (relay on/off) there is no RC6_function!!! for Ardurover V4.5.7 

BRD_TYPE = 14 (pixwack pro)

Important Considerations

    Low Current Bus:
    The AUX outputs are on a low-current bus, so it's best to power servos from a separate alternate source to avoid overloading it. 

Airframe & Mixer:
Some airframe configurations may have pre-configured passthrough mixers on certain AUX outputs. 
SBUS:
If you're using an SBUS receiver, you may need to subtract 16 from the SBUS channel number to get the correct RC channel number for the passthrough setting
