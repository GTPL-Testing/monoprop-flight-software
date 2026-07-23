README - ControlLoop Testing

Has been drastically simplified as of 4/11.

All you need to do now is navigate to the ControlLoop directory, run:

~/monoprop-flight-software/ControlLoop$ make

And then run

./data_mocker

Which will run the loop and fill up the output csv file.
Reading the CSV file remains the same, naviagte to /data_creators
and run:

~/monoprop-flight-software/ControlLoop/data_creators$ python3 plot_state.py

Make sure you are either in the virtual environment (dataEnv) or 
that you have plotly, numpy, and pandas on your system Python!

Note: To clean up .o files, please do:

~/monoprop-flight-software/ControlLoop$ make clean

Thanks!