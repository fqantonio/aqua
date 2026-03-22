![](Photos/banner-772x250.png)

# Battery resume and overall FS parameters
AQUA as two bateries packs 4S4P in parallel, meaning that it is a 4S8P setup. Open voltage circuit is 16,7 V with a nominal voltage, 14.4 V (from the manufacturer) and a Cut-off Voltage of 12,0 V (conservative value). Notice that, for each 18650 we have a open circuit voltage of 3.6 V and cutoff 2,65 V, meaning a cutoff around 10.6 V for 4S setup (we use 3V as cutoff voltage). 

 - 4S means, since each 18650 cell as a 3.6 V nominal voltage (manufacturer rate, see: https://batteryservice.bg/wp-content/uploads/2019/11/samsung-35e-e.pdf), we get a whole nominal voltage of **14.4 V** $\ 4 \times 3.6 V \$.
 - 8P means that we add up the individual battery capacity (and energy), we get, since for each battery 2.5 Ah (conservative capacity value), $\8 \times 2.5 Ah \$, meaning 20 Ah for this setup.

So, at a velocity of 1 m/s (3,6 km/h), it has a conservative estimation of 5 hours of autonomy, corresponding to 20 000 mAh capacity and energy available of 288 Wh. The math goes like this:

$/ Energy = Power \times Time = Voltage \times Current \times Time = Voltage \times Capacity \$

Since the nominal voltage is 14.4 V, and the capacity is 20 Ah, so, dividing, we get:

$/ Energy = 14.4 V * 20 Ah = 288 Wh = 0.288 kWh \$

Using the graphs of the technical detail of Bluerobotics (https://bluerobotics.com/store/thrusters/t100-t200-thrusters/t200-thruster-r2-rp/) we can draw some reference operating parameters values.

AQUA as two thusters of 200 W each, capable of handling with 50 A max each. 

Operating at At 1 to 2 m/s velocities (3.6 to 7.2 km/h), current is around 1 to 2 A with voltage around 14.8 to 15.4 V. Each thusrter draws 15 W, so 30 W power in toal, means that at 30 W in total, with an 15.4 measured voltage (Notice that this thrusters have an optimal Operating Voltage between 12 and 16 V).

For these low currents, between 1 to 2 A, with a voltage range between 14 and 16, the PWM is 1360. At this PWM, the thrust is arroun 0.55 to 0.55 Kgf: each motor exerts 500 g, so both, 1 kg; the motors effeciency is really high: from 30.2 to 33.5 g/W (this means that, for each watt of power, we can push 33.5 g: so, if we have 30 W, we get around 1 kg of thrust).

Now, for the autonomy, we go with the max current for both thrusters, 2A, at 2 m/s of max velocity. Since we have 20 Ah, this means that, at a constant current of 2 A we have 10 hours of autonomy.

This are the theoretical values, lets measure it, and confirme the results listed here:

| date |	Velocity (m/s) |	Voltage (V) |	Current (A) | Observations |
|---|---|---|---|
| november 2025 | 1.4	| 15.4 	| 1.2 | not really acurate (to be confirmed) |
|  | 	| |  |  |
|  | 	| |  |  |
|  | 	| |  |  |
|  | 	| |  |  |

In conclusion, using the aqua in these conditions of very low velocities, we get the most efficiency regime of T200, in an optimal voltage range, for sure, of 5, but can be up to 6 or even 7 hours of autonomy.

So, for the operacional safety point of view, on MP, we set these parameters:

| Category |	Parameter |	Suggested Value |	Purpose |
|---|---|---|---|
| Monitoring | BATT_MONITOR	| 4	| Activates the monitoring of Voltage and Current|
| Power	| BATT_CAPACITY	| 20000 mAh	| Defines the total capacity for the dual 4S4P (4S8P) pack|
| BATT_LOW_MAH | 4000 |	Triggers alert battery at 20% capacity (4 Ah remaining) |
| Power	| BATT_LOW_VOLT	| 12V |	Should be 12,8V, but we are not conservative here; Safety trigger (3.2V per cell) for voltage-based failsafe, 20% capacity |
| Safety	| BATT_FS_LOW_ACT |	3 (RTL)	| Triggers automatic Return To Launch (Home) on low battery|
| Safety | BATT_FS_CRT_ACT |	3 (RTL)	| RTL in critical situations |
| Navigation	| CRUISE_SPEED |	1.0 m/s	| Nominal mission speed optimized for maximum efficiency|
|Control |	ATC_ACCEL_MAX	| 0.3 m/s²	| Softens acceleration to prevent voltage sag|
| Control | MOT_SLEWRATE |	50 |	Maxim motor change per second (avoid current pics) |
| Auto model, Way Points | WP_RADIUS |	2.0	m | No diretly involve but within the GPS error range in order to use less energy |
| Control | RTL_SPEED |	1.0 m/s |	Return to land in failsafe mode |
| Control | FS_GCS_ENABL |	1	| Not really necessary because we have radio, but it activates RTL if lossing the connection to Mission Planner|
| Control | FS_GCS_TIMEOUT|	60 s | Time of silence before activates the RTL |
| RADIO | FS_THR_ENABLE	| 1 | Enabled RTL protection if radio signal loss |
| RADIO | FS_THR_VALUE |	910	| PWM low value, meaning the system is no longer activated |

And follow this table as a reference to monitor the autonomy of AQUA:

| Voltage | Capacity % | Estimated Capacity | State of Charge |
|---|---|---|---|
| 16.8V | 100% | 20 Ah | Fully Charged (open circuit) |
| 16.0V | 100 % | 20 Ah | High Charge |
| 15.2V | 65% | 12 Ah | Stable Range |
| 14.4V | 50% | 10 Ah | Nominal Voltage |
| 13.6V | 30% | 6 Ah | Low Battery signal |
| 12.8V | 20% | 4 Ah | RTL activated, Critical Level (Failsafe Trigger) |

# DATA and CALCS
Samsung 18650-25R cell capacity and voltage: nominal capacity of 2,500 mAh (2.5 Ah) and a 16,8 V.

==== measure this values ====

AQUA has two BlueRobotics T200 thrusters (https://bluerobotics.com/store/thrusters/t100-t200-thrusters/t200-thruster-r2-rp/). Using this online data its possible to check that, at 1,7 A, we get a 1360 PWM, wich means a measured velocity of 1,5 m/s??? (measured with MP). 

Max Draw: A single T200 can draw up to 25A at full throttle (16V). Two could draw 50A.

1,7 A during and hour, means 1,7 Ah; since AQUA as 20 Ah, then, dividing, we get 11 hours of autonomy. Off course, turnings cost

### Energy Calculation (Wh)
To verify your energy value of 288 Wh, we use the nominal voltage:
$\ Energy (Wh)= 20,000 mAh \times 14.4 V ​= 288 Wh \$

This sentence uses $\` and \`$ delimiters to show math inline: $`\sqrt{3x-1}+(1+x)^2`$

## 4S4P configuration


---

Compare with this GEMINI title: Battery Voltage and Motor Current

Link: https://gemini.google.com/share/1584391ce280

Aqui tens o documento final consolidado, integrando os objetivos do projeto, a configuração técnica e as referências bibliográficas formatadas.

---

## Bibliographic References

### **Software & Navigation**

* **ArduPilot Dev Team.** (2024). *Rover & Boat Failsafes and Power Monitoring*. ArduPilot Official Documentation. [https://ardupilot.org/rover/docs/rover-failsafes.html](https://ardupilot.org/rover/docs/rover-failsafes.html)
* **Shuck, T.** (2013). *Development of Autonomous Optimal Cooperative Control in Small Unmanned Systems*. AFIT Scholar.

### **Energy & Battery Science**

* **Islam, S. M. R., Park, S. Y., & Balasingam, B.** (2020). Unification of Internal Resistance Estimation Methods for Li-Ion Batteries Using Hysteresis-Free Equivalent Circuit Models. *Batteries*, 6(2), 32. [https://doi.org/10.3390/batteries6020032](https://doi.org/10.3390/batteries6020032)
* **Linden, D., & Reddy, T. B.** (2010). *Handbook of Batteries*. McGraw-Hill Education (4th ed.). [Referência para cálculos de densidade energética e ciclos de vida].
* **Edge, J. S., et al.** (2021). Lithium ion battery degradation: what you need to know. *Physical Chemistry Chemical Physics*, 23(14), 8200-8221.



