![](Photos/banner-772x250.png)

# Battery resume parameters
AQUA as two bateries packs 4S4P, meaning that it is a 4S8P, at a velocity of 1 m/s, it as a conservative estimation of 5 hours of autonomy, corresponding to a 20 000 mAh capacity and an energy of 288 Wh. It works with a open voltage circuit of 16,8 V with a nominal voltage, from the manufacturer, of 14,4 V and a Cut-off Voltage of 12,0 V.

For the operacional point of view, on MP we should set these parameters:

| Category |	Parameter |	Suggested Value |	Purpose |
|---|---|---|---|
| Monitoring | BATT_MONITOR	| 4	| Activates the monitoring of Voltage and Current|
| Power	| BATT_CAPACITY	| 20000 mAh	| Defines the total capacity for the dual 4S4P (4S8P) pack|
| BATT_LOW_MAH | 4000 |	Triggers alert battery at 20% capacity (4 Ah remaining) |
| Power	| BATT_LOW_VOLT	| 12.8V |	Safety trigger (3.2V per cell) for voltage-based failsafe, 20% capacity |
| Safety	| BATT_FS_LOW_ACT |	2 (RTL)	| Triggers automatic Return To Launch (Home) on low battery|
| Safety | BATT_FS_CRT_ACT |	2 (RTL)	| RTL in critical situations |
| Navigation	| CRUISE_SPEED |	1.0 m/s	| Nominal mission speed optimized for maximum efficiency|
|Control |	ATC_ACCEL_MAX	| 0.3 m/s²	| Softens acceleration to prevent voltage sag|
| Control | MOT_SLEWRATE |	50 |	Maxim motor change per second (avoid current pics) |
| Auto model, Way Points | WP_RADIUS |	2.0	m | No diretly involve but within the GPS error range in order to use less energy |
| Control | RTL_SPEED |	1.0 m/s |	Return to land in failsafe mode |
| Control | FS_GCS_ENABL |	1	| Not really necessary because we have radio, but it activates RTL if lossing the connection to Mission Planner|
| Control | FS_GCS_TIMEOUT|	5.0 | Time of silence before activates the RTL |
| RADIO | FS_THR_ENABLE	| 1 | Enabled RTL protection if radio signal loss |
| RADIO | FS_THR_VALUE |	950	| PWM low value, meaning the system is no longer activated |

And follow this table as a reference to monitor the autonomy of AQUA:

| Voltage (Total) | Estimated Capacity | State of Charge |
|---|---|---|
| 16.8V | 100% | 20 Ah | Fully Charged, open circuit |
| 16.0V | 100 % | 20 Ah | High Charge |
| 15.2V | 65% | 12 Ah | Stable Range |
| 14.4V | 50% | 10 Ah | Nominal Voltage |
| 13.6V | 30% | 6 Ah | Low Battery signal |
| 12.8V | 20% | 4 Ah | RTL activated, Critical Level (Failsafe Trigger) |

# DATA and CALCS
Samsung 18650-25R cell capacity and voltage: nominal capacity of 2,500 mAh (2.5 Ah) and a 16,8 V.

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



