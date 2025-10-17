Safety issues. This a GEMINI text to the question why the safety switch is giveing a a warning and the batery is  full...!?!?!?

This is a very common issue with Pixhawk (ArduPilot or PX4 firmware) systems! The low battery warning is usually triggered based on **voltage** and/or **remaining capacity** thresholds configured in the flight controller, and if those settings are incorrect, you can get a false alarm even with a fully charged battery.

Here are the most likely causes and what you should check:

### 1. Incorrect Battery Monitor Calibration (Most Common)

The Power Module (or "Power Brick") connected to the Pixhawk measures the battery voltage and current. If the internal scaling factor is wrong, the flight controller will read an incorrect, usually lower, voltage.

**What to check and how to fix it:**

* **Check the Voltage Reading:** Connect your Pixhawk to a Ground Control Station (GCS) like **Mission Planner (for ArduPilot)** or **QGroundControl (for PX4)**. Look at the live battery voltage reading.
* **Measure the True Voltage:** Use a **multimeter** to measure the voltage directly at your battery's connector.
* **Compare and Calibrate:** If the GCS voltage is significantly lower than the multimeter voltage, you need to calibrate the Power Module's voltage divider ratio.
    * **In Mission Planner (ArduPilot):** Go to **Initial Setup > Optional Hardware > Battery Monitor** (or **Setup > Battery Monitor**). You'll typically be asked to enter the measured voltage (from your multimeter) next to the displayed voltage (from the GCS). The software will calculate the correct **Voltage Divider** value.
    * **In QGroundControl (PX4):** Go to **Vehicle Setup > Power** and check/correct the **Voltage Divider** setting.

* *Example of a common error:* One user reported their Pixhawk Power Module was reading $2 \text{V}$ below the actual voltage, which was fixed by performing the proper calibration.

### 2. Incorrect Low Voltage Thresholds

The Pixhawk has parameters that define what constitutes a "low" or "critical" battery level, either by a minimum **voltage** or minimum **remaining capacity (mAh)**. If these thresholds are set too high for your specific battery, the alarm will trigger too early.

**What to check and how to fix it (for ArduPilot/Mission Planner):**

Look at these parameters and adjust them if necessary (or check the corresponding settings in QGroundControl):

* **`BATT_LOW_VOLT`:** The voltage level (per cell or total, depending on the parameter) that triggers the **low** action (usually a warning or Return-To-Launch/Home (RTL)).
* **`BATT_CRT_VOLT`:** The voltage level that triggers the **critical** action (usually an immediate Land).
* **`BATT_LOW_MAH` / `BATT_CRT_MAH`:** The remaining battery capacity (in mAh) that triggers the low/critical actions.

**Typical LiPo guidelines:**
* A fully charged LiPo cell is $4.2 \text{V}$.
* The voltage alarm is usually set around **$3.5 \text{V}$ to $3.7 \text{V}$ per cell** under *load*.
* For a fully charged $3\text{S}$ battery ($\sim 12.6 \text{V}$), an incorrect alarm may trigger if a low voltage like $11.1 \text{V}$ is set too high or the voltage reading is off (see point 1).

### 3. Incorrect Battery Capacity Parameter

The flight controller uses the defined battery capacity to estimate the remaining percentage. If the set capacity is **too low** (e.g., set to $3000 \text{mAh}$ for a $5000 \text{mAh}$ battery), the estimated remaining capacity will drop quickly, triggering the capacity-based low battery warning prematurely.

**What to check and how to fix it (for ArduPilot/Mission Planner):**

* **`BATT_CAPACITY`:** Ensure this parameter is set to the correct rated capacity (in mAh) of your battery.

### 4. Poor Physical Connections

A loose or damaged connection between the battery, the Power Module, and the Pixhawk can cause a momentary or continuous **voltage drop** which the flight controller interprets as a low battery.

**What to check:**

* **Inspect all cables** for wear or damage.
* **Ensure the Power Module connector** is fully and firmly seated on the Pixhawk.
* **Check the main battery connector** for corrosion or a poor fit.

### 5. Faulty Power Module or Pixhawk

If you have tried calibration and checked the parameters without success, the Power Module itself might be faulty and reading the voltage incorrectly, or there could be an issue with the voltage sensing circuitry on the Pixhawk.

**What to try:**

* **Check the $5 \text{V}$ rail:** Some issues are related to the $5 \text{V}$ power supplied by the Power Module's BEC. Use a multimeter to measure the $5 \text{V}$ pins on the Power Module connector to ensure they are stable and near $5.3 \text{V}$ (as suggested in some forums).
* **Try a different Power Module or Battery:** If possible, swap the Power Module or use another known-good battery to see if the problem persists.

**In summary, the most immediate steps are:**

1.  **Check the live voltage reading** in your GCS (Mission Planner/QGroundControl).
2.  **Measure the battery voltage** with a multimeter.
3.  **Calibrate the Battery Monitor** in your GCS if the readings do not match.
4.  **Verify the `BATT_LOW_VOLT` and `BATT_CAPACITY`** parameters are correctly set for your battery.

Monitoring and calibration BATT_MONITOR: Selects the battery monitoring type. Common values are \(3\) for voltage-only and \(4\) for both voltage and current.BATT_VOLT_PIN: Specifies the autopilot's analog pin connected to the power module's voltage sensing output.BATT_CURR_PIN: Specifies the autopilot's analog pin connected to the power module's current sensing output.BATT_VOLT_MULT: Scales the raw voltage reading from the sensor to get the actual battery voltage.BATT_AMP_PERVLT: Converts the voltage reading from the current sensor into a current reading in amps.BATT_AMP_OFFSET: Adjusts for any voltage offset from the current sensor when no current is being drawn.BATT_CURR_MULT: Scales reported current values for specific monitors like DroneCAN. Failsafe and safety BATT_LOW_VOLT: The voltage threshold for the "low battery" warning and action.BATT_CRT_VOLT: The voltage threshold for the "critical battery" warning and action. Set to zero to disable.BATT_LOW_MAH: The remaining capacity in mAh for the "low battery" failsafe.BATT_CRT_MAH: The remaining capacity in mAh for the "critical battery" failsafe.BATT_FS_LOW_ACT: The action to take when the low battery threshold is reached, such as "RTL" (Return to Launch) or "Land".BATT_FS_CRT_ACT: The action to take when the critical battery threshold is reached.BATT_ARM_VOLT: The minimum voltage required to arm the vehicle.BATT_ARM_MAH: The minimum remaining capacity in mAh required to arm the vehicle. Other parameters BATT_CAPACITY: Automatically updated to the battery's actual capacity in mAh after it's been used.BATT_SERIAL_NUM: Used for SMBus or DroneCAN monitors to identify which battery it is monitoring.BATT_MAX_AMPS: The maximum current to be reported, primarily for INA2xx sensors. 

https://ardupilot.org/rover/docs/common-power-module-configuration-in-mission-planner.html
