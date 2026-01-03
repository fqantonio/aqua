![](Photos/banner-772x250.png)

In this projet we set the vehicle to set an alarm by telemetry when the voltage drop under 12 V. Since its a 4S4P system, 16,8 V is the full battery voltage and 13,8 Ah. See data results. 

Note: It shoul be interesting to have a smart RTL (SRTL) as a predefined fail safe action

# DATA and CALCS
Capacity calculation Samsung 18650-25R cell capacity: The individual Samsung 18650-25R cell has a nominal capacity of 2,500 mAh (2.5 Ah).

## 4S4P configuration
This configuration means: 4S (4 cell bateries in series): Four cells are connected in series, which increases the total voltage up to 16,8 V. The capacity remains the same as a single parallel group. 

4P (4 parallel): Four parallel groups of cells are connected together, which multiplies the total capacity by four. 

Calculation: To find the total capacity of the pack, you multiply the capacity of a single cell by the number of cells in parallel.\(2,500\ mAh\times 4\ (parallel\ cells)=10,000\ mAh\) 

We are using your 4S4P battery pack with a conservative strategic point of view that can deliver a 30% of remain capacity, with a maximum capacity of 10,000 mAh (10 Ah), the total runtime with two bluerobotics thrusters of 200W each.

We suppose that this will have an autonomy of 1.25 hours. 

Here is the step-by-step breakdown: Calculate the pack's total energy capacity:Nominal voltage (4S configuration): \(4\ cells\times 3.6\ V/cell=14.4\ V\)Total capacity in Watt-hours (Wh): \(10\ Ah\times 14.4\ V=144\ Wh\)Calculate the average energy draw over time:Energy used at 200W: This is the power multiplied by the fraction of time.\(200\ W\times 40\%=200\ W\times 0.4=80\ W\)Energy used at 100W:\(100\ W\times 60\%=100\ W\times 0.6=60\ W\)Average power consumption: Add the weighted power values together.\(80\ W+60\ W=140\ W\)Calculate the total runtime:Divide the battery pack's total energy capacity by the average power consumption.\(144\ Wh\ /\ 140\ W\approx 1.03\ hours\)Convert the runtime to minutes:\(1.03\ hours\times 60\ minutes/hour\approx 62\ minutes\) Note: The initial estimation was slightly incorrect due to a rounding error in the second step of calculation. 

A corrected estimation is included below, followed by further considerations for practical applications. Recalculating with a more detailed method A more precise way to calculate the runtime with a variable load is to find the total energy consumed over one cycle and divide the battery's total energy by that. Calculate total energy consumed in one hour:Energy consumed at 200W (40% of hour): \(200\ W\times 0.4\ hr=80\ Wh\)Energy consumed at 100W (60% of hour): \(100\ W\times 0.6\ hr=60\ Wh\)Total energy consumed per hour: \(80\ Wh+60\ Wh=140\ Wh\)Calculate the total runtime:Battery pack capacity: \(144\ Wh\)Divide the total capacity by the hourly consumption: \(144\ Wh/140\ Wh/hr\approx 1.03\ hours\)Convert to minutes: \(1.03\ hr\times 60\approx 62\ minutes\) Practical considerations Depth of Discharge (DoD): Repeatedly fully draining the battery (100% DoD) will shorten its lifespan. To maximize the battery life, it's recommended to discharge it less, such as to 80% DoD. T

his reduces the usable capacity, but significantly increases the number of charge cycles.Battery Management System (BMS): A BMS is essential for a battery pack, especially in a series configuration. It protects against over-charging, over-discharging, over-current, and short-circuits. It also ensures the cells remain balanced, which is crucial for safety and performance.Battery age and temperature: These factors can impact the battery's actual performance. Older batteries or batteries used in extreme temperatures may have a lower capacity. As respostas de IA podem incluir erros. Saiba maisA criar um link público…Não foi possível criar o link. Tente mais tarde.Esta discussão não é compatível com a partilha.You can now share this thread with othersObrigadoO seu feedback ajuda a Google a melhorar. Consulte a nossa Política de Privacidade.Partilhar mais feedbackComunicar um problemaFechar10 sites10 sitesElectricity Calculator: Power Consumption kWh Estimator29/01/2025 — How to calculate power consumption in your home. Your monthly energy bill accounts for how much electricity you use to p...SaveOnEnergy.comBattery Capacity CalculatorWhat are battery amp hours? The primary function of a battery is to store energy. We usually measure this energy in watt-hours, wh...Omni CalculatorHow to Calculate Lithium Battery Capacity, Runtime, and ...23/05/2025 — Understanding Lithium Battery Capacity * Overview. The capacity of a lithium battery shows how much energy it can hold, ...yibaienergy-china.comBattery Run Time Calculator16/02/2025 — That ends guesswork. * Battery run time is the length of time a device operates from a fully charged battery until it ru...vibms.comSamsung INR18650-25R 2500 mAh 3.6V - 3.7V Li-ion industrial cell.Samsung INR18650-25R 2500 mAh 3.6V - 3.7V Li-ion industrial cell. akkuteile.de. ... * Lithium-Ionen Battery. * Size 18650. * Samsu...AkkuteileHow to calculate battery energy - x-engineer.orgCalculate the energy content of a Ni-MH battery cell, which has the cell voltage of 1.2 V and current capacity of 2200 mAh. * Step...x-engineer.orgHow to Choose the Backup Battery for Two-Story Modular HomesFormula: Capacity (Wh) ÷ total load (W) = runtime in hours.EcoFlowHow Long Will a 100Ah Battery Last？- MANLY14/05/2023 — Adjusted Runtime Calculation Chart (Considering Temperature and 80% DOD) DOD and Lifespan: Frequently discharging a batt...MANLY BatteryEngineering Document NumberThe deeper the discharge, (e.g., DoD 100% means a completely discharged battery), the shorter the battery life in its estimated li...RebacasFor a science project, Kenji is studying the rate that a cell p...01/10/2025 — The battery starts at 100% charge ( B( 0)= 100).Filo10 sitesElectricity Calculator: Power Consumption kWh Estimator29/01/2025 — How to calculate power consumption in your home. Your monthly energy bill accounts for how much electricity you use to p...SaveOnEnergy.comBattery Capacity CalculatorWhat are battery amp hours? The primary function of a battery is to store energy. We usually measure this energy in watt-hours, wh...Omni CalculatorHow to Calculate Lithium Battery Capacity, Runtime, and ...23/05/2025 — Understanding Lithium Battery Capacity * Overview. The capacity of a lithium battery shows how much energy it can hold, ...yibaienergy-china.comMostrar tudoIgnorarCarregar imagem

The 80% capacity threshold
A widely accepted industry benchmark for a rechargeable battery nearing the end of its useful life is when its capacity has degraded to 80% of its original rating. At this point, the battery has a lower maximum state of charge, which can lead to shorter runtimes, and may struggle to deliver peak performance. 
For your 10,000 mAh pack, a low capacity would be anything less than 8,000 mAh (80% of 10,000 mAh). This reduction in capacity would reduce your average runtime from about 62 minutes to roughly 50 minutes.

## DATA

Results...

## Fail Safe triger

Low battery trigger:
BATT_LOW_VOLT (or FS_BATT_VOLTAGE) = 14V??? duration 10 seconds??? Fail safe trigered: FS can be smmart RTL!?!?!?

in percentage!?!?!? BATT_LOW_MAH. 

lower threshold BATT_CRT_VOLT = 12V and BATT_CRT_MAH.

severe failsafe action: smart return to land

Override:
The failsafe can be overridden by the pilot by switching the vehicle to a different mode using the RC controller or ground control station, as long as a valid mode is available. 
Reset:
After the battery is replaced, the failsafe must be manually reset by disarming the vehicle and using a command in the ground control software, like Mission Planner, to acknowledge that a fresh battery has been installed. 

Configuration

    The settings are typically configured in the safety setup page of a ground control software like QGroundControl. 

Users can adjust the voltage and capacity thresholds, disable them by setting them to zero, and choose the failsafe action

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
