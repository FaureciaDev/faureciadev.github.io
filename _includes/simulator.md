<div class="row">
    <div class="col-md-9 col-md-offset-1">
        <img src="/images/Simulator.png" style="width:100%"/>
    </div>
</div>

The diagram only displays heart rate, temperature and humidity information.  The table on the right, however, displays all of the characteristics and their values. Values can be edited by clicking on a row and entering the desired value in the text box.

Scenarios 1, 2 and 3 will play back data recorded from a BioFit session.  Heart Rate, Respiration Rate, Systolic Blood Pressure, Diastolic Blood Pressure and Stress were all recorded at a rate of 1Hz for a human participant.  Other fields were not recorded, and are assigned static default initial values.

To modify the data for various scenarios, the ABCDEF buttons are linked to custom data modification functions in the code.

Helpful features for modification
 - the values struct: contains the current state of all the values
 - the *find out real name* simulated data array - contains an array of heart rate, respiration rate, systolic blood pressure, diastolic blood pressure and stress for each state.  If a similuator is running, this array can be modified.
 - "ticker". This is reset every time a new simulation is loaded.  Every time the simulator updates (every second), it will increment by one.  It can be used to apply a modification for a certain amount of time.
