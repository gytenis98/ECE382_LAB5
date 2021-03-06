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

Prelab questions:

Question 1: it should be arround 65.536 msec

Question 2: It should be around 1ms per count

Pictures of prelab table are includes. Also, collected data included too.

###Lab day 1 (Done)

Connecting the IR sensor

Insert the IR receiver module into the protoboard. Use M/F wires to connect your protoboard to your MSP430. Use a regular wire to connect your signal and ground to the logic analyzer.

When you are looking at the sensor ball on your IR receiver module, the pin on the left is your signal pin; the pin in the middle is your ground pin; and the pin on the right is your Vcc. 

On your MSP430, connect the signal pin to XIN/P2.6 on J2, the ground pin to the GND pin on J6, and the Vcc pin to Vcc on J6. 

Timer Counts

Build a project around test5.c and then download it onto your LaunchPad. Make sure to open the variables tab (View -> Variables). I also like to clear memory from the Memory Browser tab (View -> Memory Browser), Fill Memory from 0x200 to 0x400 with 0's. Run the program and then press a button on a remote. Then pause the program and look at the variables. You should see something like the following. 

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/arrayScreenShot.gif?raw=true "LCD")

Annotate the picture below to indicate which line of the for loop in the program is executed at which part of the pulse. You should show a total of 6 lines of code (lines 32-34 and lines 36-38). 

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/irWave.gif?raw=true "LCD")

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.02.57.jpg?raw=true "LCD")

IR data packets

Before you start on this portion of the assignment, watch Dave Jones' Trigger Hold-off Tutorial. You are going to need to use the O'scopes to examine the IR waveforms generated by a remote control of your choice. 

Setup your LaunchPad like the picture below. Make sure to connect the power and ground in the correct order! Connect the the O'scope on the Vout pin of the Vishay Remote Control Decoder. 

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/launchpadSetup.jpg?raw=true "LCD")

And my setup:

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-03%2009.15.22.jpg?raw=true "LCD")

Set the trigger threshold to mid voltage and the trigger hold-off to accommodate an IR packet. On my remote control, this was about 80ms. Please note that remote control data packets are not standardized by any means, so the remote that you use to perform these experiment will almost certainly generate different results than those that your neighbor's will generate.

List the lengths of the pulses generated by the remote control in absolute time using the O'scope (3 significant figures) and in timer A counts. Note: "start logic 0 half-pulse" refers to the logic LOW portion of the start pulse, and "data 0 logic 1 half pulse" refers to the second half (which is a logic HIGH) of the pulse representing a zero bit.

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.16.44.jpg?raw=true "LCD")
*data is attached with excel file.

Collect and tabulate in Excel 8 samples of timer A counts for each of the following pulse types (in decimal). Compute the average and standard deviation of each pulse type. I would suggest just grabbing it from the CCS variables tab.
- Data 1, logic 1 half-pulse - Data 0, logic 0 half-pulse - Data 0, logic 1 half-pulse 
 Ensure you label the rows and columns of your table so that I will know what the information in each cell means. For each pulse type list the range of timer A counts that would correctly classify 99.9999426697% of the pulses. This number has something to do with the standard deviation (hint: look at the table in this section). 
 Write the codes (in hex) for several remote control buttons. 


![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.16.37.jpg?raw=true "LCD")



![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/2014-11-04%2023.16.47.jpg?raw=true "LCD")

###Day 2 (Done)

Demonstrate to your instructor that your code can receive and decode button presses from the remote control. 

##Required Functionality (Done)

Watch the Dave Jones Trigger Hold-off video and achieve that functionality using both timer interrupts and a port 2 interrupt. Turn an LED on and off with one button on the remote. Turn another LED on and off with a different button.

The below image may be of some use:

![LCD](https://raw.githubusercontent.com/gytenis98/ECE382_LAB5/master/schematic.jpg?raw=true "LCD")

##A Functionality

Use the buttons on a remote control to either control your lab #4 etch-a-sketch (up, down, right, left, color) or your pong game.

##Testing/Debugging
I had some problems figuring out how to make my device listen to my remote. In particular, with the length of signals. I spent quite a few hours in the lab for the first day requirements. Later, i have problem to figure out how I should determine  the length of +/- of my signal. I used original 100 and it did not work. I found that 200 works by experimenting with it. 


###Documentation
Dr. Coulston helped me to debug my sintax mistakes. Dr. York help me to understand the structure of how I should build my program. Also, I discussed principals how to build the program with C2C Terragonli.
