# BEFORE

- Feetching the maps with Mission Planner (PM) in a computer with internet access beforehand;
- Check the site permissions to test/use the AQUA;
- Materials check list: computer; trolley; wooden platform; box (roap; fenders; basic tools; USB cables; charger; telemetry radio); dingy if possible;

update about this...
- Operation mode: NORMAL or SIMPLE or AUTO? (WICH BUTTONS!?!?!?)
https://ardupilot.org/rover/docs/boat-configuration.html
- Types of ArduBoat driving modes

    Autonomous Modes:
        Auto: Follows a pre-programmed mission, often from a ground station.
        Guided: Follows a specific command from the ground station, like moving to a new waypoint.
    Position-Holding Modes:
        Loiter: Holds the boat in its current position, even after it reaches a destination.
        PosHold: Holds the vehicle's current position in altitude and location.
    Return/Landing Modes:
        RTL (Return-to-Launch): Commands the boat to return to its starting point.
        SmartRTL: A variation of RTL that attempts to maintain position after reaching the destination.
        Land: Commands the boat to land at its current location.
    Manual/Assisted Control Modes:
        Manual: The pilot has direct control over the vehicle's motors and movement.
        Acro: Requires pilot input to hold heading and roll, with no automatic stabilization.
        Stabilize: A form of assisted control where the vehicle self-levels its attitude when the control sticks are released.
- In the case of AUTO, ways point settled??? https://ardupilot.org/planner/docs/common-mission-planning.html

### SOUNDS AND LED SIGNS

LEDS
https://ardupilot.org/copter/docs/common-leds-pixhawk.html

Safety switch LED meaning¶
Constant blinking - system is initialising
Intermittent blinking - system is ready but in the “Safety” state. press the safety switch to enable output to the motors and control surfaces if already armed, or to cancel the pre-arm error condition that prevents arming.
Solid - safety switch has been pressed, motors and servos are able to move once the vehicle is armed.

https://ardupilot.org/copter/docs/common-safety-switch-pixhawk.html


TONES
https://ardupilot.org/copter/docs/common-sounds-pixhawkpx4.html#common-sounds-pixhawkpx4
https://bluerobotics.com/store/thrusters/speed-controllers/besc30-r3/

# DURING OPERATIONS

## START
- Connect the telemetry radio to the USBC in the computer
- Turn on the computer and open MP;
- open the starboard float cover
- Turn on the main power switch (see picture: put picture here!?!?!?): verify sounds and PIX4 led colors: motor DRIVER sounds mean that they are connected connected;
- Conecting MP to the pixhwack (upper button on the right of the MP screen);
- Turn on the radio transmitter (verify green led in the receiver: changing from blinking to solid red);
- Check the battery voltage;
- Turn on the safety switch on: it will change from blinking to solid light and emit two tones indicating initialization
- Close the starboard float cover;
- Put the boat in the water: if needed use a roap for safety: tie up the boat at the pier
- Everything ready to arm the AQUA?
  - check list:  Security check: no other boats, people or obstacles around AQUA?
  - No warning signals; leds normal; 
- At MP push the ARM/DISARM button: down left window;
- Untie AQUA
- Drive AQUA mission
- ATTENTION to voltage levells and safety screen warnings, namelly (??!?!?)

## STOP

- Take AQUA to safety shore
- Tie it
- DISARM at MP if necessary

## RESTART

- untie
- ARM at MP
- Drive AQUA

## END

- Disarm at MP;
- open the starboard float cover
- Turn off motor switch (from solid red led to blink)
- Turn of power if necessary
- Bring AQUA to shore
- Clean as much as possible with fresh water: be carefull with the entrances of water inside AQUA

# AFTER

- If necessary, unscrew the white light
- collect tools and utensils in the bag and box
- put everything in the trolley
- Use the wooden platform to help you get AQUA into the car
