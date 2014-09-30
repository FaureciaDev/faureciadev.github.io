The Faurecia BioFit Seat is a [Bluetooth LE](http://www.bluetooth.com/Pages/low-energy-tech-info.aspx) peripheral.

All values are integers unless a decimal precision is shown in which
case it is fixed point (treat as integer and divide by 10 * number of
decimal places to convert to floating point). The numeric types in
order of preference are:

|Type | Value|
| :----- | :----------- |
| int8   | -128 .. 127 |
| uint8  | 0 .. 255 |
| int16  | -32768 .. 32767 |
| uint32 | elapsed time |

<br />
A group of characteristics can be requested to be notifiable by
writing the UUIDs of the desired characteristics to Notifiable Group.
This is the primary way of getting push data from the seat. The group
always includes Current Elapsed Time. Certain other characteristics
may also be independently notifiable, but doing that will lose the
benefit of the time stamp.

Characteristics marked with an asterisk are independently notifiable
with values sent once per second. Other attributes are only notified
when the value changes.

The writable characteristics use the same formats as the readable
characteristics (they often have the same UUID). Since the seat is a
physical system, there can be a significant time delay between writing
a value and the seat effecting the change. Do not poll the
characteristic watching for it to change: use the notify-only
characteristic Write Effect Complete.

The standard Bluetooth heart rate service is not planned to be used
since it focuses on data we don't have such as energy expended,
RR-interval, control points and body sensor location. It also does not
send time stamped values.

<hr />
##SPECIAL CHARACTERISTICS
<hr />

|  Property  | Description   | Value | 
| :---------------------- | :------------- | :-----| 
|Notifiable Group   			| A list of characteristics to notify at 1Hz 			|  [ID-1][ID-2]...[ID-N]
|Notifiable Group Values*   	| The packed values of the characteristics in the group	| [Current Elapsed Time][Value-1][Value-2]...[Value-N]


<hr />
##READABLE CHARACTERISTICS
<hr />

| ID&nbsp; |  Property  | Description   | Value | 
| :------------ | :------------- | :-----| | :-----| 
| 0 | Occupant Presence 			|  1 if seat is occupied, 0 if not 						| 0 or 1 |
| 1 | Heart Rate  					| Heart Rate Value in Beats / Minute 					| 0 .. 255 |
| 2 | Respiration Rate 				| Filtered Respiration Rate Value in Breaths / Minute 	| 0 .. 200 |
|   | Integrated Pulmonary Index 	| Score 												| 0 .. 100 |
|   | Heart Rate Variability 		| =LF/(LF+HF): Very Low Frequency (VLF) < 0.04 Hz Low Frequency (LF), 0.04 .. 0.14 Hz High Frequency (HF) 0.15 .. 0.40 Hz | 0.00 .. 1.00 |
| 3 | Blood Pressure (Systolic) 	| Value in mmHG (normal < 120, prehypertension 120 .. 139, hypertension 140 ..) | 0 .. 255 | 
| 4 | Blood Pressure (Diastolic) 	| Value in mmHG (normal < 80, prehypertension 80 .. 89, hypertension 90 ..) | 0 .. 255 |
|   | Blood Flow Index | Score 		| 0 .. 100 												| 
|   | Integrated Comfort Index 		| Score 												| 0 .. 100 | 
|   | Stress 						| 0 is very un-stressed, 100 is very stressed 			| 0 .. 100 |
|   | Emotional Valence 			| Score: aversiveness (fear) - attractiveness (joy) 	| 0 .. 100 | 
|   | Emotional Arousal 			| Score: weak - strong 									| 0 .. 100 | 
|   | Occupant Mass 				| Weight in Kilograms 									| 0 .. 500 |
|   | Occupant Center of Mass 		| XYZ Coordinates Relative to H-Point (mm) 				| (-500, -500, -500) .. (+500, +500, +500) | 
|   | Ambient Humidity 				| Percent Relative Humidity 							| 0 .. 100 |
|   | Cushion Surface Humidity 		| Percent Relative Humidity 							| 0 .. 100 |
|   | Upper Back Surface Humidity  	| Percent Relative Humidity 							| 0 .. 100 |
|   | Lower Back Surface Humidity 	| Percent Relative Humidity 							| 0 .. 100 |
|   | Cushion Surface Temperature	| Value in ⁰C                                           | 0 .. 85 |
|   | Back Surface Temperature 		| Value in ⁰C                                           | 0 .. 85 |
|   | Ambient Temperature 			| Value in ⁰C | 0 .. 85 |
|   | Lower Lumbar Pressure 		| % of Range. 0 is no pressure, 100 is maximum pressure. | 0 .. 100 |
|   | Middle Lumbar Pressure 		| % of Range. 0 is no pressure, 100 is maximum pressure. | 0 .. 100 |
|   | Upper Lumbar Pressure 		| % of Range. 0 is no pressure, 100 is maximum pressure. | 0 .. 100 |
|   | Cushion Side Bolster Pressure	| % of Range. 0 is no pressure, 100 is maximum pressure. | 0 .. 100 |
|   | Back Side Bolster Pressure	| % of Range. 0 is no pressure, 100 is maximum pressure. | 0 .. 100 |
|   | Cushion Edge Pressure 		| % of Range. 0 is no pressure, 100 is maximum pressure | 0 .. 100 |
|   | Cushion Length 				| Percent of Full Extension. 0 is minimum extension, 100 is maximum extension. | 0 .. 100 |
|   | Upper Backrest Position 		| Angle in Degrees | -20 .. +30 |
|   | Massage Program Selection		| 0 is off, 1-99 are pre-set programs | 0 .. 99
|   |Massage Intensity				| 1 is min intensity, 9 is max intensity |    1 .. 9
|   |Massage Speed					| 1 is min speed, 9 is max speed|    1 .. 9
|   |Ventilation Level				| 0 is off, 1 is min ventilation, 9 is max ventilation |    0 .. 9
|   |Back Heating and Cooling		| < 0 is cooling, 0 is off, > 0 is heating | -9 .. 9
|   |Cushion Heating and Cooling	| < 0 is cooling, 0 is off, > 0 is heating | -9 .. 9

<hr />
##NOTIFIABLE ONLY CHARACTERISTICS
<hr />

|  Property  | Value | 
| :---------------------- | :------------- | :-----| 
|Write Effect Complete  || [UUID][Value]


<hr />
##WRITEABLE CHARACTERISTICS
<hr />
|  Property  | Time to take effect  | 
| :---------------------- | :-----| 
|Massage Program Selection     |   0.2 s 
|Massage Intensity             |   0.2 s
|Massage Speed                 |   0.2 s
|Lower Lumbar Pressure         |   4.0 s
|Middle Lumbar Pressure        |   4.0 s
|Upper Lumbar Pressure         |   4.0 s
|Cushion Side Bolster Width    |   2.5 s
|Back Side Bolster Width       |   3.5 s
|Cushion Length                |   2.5 s
|Upper Backrest Position       |   3.0 s
|Ventilation Level             |   0.2 s
|Back Heating and Cooling      |   0.2 s
|Cushion Heating and Cooling   |   0.2 s