---
layout: page
title: "Electrical"
---

Our robot was powered in tandem by a rechargeable 12V lithium ion battery pack and a disposable 9V battery. The 12V was used for the realtively high current draw of 3 motors and 3 servos while the 9V battery was used to power a bluepill that controlled our robot.

**TODO**
1. Clean up description for the general approach of our electronics below
2. Update a nice diagram for the overview of our circuits  

TWO-TIER ELECTRICAL DESIGN PHILOSOPHY
Bifurcation of electrical concerns into two high-level circuits: 
(a) power distribution unit (PDU)
(b) data processing unit (DPU).
Multiple, small, distributed endpoint modules for individual functions placed closer to point of use:
Separate sources of noise generation
Easier to troubleshoot, modify, and enhance electrical system
Modules can be designed and bench-tested individually
Allows for common electronic devices (e.g., gate driver ICs) to be installed upstream on brainboard for shared use amongst endpoint modules
Easier to recreate, troubleshoot, and deploy for 4 robots

ENDPOINT MODULE DESIGN PHILOSOPHY
Each endpoint module
Can draw power from any nominal power supply exposed on the brainboard
Can close (sub-)circuits to either power ground (12V supply) or data ground (STM32 Bluepill) in parallel
Is responsible for signal amplification and any endpoint-specific signal conditioning and that is not generalizable for other digital/analog signals

![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/elec_map_2.PNG)
Figure 1. A mapping of the location of the boards on the robot
or
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/elec_map_tobeupdated.PNG)
Figure 1. A mapping of the location of the boards on the robot
or
nice block diagram like Rudy made for design propsal

**TODO**

# Boards
Our electronics system experinced multiple iterations as we were constantly learning new ways to improve our circuitry.
These are our boards and the resulting lessons we learned about through their progression:

**1. Power Board**
Input: 12V, GND  
Output: 12V, 5V, PWR_GND  
Purpose: Expose power to boards containing servos, motors, and sensors
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/powerboard.jpg)
Figure 2. Power Board Progression

Initially we were using a 7805 Linear Voltage Regulator to provide a 5V source which would waste a lot of energy in the form of heat.
To optimize the production of our 5V power source we transitioned to a more efficient LM2596 Step Down Buck Converter

**2. Data Board**
Input: 9V, GND, Sensor Signals  
Output: 5V, 3.3V, DATA_GND, Motor/Servo/Sonar Output Signals  
Purpose: Control the function of the robot by reading inputs and executing various tasks based on the code
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/blue_pill_map.jpg)
Figure 3. Blue Pill Pinout

![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/databoard.jpg)
Figure 4. Data Board Progression

**3. Sensor Board**
Input: 5V, 3.3V, PWR_GND, DATA_GND  
Output: Sensor Signals  
Purpose: Relay information about the robots enviroment (ie location, can detection, etc) to the blue pill
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/sensorboard.jpg)
Figure 5. Sensor Board

**TODO**
Add an image of the data sheet of the IR sensors and explain the point of isolated GND for Data singals (elimates conductive noise from motors and servos from influences data through opto isolators)
**TODO**

**4. Servo Board**
Input: 12V, 5V, PWR_GND, DATA_GND (double check)  
Output: Servo Signals  
Purpose: Rotates the hopper and releases cans
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/servoboard.jpg)
Figure 6. Servo Board

**TODO**
Explain:
1. Use of opto isolators for noise reduction
2. Importance of buck converter since servos have high current draw
**TODO**


**5. Motor Driver**
Input: 12V, 5V, PWR_GND, DATA_GND (double check)  
Output: Motor Signals  
Purpose: Drive the motors, resulting in traversal of the course
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/motordriver.jpg)
Figure 7. Motor Driver Board

**TODO**
Add an image of the H-bridge circuit and explain that it allows for the motors to turn CW and CCW
**TODO**

**6. Roller Driver + Slapper Servo**
Input: 12V, 5V, PWR_GND, DATA_GND (double check)
Output: Motor Signal, Servo Signal
Purpose: Drive the rollers, slap in cans
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/rollerdrive.jpg)
Figure 8. Motor Driver Board

**TODO**
Maybe explain the need for an H-bridge since the rollers can spit out a can?
**TODO**

**7. Start Buttonr**
Input: (double check)
Output: Button Status
Purpose: Initiate Cometition Code

**TODO**
Add an image 
**TODO**

