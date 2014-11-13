ECE382_LAB5
===========
# Lab 5 - Interrupts - "Remote Control Decoding"




Objectives

In this lab, you'll use your knowledge of interrupts and the Timer_A subsytem to reverse engineer a remote control. 

Details

The Basic Idea

You will need to use the timer interrupt and the general purpose pin interrupt to decode a remote control. Be sure to pick one remote for the whole lab, as remote codes vary. 

Lab day 1: learn the timing and bit patterns for your remote control

Lab day 2: demonstrate your code can receive and decode button presses from the remote control

Lab day 3: implement etch-a-sketch or pong

Prelab:

Question 1: it should be arround 65.536 msec

Question 2: It should be around 1ms per count

Pictures of prelab table are includes. Also, collected data included too.

###Lab day 1

Connecting the IR sensor

Insert the IR receiver module into the protoboard. Use M/F wires to connect your protoboard to your MSP430. Use a regular wire to connect your signal and ground to the logic analyzer.

When you are looking at the sensor ball on your IR receiver module, the pin on the left is your signal pin; the pin in the middle is your ground pin; and the pin on the right is your Vcc. 

On your MSP430, connect the signal pin to XIN/P2.6 on J2, the ground pin to the GND pin on J6, and the Vcc pin to Vcc on J6. 

Timer Counts

Build a project around test5.c and then download it onto your LaunchPad. Make sure to open the variables tab (View -> Variables). I also like to clear memory from the Memory Browser tab (View -> Memory Browser), Fill Memory from 0x200 to 0x400 with 0's. Run the program and then press a button on a remote. Then pause the program and look at the variables. You should see something like the following. 

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.02.57.jpg?raw=true "LCD")


![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.02.57.jpg?raw=true "LCD")

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.16.37.jpg?raw=true "LCD")

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.16.44.jpg?raw=true "LCD")

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.16.47.jpg?raw=true "LCD")

