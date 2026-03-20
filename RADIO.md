![](Photos/banner-772x250.png)

# RADIO transmiter
To configure the radio transmitter to **manualy control** de boat by radio, follow this text (https://ardupilot.org/rover/docs/common-radio-control-calibration.html) and then this one for the boat, where you only change the FRAME_CLASS parameter to 2 (https://ardupilot.org/rover/docs/boat-configuration.html).

For the **binding** process, follow this video (https://www.youtube.com/watch?v=xRmlNQ3M3zE) or this link (https://manuals.plus/flysky/fs-ia6b-receiver-2-4g-6ch-with-double-antenna-manual);

Notice that, if your radio receiver is **already binded** with another transmitter then, you just have to plug the power and the shunt (black) as in the picture and remove the power once and plug again and the led will blink faster, meaning that the receiver is ready to bind. After this you follow the procedure of the video or the webpage above.

(put picture here)

Using Buttons SWC and SWD, channels 7 and 8, to make a misture of 6 "flights" modes.

Gemini Prompt:
FlySky i6 Flight Mode Switch Setup

link Gemini: 
https://gemini.google.com/share/9bb314468d82

Resume: 
To assign a 3-position switch (**SwC**) and a 2-position switch (**SwD**) to work together for 6 flight modes on the FlySky i6, follow this procedure:

### Phase 1: Assign Switches to Channels

1. Power on your transmitter and long-press **OK** to enter the menu.
2. Select **Functions Setup** and press **OK**.
3. Navigate to **Aux. channels** and press **OK**.
4. Set **Channel 5** to **Source: SwC** (Your 3-position switch).
5. Set **Channel 6** to **Source: SwD** (Your 2-position switch).
6. Long-press **CANCEL** to save and exit back to the menu.

### Phase 2: Configure the Mix

1. In the **Functions Setup** menu, select **Mix** and press **OK**.
2. Select **Mix #1** and press **OK**.
3. Change the setting to **On**.
4. Set **Master** to **Ch6** (The 2-position switch).
5. Set **Slave** to **Ch5** (The 3-position switch).
6. Set **Pos. mix** to **50%**.
7. Set **Neg. mix** to **50%**.
8. Set **Offset** to **0%**.
9. Long-press **CANCEL** to save these settings.

### Phase 3: Verify the Output

1. Navigate to the **Display** menu in **Functions Setup**.
2. Watch the bar for **Ch5**:
* With **SwD** in the "Up" position, move **SwC** through its 3 positions. You will see the bar move in the lower range.
* Flip **SwD** to the "Down" position, then move **SwC** through its 3 positions again. The bar will now move through 3 higher positions.


3. Ensure you have 6 distinct, non-overlapping positions on the **Ch5** bar.

### Phase 4: Flight Controller Calibration

1. Connect your drone to your computer (Betaflight, INAV, or Mission Planner).
2. Go to the **Modes** tab.
3. Assign your flight modes to **AUX 1** (which corresponds to Channel 5).
4. Adjust the range sliders to cover the specific "tick" marks created by your switch combinations.

Would you like me to help you adjust the **Pos. mix** percentage if the modes are overlapping in your software?

References:

    FlySky FS-i6 User Manual: Standard procedures for "Functions Setup" and "Aux. channels."

    ArduPilot/APM Documentation: Standard PWM ranges for 6-mode flight controllers (usually 1165, 1295, 1425, 1555, 1685, and 1815 microseconds).

    Betaflight/INAV Wiki: Instructions for mapping AUX channels to flight modes.

    RCwithAdam / Joshua Bardwell: Community guides for transmitter mixing logic.

FlySky FS-i6 6 Flight Mode Setup Guide

This video provides a visual walkthrough of the mixing menu and how to verify that your channel outputs are correctly spaced for a flight controller.
