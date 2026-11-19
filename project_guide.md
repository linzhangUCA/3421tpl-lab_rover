# Lab Rover
> [!IMPORTANT]
> ## $\color{#582c83}\text{Demonstration Due: Thursday, Dec. 10th @ 1 PM}$
> ## $\color{#582c83}\text{Submission Due: Thursday, Dec. 10th @ 5 PM}$

## 1. Background Story

On the surface of the planet LEDG-100n, our brave rover TBot has successfully secured a volatile sample of "Element M2-5", a crucial resource to build planetary engines.
Now begins the perilous return journey to the Base Station, a navigation challenge that would fry the circuits of lesser bots.
TBot must traverse the extraterrestrial terrain, relying on its sensors to differentiate between solid ground and deceptively steep cliffs.
The good news is, on the way to the sampling site, TBot memorized the surrounding environment and made a map.
TBot shared this information to its trustworthy human partner, you, and is waiting on a reliable plan to start the journey back home.


## 2. Autonomous Navigation Demonstration

### 2.1. Procedure
1. Initialization and self-check.
2. Receive the payload ("Element M2-5", a.k.a. **M2.5 nut**)
3. Set robot behind the "Start Line" at any location and heading angle.
4. Let the robot autonomously navigate towards the destination.
5. $\color{purple}\text{Terminate}$ the navigation when the robot thinks it is done.

> [!IMPORTANT]
> ### 2.2. Rules (Bonus/Penalty)
> - Each student can attempt up to 3 times in total.
>   The student with fewer attempts has higher priority in the queque.
> - A navigation trial will be considered as successful if the robot terminate inside of the "Home Base" as shown in the map below.
> - Entering the "Danger Zones" will lead to disqualification of the attempt.
>   The location where the robot enters the "Danger Zone" will be counted as the end of navigation location.
> - Human intervention after the robot crossed over the "Start Line" will disqualify the current attempt.
>   The location where the human physically contact the robot will be counted as the end of navigation location.
> - (**25% Bonus**)The robot needs to navigate to the deeper portion of the "Home Base" to claim a 25% **bonus** points.
> - (**Up to %40 Penalty**) If the robot failed to finish the navigation in the "Home Base", the distance, $d$ (in meters), will be measured between the navigation ending location and the nearest point on the entry line of the "Home Base".
>   $max(-40, -10d)$% points will be taken as the penalty.
> - Only the highest scored trial will be kept.  
> - The robot traveling in-between the "Rails" can claim a 5% bonus points.
>   At least one wheel needs to on the track.
> - Only encoders and the DC motors are required, students have the freedom to employ other sensors and actuators.

Reference map for the navigation:
![lab_nav](./assets/images/lab_nav.png)


## 3. Requirements
> [!CAUTION]
> - A live demonstration is required to redeem the points below.

### 3.1. Mechanical Design & Implementation (15% Base)
- (3%) Assemble your robot and upload a portrait picture (you pick the viewing angle) for your robot.
  Try to reveal as many key components as possible.
- (12%) Use _Top View_, _Side View_ and _Front View_ drawings to illustrate:
  - Dimensions of the key components (base, wheels, circuit boards, **payload storage**, etc.).
  - Locations and layout of of the key components.

### 3.2. Electrical Design & Practice (10% Base + Bonus)
Wire up all the electrical and electronics components.
- (10%) Upload schematic(s) of wiring diagram depicting the power distribution and the signal networking.
- (**5% Bonus**) Self-Soldered PCB of TBot control relay.

#### 3.3. Algorithm (10% Base + Bonus)
- (10%) Describe the logic of the navigation using an [itemized list]((https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#lists)), or a [algorithm table](https://i.sstatic.net/6hfCG.png), or a [flowchart](https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/LampFlowchart.svg/960px-LampFlowchart.svg.png).
- (**10% Bonus**) Fuse the IMU measurement with the encoders'. Explain your sensor fusion approach with math language. 

### 3.4. Coding (50% Base + Bonus)
#### 3.4.1. (10%) Initialization (System Check).
   - (3%) On power-up, verify sensors are functional.
     - Button GPIO pin reads its configured default resting logic level (0 for PULL_DOWN, 1 for PULL_UP)
     - Ultrasonic sensor (if applied) returns a non-zero, valid distance reading.
     - IMU (if applied) returns non-zero, reasonable motion data.
   - (7%) Verify actuators are functional.
     - Spin mobile base exactly 90 degrees CCW or CW in place, then spin it back (to also verify the encoders are functional)
     - Spin servo (if applied) exactly 90 degrees CCW or CW, then spin it back.
   - If all of the above conditions are met, blink all status LEDs simultaneously at 5 Hz for 2 seconds.
   - Automatically transition into `PAUSE` mode upon successful self-test completion.
 > [!IMPORTANT]
 > If any initialization check fails, the robot **must not** proceed to active navigation.

#### 3.4.2. (3%) When `PAUSE` mode is activated:
  - (1%) Stop all actuators.
  - (1%) Modulate the $\color{green}\text{green}$ LED with a breathing/fading effect at 1 Hz (allocating equal duration to fade-in and fade-out cycles).
  - (1%) Switch to `WORK` mode at the moment the tactile button is **released**.

#### 3.4.3. (32%) When `WORK` mode is activated:
  - (1%) Solid $\color{green}\text{green}$ LED continuously lit.
  - (30%) Calculate reasonable velocity commands based on the sensors' measurements to guide your robot navigating towards the goal. 
  - (1%) Switch to `PAUSE` mode at the moment the tactile button is **released**.

#### 3.4.4. (5%) Terminate the navigation if the robot thinks it reached the destination.
   Lit solid $\color{purple}\text{purple}$ to indicate end of journey.  

#### 3.4.5. (10% Bonus) Adjust brightness of the LEDs and behavior of the robot based on the battery voltage (apply to `WORK` mode).
  - For 8.4 V and above: only $\color{green}\text{green}$ LED with full brightness
  - From 7.4 V to 8.4 V: $\color{green}\text{green}$ LED brightness from 50% to maximum, while $\color{red}\text{red}$ LED brightness from 50% to 0.
  - From 6.4 V to 7.4 V: $\color{green}\text{green}$ LED brightness from 0 to 50%, while $\color{red}\text{red}$ LED brightness from maximum to 50%.
  - Shut down the system/robot if battery voltage fell below 6.4 V.

#### 3.4.6. (10% Bonus) Implement sensor fusion algorithm to better estimate robot's motion status. 

### 3.5. Documentation (15% Base + Bonus)
> [!CAUTION]
> All project documentation must be committed directly to your repository's root [README.md](README.md) file.

#### 3.5.1. (8%) Mechanical drawings
- (2%) Display the portrait of your robot with resolution of 800 px. by 600 px..
- (6%) Display all the mechanical drawings with resolution of 1200 px. by 900 px..

#### 3.5.2. (4%) Wiring diagrams
Display the wiring diagram(s).

#### 3.5.3. (2%) Algorithm charts
Document navigation algorithms

#### 3.5.4. (1%) Acknowledge AI's contributions 
Please list out all the AI's contributions to this project.

## 4. Resources
- [Differential driver controller examples code](https://github.com/linzhangUCA/3421example-differential_drive_controller).
- [Distance sensor example code](https://github.com/linzhangUCA/3421example-ultrasonic_sensor).
- [IMU example code](https://github.com/linzhangUCA/3421example-inertial_measurement_unit).
- [Servo control example code](https://github.com/linzhangUCA/3421example-servo).
- [Reference mechanical Design](https://github.com/linzhangUCA/tbot_mechanical).
- [Reference electrical Design](https://github.com/linzhangUCA/tbot_electrical).
- [Sensor fusion tutorial](https://youtu.be/0rlvvYgmTvI?si=u2gn0NF3f4oAkx-W)
