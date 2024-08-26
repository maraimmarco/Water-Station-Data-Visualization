# Water Management DAX Calculations

This documentation outlines the DAX formulas used for calculating water distribution, consumption, losses, and theft in a water management system.

## 1. Total Water Distributed

This calculation sums up the total input flow from various water stations (Debaa, Jeddah, Joupel, and Shoaeba).



```DAX 
Total_Water_Distributed =
SUM(Debaa_In_Out[Total_input_Flow]) +
SUM(Jeddah_In_Out[Total_input_Flow]) +
SUM(Joupel_In_Out[Total_input_Flow]) +
SUM(Shoaeba_In_Out[Total_input_Flow])
```
## 2. Metered Consumption
This formula calculates the metered water consumption, considering only the operational pumps from each water station. Each station's output flow is summed up only when the corresponding pumps are not zero.
```Metered_Consumption =
VAR DebaaFlow =
CALCULATE(
SUM('Debaa_In_Out'[Total_Output_Flow]),
'Debaa_In_Out'[Flow_Pump_1] <> 0 ||
'Debaa_In_Out'[Flow_Pump_2] <> 0 ||
'Debaa_In_Out'[Flow_Pump_3] <> 0 ||
'Debaa_In_Out'[Flow_Pump_4] <> 0 ||
'Debaa_In_Out'[Flow_Pump_5] <> 0 ||
'Debaa_In_Out'[Flow_Pump_6] <> 0 ||
'Debaa_In_Out'[Flow_Pump_7] <> 0 ||
'Debaa_In_Out'[Flow_Pump_8] <> 0
)
VAR JeddahFlow =
CALCULATE(
SUM(Jeddah_In_Out[Total_Output_Flow]),
'Jeddah_In_Out'[Flow_Pump_1] <> 0 ||
'Jeddah_In_Out'[Flow_Pump_2] <> 0 ||
'Jeddah_In_Out'[Flow_Pump_3] <> 0 ||
'Jeddah_In_Out'[Flow_Pump_4] <> 0 ||
'Jeddah_In_Out'[Flow_Pump_5] <> 0 ||
'Jeddah_In_Out'[Flow_Pump_6] <> 0 ||
'Jeddah_In_Out'[Flow_Pump_7] <> 0 ||
'Jeddah_In_Out'[Flow_Pump_8] <> 0 ||
'Jeddah_In_Out'[Flow_Pump_9] <> 0 ||
'Jeddah_In_Out'[Presure_Pump_10] <> 0
)
VAR JoupelFlow =
CALCULATE(
SUM(Joupel_In_Out[Total_Output_Flow]),
'Joupel_In_Out'[Flow_Pump_1] <> 0 ||
'Joupel_In_Out'[Flow_Pump_2] <> 0 ||
'Joupel_In_Out'[Flow_Pump_3] <> 0 ||
'Joupel_In_Out'[Flow_Pump_4] <> 0 ||
'Joupel_In_Out'[Flow_Pump_5] <> 0 ||
'Joupel_In_Out'[Flow_Pump_6] <> 0 ||
'Joupel_In_Out'[Flow_Pump_7] <> 0 ||
'Joupel_In_Out'[Flow_Pump_8] <> 0 ||
'Joupel_In_Out'[Flow_Pump_9] <> 0 ||
'Joupel_In_Out'[Flow_Pump_10] <> 0 ||
'Joupel_In_Out'[Flow_Pump_11] <> 0 ||
'Joupel_In_Out'[Flow_Pump_12] <> 0
)
VAR ShoaebaFlow =
CALCULATE(
SUM(Shoaeba_In_Out[Total_Output_Flow]),
'Shoaeba_In_Out'[Flow_Pump_1] <> 0 ||
'Shoaeba_In_Out'[Flow_Pump_2] <> 0 ||
'Shoaeba_In_Out'[Flow_Pump_3] <> 0 ||
'Shoaeba_In_Out'[Flow_Pump_4] <> 0 ||
'Shoaeba_In_Out'[Flow_Pump_5] <> 0 ||
'Shoaeba_In_Out'[Flow_Pump_6] <> 0
)
RETURN
DebaaFlow + JeddahFlow + JoupelFlow + ShoaebaFlow
```
## 3. Unmetered Consumption
This calculation is the inverse of metered consumption, summing the output flow where the pumps are off (equal to zero).
```UNMetered_Consumption =
VAR DebaaFlow =
CALCULATE(
SUM('Debaa_In_Out'[Total_Output_Flow]),
'Debaa_In_Out'[Flow_Pump_1] == 0 ||
'Debaa_In_Out'[Flow_Pump_2] == 0 ||
'Debaa_In_Out'[Flow_Pump_3] == 0 ||
'Debaa_In_Out'[Flow_Pump_4] == 0 ||
'Debaa_In_Out'[Flow_Pump_5] == 0 ||
use case: 3
'Debaa_In_Out'[Flow_Pump_6] == 0 ||
'Debaa_In_Out'[Flow_Pump_7] == 0 ||
'Debaa_In_Out'[Flow_Pump_8] == 0
)
VAR JeddahFlow =
CALCULATE(
SUM(Jeddah_In_Out[Total_Output_Flow]),
'Jeddah_In_Out'[Flow_Pump_1] == 0 ||
'Jeddah_In_Out'[Flow_Pump_2] == 0 ||
'Jeddah_In_Out'[Flow_Pump_3] == 0 ||
'Jeddah_In_Out'[Flow_Pump_4] == 0 ||
'Jeddah_In_Out'[Flow_Pump_5] == 0 ||
'Jeddah_In_Out'[Flow_Pump_6] == 0 ||
'Jeddah_In_Out'[Flow_Pump_7] == 0 ||
'Jeddah_In_Out'[Flow_Pump_8] == 0 ||
'Jeddah_In_Out'[Flow_Pump_9] == 0 ||
'Jeddah_In_Out'[Presure_Pump_10] == 0
)
VAR JoupelFlow =
CALCULATE(
SUM(Joupel_In_Out[Total_Output_Flow]),
'Joupel_In_Out'[Flow_Pump_1] == 0 ||
'Joupel_In_Out'[Flow_Pump_2] == 0 ||
'Joupel_In_Out'[Flow_Pump_3] == 0 ||
'Joupel_In_Out'[Flow_Pump_4] == 0 ||
'Joupel_In_Out'[Flow_Pump_5] == 0 ||
'Joupel_In_Out'[Flow_Pump_6] == 0 ||
'Joupel_In_Out'[Flow_Pump_7] == 0 ||
'Joupel_In_Out'[Flow_Pump_8] == 0 ||
'Joupel_In_Out'[Flow_Pump_9] == 0 ||
'Joupel_In_Out'[Flow_Pump_10] == 0 ||
'Joupel_In_Out'[Flow_Pump_11] == 0 ||
'Joupel_In_Out'[Flow_Pump_12] == 0
)
VAR ShoaebaFlow =
CALCULATE(
SUM(Shoaeba_In_Out[Total_Output_Flow]),
use case: 4
'Shoaeba_In_Out'[Flow_Pump_1] == 0 ||
'Shoaeba_In_Out'[Flow_Pump_2] == 0 ||
'Shoaeba_In_Out'[Flow_Pump_3] == 0 ||
'Shoaeba_In_Out'[Flow_Pump_4] == 0 ||
'Shoaeba_In_Out'[Flow_Pump_5] == 0 ||
'Shoaeba_In_Out'[Flow_Pump_6] == 0
)
RETURN
DebaaFlow + JeddahFlow + JoupelFlow + ShoaebaFlow
```
## 4. Unmetered Water Loss
The unmetered water loss is the difference between the total distributed water and the metered consumption.
``` Unmetered_Consumption = TOTAL_WATER_DISTRIBUTED - Metered_Consumption ```
## 5. Meter-Insensitive Water Volume
This calculation assumes that 10% of the unmetered water is due to meter insensitivity.
```
Meter_Insensitive_Water_Volume = 0.1 * Unmetered_Consumption
```
## 6. Water Theft
An estimate or actual value representing water theft. The user must replace the placeholder value with actual data.
```Water_Theft = 759000 -- Replace with the actual value```
## 7. Non-Revenue Water (NRW)
This formula calculates the total non-revenue water, combining commercial losses (e.g., meter insensitivity), water theft, and meter-insensitive volume.
```Non_Revenue_Water = Commercial_Loss + Water_Theft +
Meter_Insensitive_Water_Volume 
```
## 8. Physical Loss
This assumes 30% of the total water distributed is lost physically
```Physical_Loss = 0.3 * Total_Water_Distributed
Water_Leakage = 0.2 * Physical_Loss
```

