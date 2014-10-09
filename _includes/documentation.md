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
##BioFit Characteristics

| ID&nbsp; |  Property  | 
| :--:  | :---------------------- | 
| 0  | <a href="#occupantPresence" name="occupantPresenceTable">Occupant Presence</a>
| 1  | <a href="#systemTimeStamp" name="systemTimeStampTable">System Time Stamp</a> 
| 2  | <a href="#connectionReferenceTime" name="connectionReferenceTimeTable">Connection Reference Time</a> 
| 3  | <a href="#currentElapsedTime" name="currentElapsedTimeTable">Current Elapsed Time</a> 
| 4  | <a href="#notifiableGroup" name="notifiableGroupTable">Notifiable Group</a> | 
| 5  | <a href="#notifiableGroupValues" name="notifiableGroupValuesTable">Notifiable Group Values*</a> 
| 6  | <a href="#writeEffectComplete" name="writeEffectCompleteTable">Write Effect Complete*</a> 
| 7  | <a href="#heartRate" name="heartRateTable">Heart Rate</a>
| 8  | <a href="#respirationRate" name="respirationRateTable">Respiration Rate</a>
| 9  | <a href="#integratedPulmonaryIndex" name="integratedPulmonaryIndexTable">Integrated Pulmonary Index</a>
| 10 | <a href="#heartRateVariability" name="heartRateVariabilityTable">Heart Rate Variability</a>
| 11 | <a href="#bloodPressureSystolic" name="bloodPressureSystolicTable">Blood Pressure (Systolic)</a>
| 12 | <a href="#bloodPressureDiastolic" name="bloodPressureDiastolicTable">Blood Pressure (Diastolic)</a>
| 13 | <a href="#bloodFlowIndex" name="bloodFlowIndexTable">Blood Flow Index</a> 
| 14 | <a href="#integratedComfortIndex" name="integratedComfortIndexTable">Integrated Comfort Index</a>
| 15 | <a href="#stress" name="stressTable">Stress</a>
| 16 | <a href="#emotionalValence" name="emotionalValenceTable">Emotional Valence</a>
| 17 | <a href="#emotionalArousal" name="emotionalArousalTable">Emotional Arousal</a>
| 18 | <a href="#occupantMass" name="occupantMassTable">Occupant Mass</a>
| 19 | <a href="#occupantCenterOfMass" name="occupantCenterOfMassTable">Occupant Center of Mass</a>
| 20 | <a href="#ambientHumidity" name="ambientHumidityTable">Ambient Humidity</a>
| 21 | <a href="#cushionSurfaceHumidity" name="cushionSurfaceHumidityTable">Cushion Surface Humidity</a>
| 22 | <a href="#upperBackSurfaceHumidity" name="upperBackSurfaceHumidityTable">Upper Back Surface Humidity</a>
| 23 | <a href="#lowerBackSurfaceHumidity" name="lowerBackSurfaceHumidityTable">Lower Back Surface Humidity</a>
| 24 | <a href="#cushionSurfaceTemperature" name="cushionSurfaceTemperatureTable">Cushion Surface Temperature</a>
| 25 | <a href="#backSurfaceTemperature" name="backSurfaceTemperatureTable">Back Surface Temperature</a>
| 26 | <a href="#ambientTemperature" name="ambientTemperatureTable">Ambient Temperature</a>
| 27 | <a href="#lowerLumbarPressure" name="lowerLumbarPressureTable">Lower Lumbar Pressure</a>
| 28 | <a href="#middleLumbarPressure" name="middleLumbarPressureTable">Middle Lumbar Pressure</a>
| 29 | <a href="#upperLumbarPressure" name="upperLumbarPressureTable">Upper Lumbar Pressure</a>
| 30 | <a href="#cushionSideBolsterPressure" name="cushionSideBolsterPressureTable">Cushion Side Bolster Pressure</a>
| 31 | <a href="#backSideBolsterPressure" name="backSideBolsterPressureTable">Back Side Bolster Pressure</a>
| 32 | <a href="#cushionLength" name="cushionLengthTable">Cushion Length</a>
| 33 | <a href="#cushionEdgePressure" name="cushionEdgePressureTable">Cushion Edge Pressure</a>    
| 34 | <a href="#upperBackrestPosition" name="upperBackrestPositionTable">Upper Backrest Position</a>
| 35 | <a href="#massageProgramSelection" name="massageProgramSelectionTable">Massage Program Selection</a>
| 36 | <a href="#massageIntensity" name="massageIntensityTable">Massage Intensity</a>
| 37 | <a href="#massageSpeed" name="massageSpeedTable">Massage Speed</a>
| 38 | <a href="#ventilationLevel" name="ventilationLevelTable">Ventilation Level</a>
| 39 | <a href="#backHeatingAndCooling" name="backHeatingAndCoolingTable">Back Heating and Cooling</a>
| 40 | <a href="#cushionHeatingAndCooling" name="cushionHeatingAndCoolingTable">Cushion Heating and Cooling</a>

<hr />

#Property Characteristic Details

##<a name="occupantPresence">Occupant Presence</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>0
    </td><td>
        <h4>UUID</h4>B43EED9C-E88E-42FF-AB8C-4399977C3D9D
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 or 1 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
  1 if seat is occupied, 0 if not 
<h6 style="padding-top:5px"><a href="#occupantPresenceTable">back to table</a></h6>
</div>
<hr />

##<a name="systemTimeStamp">System Time Stamp</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>1  
    </td><td>
        <h4>UUID</h4>71BFAE4D-51CD-422D-AE87-B4921AC75C1
    </td><td>
       <h4>Type</h4> uint32
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4>
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Seat Timestamp</h4>
<h6 style="padding-top:5px"><a href="#systemTimeStampTable">back to table</a></h6>
</div>
<hr />

##<a name="connectionReferenceTime">Connection Reference Time</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>2  
    </td><td>
        <h4>UUID</h4> 21752B03-3735-473E-903F-485CF77DA0AE
    </td><td>
       <h4>Type</h4> uint32
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4>
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>connection reference time</h4>
<h6 style="padding-top:5px"><a href="#connectionReferenceTimeTable">back to table</a></h6>
</div>
<hr />

##<a name="currentElapsedTime">Current Elapsed Time</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>3  
    </td><td>
        <h4>UUID</h4>0A347E6C-02E4-4749-A8A4-6BD6202E8FEA
    </td><td>
       <h4>Type</h4> uint32
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4>
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>current elapsed time</h4>
<h6 style="padding-top:5px"><a href="#currentElapsedTimeTable">back to table</a></h6>
</div>
<hr />

##<a name="notifiableGroup">Notifiable Group</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>4  
    </td><td>
        <h4>UUID</h4>B4A265CD-2786-432D-8E92-819B9113AA10
    </td><td>
       <h4>Type</h4> uint8 for each element in array 
   </td><td>
       <h4>Bluetooth Properties</h4>Readable, Writeable 
   </td><td>
       <h4>Values</h4> [int8 ID-1][int8 ID-2]...[int8 ID-N]
</td></tr></table>

<span style="padding-top:5px"></span>
<h4>Description</h4>
A list of characteristics to notify at 1Hz. Notifications will occur on the <a href="#notifiableGroupValues">notifiable group values</a> characteristic.
<h6 style="padding-top:5px"><a href="#notifiableGroupTable">back to table</a></h6>
</div>
<hr />

##<a name="notifiableGroupValues">Notifiable Group Values</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>5  
    </td><td>
        <h4>UUID</h4>5957BE8F-C01F-4531-A529-0924398E4FE9
    </td><td>
       <h4>Type</h4> Array of individually typed values <br />[uint32, [type-1][type-2]...[type-n]]
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Notifiable 
   </td><td>
       <h4>Values</h4> [Current Elapsed Time][Value-1][Value-2]...[Value-N]
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
The packed values of the characteristics in the group. Values to notify determined by the <a href="#notifiableGroup">notifiable group</a> characteristic. Limited to a total length of 20 bytes. The first item will always be the time at which the requested values were read.
<h6 style="padding-top:5px"><a href="#notifiableGroupValuesTable">back to table</a></h6>
</div>
<hr />

##<a name="writeEffectComplete">Write Effect Complete</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>6  
    </td><td>
        <h4>UUID</h4>F56A209B-2285-44E5-862F-1AB206DFFBE6
    </td><td>
       <h4>Type</h4> uint8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Notifiable 
   </td><td>
       <h4>Values</h4> [id] (0 ..40)
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
Contains the id of a property. Notifies when the request that was written is complete.
<h6 style="padding-top:5px"><a href="#writeEffectCompleteTable">back to table</a></h6>
</div>
<hr />

##<a name="heartRate">Heart Rate</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4> 7  
    </td><td>
        <h4>UUID</h4>39D1E3AE-EA25-43BD-BB62-ADD8ECD897D5
    </td><td>
       <h4>Type</h4> uint8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 255 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Heart Rate Value in Beats / Minute 
<h6 style="padding-top:5px"><a href="#heartRateTable">back to table</a></h6>
</div>
<hr />

##<a name="respirationRate">Respiration Rate </a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>8  
    </td><td>
        <h4>UUID</h4>D5F34109-9F28-4213-85A4-808357CEF8F3
    </td><td>
       <h4>Type</h4> uint8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 200 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Filtered Respiration Rate Value in Breaths / Minute 
<h6 style="padding-top:5px"><a href="#respirationRateTable">back to table</a></h6>
</div>
<hr />

##<a name="integratedPulmonaryIndex">Integrated Pulmonary Index</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>9  
    </td><td>
        <h4>UUID</h4>8217E89D-C226-45F6-A36E-DA23DDE4A83A
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
An integrated score that describes an occupant’s respiratory status (normal = 10, less than 6 may indicate intervention required)
<h6 style="padding-top:5px"><a href="#integratedPulmonaryIndexTable">back to table</a></h6>
</div>
<hr />

##<a name="heartRateVariability">Heart Rate Variability</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>10 
    </td><td>
        <h4>UUID</h4>00CFF3E3-A2FF-4E05-8EFA-C22D799EB136
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0.00 .. 1.00 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 =LF/(LF+HF): Very Low Frequency (VLF) &lt; 0.04 Hz Low Frequency (LF), 0.04 .. 0.14 Hz High Frequency (HF) 0.15 .. 0.40 Hz 
<h6 style="padding-top:5px"><a href="#heartRateVariabilityTable">back to table</a></h6>
</div>
<hr />

##<a name="bloodPressureSystolic">Blood Pressure (Systolic)</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>11 
    </td><td>
        <h4>UUID</h4>D9A9F3E2-E884-40F4-91D6-41892C2D2E73
    </td><td>
       <h4>Type</h4> uint8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 255 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Value in mmHG (normal &lt; 120, prehypertension 120 .. 139, hypertension 140 ..) 
<h6 style="padding-top:5px"><a href="#bloodPressureSystolicTable">back to table</a></h6>
</div>
<hr />

##<a name="bloodPressureDiastolic">Blood Pressure (Diastolic)</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>12 
    </td><td>
        <h4>UUID</h4>0038087B-31E2-4D67-8106-A4996E329EE2
    </td><td>
       <h4>Type</h4> uint8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 255 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Value in mmHG (normal < 80, prehypertension 80 .. 89, hypertension 90 ..) 
<h6 style="padding-top:5px"><a href="#bloodPressureDiastolicTable">back to table</a></h6>
</div>
<hr />

##<a name="bloodFlowIndex">Blood Flow Index</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>13 
    </td><td>
        <h4>UUID</h4>65CF8D40-8943-473A-8DC9-400F5A17A6C7
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
An integrated score that estimates an individual’s blood flow relative to ideal:  ideal blood flow = 100, poor blood flow = 0
<h6 style="padding-top:5px"><a href="#bloodFlowIndexTable">back to table</a></h6>
</div>
<hr />

##<a name="integratedComfortIndex">Integrated Comfort Index</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>14 
    </td><td>
        <h4>UUID</h4>48560C7A-F383-4C27-BE20-E92C416C8F80
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
An integrated score that estimates an individual’s level of comfort:  extreme comfort = 100, extreme discomfort = 0
<h6 style="padding-top:5px"><a href="#integratedComfortIndexTable">back to table</a></h6>
</div>
<hr />

##<a name="stress">Stress</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>15 
    </td><td>
        <h4>UUID</h4>96A70770-C16F-40CC-BB4D-768E0F02494E
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 0 is very un-stressed, 100 is very stressed 
<h6 style="padding-top:5px"><a href="#stressTable">back to table</a></h6>
</div>
<hr />

##<a name="emotionalValence">Emotional Valence</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>16 
    </td><td>
        <h4>UUID</h4>C2D2F281-7756-47A7-9B14-C9BAC900354F
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 An estimate of emotional positivity or negativity: negative = 0, neutral = 50, positive = 100
<h6 style="padding-top:5px"><a href="#emotionalValenceTable">back to table</a></h6>
</div>
<hr />

##<a name="emotionalArousal">Emotional Arousal</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>17 
    </td><td>
        <h4>UUID</h4>3B7E5227-2926-4E15-9FE6-E4CD273371B2
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 An estimate of how strong someone’s emotion is: calm = 0, excited = 100 
<h6 style="padding-top:5px"><a href="#emotionalArousalTable">back to table</a></h6>
</div>
<hr />

##<a name="occupantMass">Occupant Mass</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>18 
    </td><td>
        <h4>UUID</h4>E76B29AC-FD59-4530-898B-35AB751A43C8
    </td><td>
       <h4>Type</h4> int16
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 500 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Weight in Kilograms 
<h6 style="padding-top:5px"><a href="#occupantMassTable">back to table</a></h6>
</div>
<hr />

##<a name="occupantCenterOfMass">Occupant Center of Mass</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>19 
    </td><td>
        <h4>UUID</h4>B11102CC-5235-44BE-B8E8-825DFF3B90FD
    </td><td>
       <h4>Type</h4> [int16, int16, int16]
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> (-500, -500, -500) .. (500, 500, 500) 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 XYZ Coordinates Relative to H-Point (mm) 
<h6 style="padding-top:5px"><a href="#occupantCenterOfMassTable">back to table</a></h6>
</div>
<hr />

##<a name="ambientHumidity">Ambient Humidity</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>20 
    </td><td>
        <h4>UUID</h4>2B46CF2F-C102-4683-8F05-9E6AD5A84843
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Percent Relative Humidity
<h6 style="padding-top:5px"><a href="#ambientHumidityTable">back to table</a></h6>
</div>
<hr />

##<a name="cushionSurfaceHumidity">Cushion Surface Humidity</a>
<div class="content-box">
<table><tr><td>
    <h4>ID</h4>21 
    </td><td>
        <h4>UUID</h4>4612CD0D-64F0-4140-9EB5-198B770FC0D0
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Percent Relative Humidity 
<h6 style="padding-top:5px"><a href="#cushionSurfaceHumidityTable">back to table</a></h6>
</div>
<hr />

##<a name="upperBackSurfaceHumidity">Upper Back Surface Humidity</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>22 
    </td><td>
        <h4>UUID</h4>53603F65-6B4B-4D46-B373-B486B78590D2
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Percent Relative Humidity 
<h6 style="padding-top:5px"><a href="#upperBackSurfaceHumidityTable">back to table</a></h6>
</div>
<hr />

##<a name="lowerBackSurfaceHumidity">Lower Back Surface Humidity</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>23 
    </td><td>
        <h4>UUID</h4>7E3DF6AE-41C7-493E-8D4D-556A62321A9B
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Percent Relative Humidity 
<h6 style="padding-top:5px"><a href="#lowerBackSurfaceHumidityTable">back to table</a></h6>
</div>
<hr />

##<a name="cushionSurfaceTemperature">Cushion Surface Temperature</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>24 
    </td><td>
        <h4>UUID</h4>75A8A1EF-B8E0-4FB4-A867-B68E653DF932
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 85 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Value in ⁰C                                           
<h6 style="padding-top:5px"><a href="#cushionSurfaceTemperatureTable">back to table</a></h6>
</div>
<hr />

##<a name="backSurfaceTemperature">Back Surface Temperature</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>25
    </td><td>
        <h4>UUID</h4>2CD29B7B-22D5-4371-89FF-E849E2120929
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 85 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Value in ⁰C                                           
<h6 style="padding-top:5px"><a href="#backSurfaceTemperatureTable">back to table</a></h6>
</div>
<hr />

##<a name="ambientTemperature">Ambient Temperature</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>26
    </td><td>
        <h4>UUID</h4>45DEFC80-B2FC-49A4-A97D-A68FFDEFF8C2
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4> 0 .. 85 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Value in ⁰C 
<h6 style="padding-top:5px"><a href="#ambientTemperatureTable">back to table</a></h6>
</div>
<hr />

##<a name="lowerLumbarPressure">Lower Lumbar Pressure</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>27
    </td><td>
        <h4>UUID</h4>1BA22BC7-28AB-4B25-A0EE-4553C4C28DC2
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 % of Range. 0 is no pressure, 100 is maximum pressure. 
<h6 style="padding-top:5px"><a href="#lowerLumbarPressureTable">back to table</a></h6>
</div>
<hr />

##<a name="middleLumbarPressure">Middle Lumbar Pressure</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>28
    </td><td>
        <h4>UUID</h4>636235DE-D04C-42DD-8673-F11918D7C5BD
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 % of Range. 0 is no pressure, 100 is maximum pressure. 
<h6 style="padding-top:5px"><a href="#middleLumbarPressureTable">back to table</a></h6>
</div>
<hr />

##<a name="upperLumbarPressure">Upper Lumbar Pressure</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>29
    </td><td>
        <h4>UUID</h4>E430BAFB-B101-4896-9957-6E3938F575D8
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 % of Range. 0 is no pressure, 100 is maximum pressure. 
<h6 style="padding-top:5px"><a href="#upperLumbarPressureTable">back to table</a></h6>
</div>
<hr />

##<a name="cushionSideBolsterPressure">Cushion Side Bolster Pressure</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>30
    </td><td>
        <h4>UUID</h4>434A3872-2DE3-4E76-A120-30A179286D28
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 % of Range. 0 is no pressure, 100 is maximum pressure. 
<h6 style="padding-top:5px"><a href="#cushionSideBolsterPressureTable">back to table</a></h6>
</div>
<hr />

##<a name="backSideBolsterPressure">Back Side Bolster Pressure</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>31
    </td><td>
        <h4>UUID</h4>984CB911-02F5-4941-9A1D-AD09A5764F15
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 % of Range. 0 is no pressure, 100 is maximum pressure. 
<h6 style="padding-top:5px"><a href="#backSideBolsterPressureTable">back to table</a></h6>
</div>
<hr />

##<a name="cushionLength">Cushion Length</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>32
    </td><td>
        <h4>UUID</h4>65A45C5D-9B54-4488-ABD2-1853D11E7F54
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Percent of Full Extension. 0 is minimum extension, 100 is maximum extension. 
<h6 style="padding-top:5px"><a href="#cushionLengthTable">back to table</a></h6>
</div>
<hr />

##<a name="cushionEdgePressure">Cushion Edge Pressure</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>33
    </td><td>
        <h4>UUID</h4>7949ABDC-965E-4175-ACF1-B842848C6AD5
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 0 .. 100 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 % of Range. 0 is no pressure, 100 is maximum pressure 
<h6 style="padding-top:5px"><a href="#cushionEdgePressureTable">back to table</a></h6>
</div>
<hr />

##<a name="upperBackrestPosition">Upper Backrest Position</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>34
    </td><td>
        <h4>UUID</h4>EC7D0CB9-34D4-423C-AAAC-CFF722E3A6C5
    </td><td>
        <h4>UUID</h4>EC7D0CB9-34D4-423C-AAAC-CFF722E3A6C5
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> -20 .. +30 
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Angle in Degrees 
<h6 style="padding-top:5px"><a href="#upperBackrestPositionTable">back to table</a></h6>
</div>
<hr />

##<a name="massageProgramSelection">Massage Program Selection</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>35
    </td><td>
        <h4>UUID</h4>E66E4070-831B-4E23-B05E-D7BE5F06AF4B
    </td><td>
       <h4>Type</h4> uint8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 0 .. 99
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 0 is off, 1-99 are pre-set programs 
<h6 style="padding-top:5px"><a href="#massageProgramSelectionTable">back to table</a></h6>
</div>
<hr />

##<a name="massageIntensity">Massage Intensity</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>36
    </td><td>
        <h4>UUID</h4>165F7489-A805-4D70-8900-135A4E174404
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 1 .. 9
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 1 is min intensity, 9 is max intensity 
<h6 style="padding-top:5px"><a href="#massageIntensityTable">back to table</a></h6>
</div>
<hr />

##<a name="massageSpeed">Massage Speed</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>37
    </td><td>
        <h4>UUID</h4>C4248837-F351-4538-9A73-8480637F3841
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 1 .. 9
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 1 is min speed, 9 is max speed
<h6 style="padding-top:5px"><a href="#massageSpeedTable">back to table</a></h6>
</div>
<hr />

##<a name="ventilationLevel">Ventilation Level</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>38
    </td><td>
        <h4>UUID</h4>25BFE8A4-786D-458D-A4AD-F710D4E7EFC6
    </td><td>
       <h4>Type</h4> uint8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> 1 .. 9
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 0 is off, 1 is min ventilation, 9 is max ventilation 
<h6 style="padding-top:5px"><a href="#ventilationLevelTable">back to table</a></h6>
</div>
<hr />

##<a name="backHeatingAndCooling">Back Heating and Cooling</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>39
    </td><td>
        <h4>UUID</h4>C391FFC3-BD58-4BB4-AC90-08A96BF04E39
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4>-9 .. 9
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Less than 0 is cooling, 0 is off, greater than 0 is heating.  A higher magnitude represents a higher magnitude temperature.
<h6 style="padding-top:5px"><a href="#backHeatingAndCoolingTable">back to table</a></h6>
</div>
<hr />

##<a name="cushionHeatingAndCooling">Cushion Heating and Cooling</a>
<div class="content-box">
<table><tr><td>
        <h4>ID</h4>40
    </td><td>
        <h4>UUID</h4>B3AB6D33-3E6A-42B3-B1BD-D821FFBE3090
    </td><td>
       <h4>Type</h4> int8
   </td><td>
       <h4>Bluetooth Properties</h4> Readable, Writeable
   </td><td>
       <h4>Values</h4> -9 .. 9
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
 Less than 0 is cooling, 0 is off, greater than 0 is heating. A higher magnitude represents a higher magnitude temperature.
<h6 style="padding-top:5px"><a href="#cushionHeatingAndCoolingTable">back to table</a></h6>
</div>
<hr /> 

<!-- blank template
##<a name=""></a>
<div class="content-box">
<table><tr><td>
        <h4>UUID</h4> ########-####-####-####-############
    </td><td>
       <h4>Type</h4>
   </td><td>
       <h4>Bluetooth Properties</h4> Readable
   </td><td>
       <h4>Values</h4>
</td></tr></table>
<br />
<span style="padding-top:5px"></span>
<h4>Description</h4>
<h6 style="padding-top:5px"><a href="#">back to table</a></h6>
</div>
<hr />
end of template -->