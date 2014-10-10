<div class="row">
    <div class="col-md-9 col-md-offset-1">
        <img src="/images/sim.png" style="width:100%"/>
    </div>
</div>

##Overview
The diagram only displays heart rate, temperature and humidity information.  The table on the right, however, displays all of the characteristics and their values. 

A property value can be edited by clicking on a row of the table and entering the desired value in the text box.

##Scenarios
Scenarios 1, 2 and 3 will play back data recorded from a BioFit session.  Heart Rate, Respiration Rate, Systolic Blood Pressure, Diastolic Blood Pressure and Stress were all recorded at a rate of 1Hz for a human participant.  Other fields were not recorded, and are assigned static default initial values.

##Custom Data Modifications
To modify the data programatically, the ABCDEF buttons are linked to custom data modification functions in the code.  They can either modify data from the simulated data streams (i.e. increase each heart rate frame value by 20), or create entirely new data. The six functions contain example functionality, and can be modified as desired.

###Helpful features for modification
* Where to go: The top of <h5 style="display:inline; background-color:#FFF;">SeatData.m</h5> file in the simulator contains functions for simulations A through F.  It should be as easy as modify the functions and re-launch the simulator.
* <h5 style="display:inline; background-color:#FFF;">self->values.{property name}</h5> contains the current state of any property.
* <h5 style="display:inline; background-color:#FFF;">self.simulatorData</h5> - an array of all the frames of the currently loaded simulator file. Each frame is another array: [heart rate, stress, respiration rate, systolic blood pressure, diastolic blood pressure].  If a simulation has been loaded, this array can be modified.
* <h5 style="display:inline; background-color:#FFF;">ticker</h5> - A variable that will increment by one every time the simulator updates (every second).  It is reset every time a new simulation is loaded. Feel free to modify/reset it as desired - it does not have any impact outside of the data simulations.
