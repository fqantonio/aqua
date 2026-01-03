(under construction)

# Operation mode
NORMAL, AUTO, LOITER, GUIDED, SRTL, ACRO;
Right buttons: VRC, VRD (look into MP)
https://ardupilot.org/rover/docs/boat-configuration.html

Types of ArduBoat driving modes

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
