---
layout: page
title: "Electrical"
---

# Our Approach  
Our robot was powered in tandem by a rechargeable 12V lithium ion battery pack and a disposable 9V battery. The 12V was used for the realtively high current draw of 3 motors and 3 servos while the 9V battery was used to power a bluepill that controlled our robot.  

**TWO-TIER, ENDPOINT MODULE ELECTRICAL DESIGN PHILOSOPHY**
Our electrical was composed of multiple, small, distributed endpoint modules for individual functions placed closer to point of use. These modules can draw power and connect to:
1. The Power Board  
Powered by the 12V battery, the power board provides 12V, 5V, PWR_GND to end point modules that require energy to operate  
2. The Data Board
Powered by the 9V battery, the data board houses the bluepill and provides 5V, 3.3V, DATA_GND which allows for end point modules to connect to the logic of the robot

![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/elec_diagram_tobeupdated.PNG)
Figure 1. A mapping of the location of the boards on the robot

Benifits of this approach include:
- Separate sources of noise generation
- Easier to troubleshoot, modify, and enhance electrical system
- Modules can be designed and bench-tested individually
- Allows for common electronic devices (e.g., gate driver ICs) to be installed upstream on brainboard for shared use amongst endpoint modules
- Easier to recreate, troubleshoot, and deploy for 4 robots

# Boards
To execute our electrical approach we carefully designed and soldered 7 different boards. These were stratigicaly fastened onto the robot in locations suitable for their application. These include:  
1. Power Board
2. Data Board
3. Sensor Board
4. Delivery Servo Board
5. Motor Driver
6. Roller Driver + Slapper Servo
7. Start-up Button

![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/elec_map_2.PNG)
Figure 2. A mapping of the location of the boards on the robot

Our electronics system experinced multiple iterations as we were constantly learning new ways to improve our circuitry. These are our boards and the resulting lessons we learned about through their progression:

# 1. Power Board
Input: 12V, GND  
Output: 12V, 5V, PWR_GND  
Purpose: Expose power to boards containing servos, motors, and sensors
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/powerboard.jpg)
Figure 2. Power Board Progression

Initially we were using a 7805 Linear Voltage Regulator to provide a 5V source which would waste a lot of energy in the form of heat.
To optimize the production of our 5V power source we transitioned to a more efficient LM2596 Step Down Buck Converter

# 2. Data Board
Input: 9V, GND, Sensor Signals  
Output: 5V, 3.3V, DATA_GND, Motor/Servo/Sonar Output Signals  
Purpose: Control the function of the robot by reading inputs and executing various tasks based on the code
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/blue_pill_map.jpg)
Figure 3. Blue Pill Pinout

![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/databoard.jpg)
Figure 4. Data Board Progression

# 3. Sensor Board
Input: 5V, 3.3V, PWR_GND, DATA_GND  
Output: Sensor Signals  
Purpose: Relay information about the robots enviroment (ie location, can detection, etc) to the blue pill
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/sensorboard.jpg)
Figure 5. Sensor Board

**TODO**
Add an image of the data sheet of the IR sensors and explain the point of isolated GND for Data singals (elimates conductive noise from motors and servos from influences data through opto isolators)
**TODO**

# 4. Delivery Servo Board
Input: 12V, 5V, PWR_GND, DATA_GND (double check)  
Output: Servo Signals  
Purpose: Rotates the hopper and releases cans
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/servoboard.jpg)
Figure 6. Servo Board

**TODO**
Explain:
1. Use of opto isolators for noise reduction
2. Importance of buck converter since servos have high current draw
3. Add a video of the can delivery?
**TODO**


# 5. Motor Driver
Input: 12V, 5V, PWR_GND, DATA_GND (double check)  
Output: Motor Signals  
Purpose: Drive the motors, resulting in traversal of the course
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/motordriver.jpg)
Figure 7. Motor Driver Board

**TODO**
Add an image of the H-bridge circuit and explain that it allows for the motors to turn CW and CCW
**TODO**

# 6. Roller Driver + Slapper Servo
Input: 12V, 5V, PWR_GND, DATA_GND (double check)
Output: Motor Signal, Servo Signal
Purpose: Drive the rollers, slap in cans
![rs](https://raw.githubusercontent.com/seanghaeli/seanghaeli.github.io/master/assets/images/rollerdrive.jpg)
Figure 8. Motor Driver Board

**TODO**
Maybe explain the need for an H-bridge since the rollers can spit out a can?
**TODO**

# 7. Start-up Button
Input: (double check)
Output: Button Status
Purpose: Initiate Cometition Code

**TODO**
Add an image 
**TODO**

