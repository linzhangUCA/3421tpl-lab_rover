# Lab Rover
> [!IMPORTANT]
> ## $\color{#582c83}\text{Demonstration Due: Thursday, Dec. 10th @ 1 PM}$
> ## $\color{#582c83}\text{Submission Due: Thursday, Dec. 10th @ 5 PM}$

## 1. Background Story

On the surface of the planet LEDG-100c, our brave rover TBot has successfully secured a volatile sample of "Element M2-5", a crucial resource to build planetary engines.
Now begins the perilous return journey to the Base Station, a navigation challenge that would fry the circuits of lesser bots.
TBot must traverse the extraterrestrial terrain, relying on its sensors to differentiate between solid ground and deceptively steep cliffs.
The good news is, on the way to the sampling site, TBot memorized the surrounding environment and made a map.
TBot shared this information to its trustworthy human partner, you, and is waiting on a reliable plan to start the journey back home.

## 2. Autonomous Navigation Procedure

![lab_nav](./assets/images/lab_nav.jpg)

1. Set the robot behind the "Start Line" and receive the payload ("Element M2-5", an M2.5 nut).
2. Initialization and self-check.
3. Start autonomous navigation (can be manually activated).
4. Avoid the "Danger Zones", and finish inside (or as close as possible to) the "Home Base".
5. Indicate the autonomous navigation is finished (red light).

> [!CAUTION]
>
> - Human intervention will terminate the navigation after the robot crossed over the "Start Line".
> - Entering the "Danger Zones" will terminate the navigation.
> - The distance between the navigation ending location and the "Home Base" will be the dominating metric to evaluate the quality of the navigation.
See [coding requirements](#5-60-coding) below for more details.
> - **Big reward** is awaiting at the "Home Base".

## 3. Requirements
- Complete [Documentation](#documentation) and describe your designs.
- Upload your robot controlling scripts to this repository.

### 3.1. Mechanical Design & Implementation (15% Base)
- (?%) Assemble your robot and upload a portrait picture (you pick the viewing angle) for your robot.
  Try to reveal as many key components as possible.
- (?%) Use _Top View_, _Side View_ and _Front View_ drawings to illustrate:
  - Dimensions of the key components (base, wheels, circuit boards, **payload storage**, etc.).
  - Locations and layout of of the key components.

### 3.2. Electrical Design & Practice (10% Base + Bonus)
Wire up all the electrical and electronics components.
- (?%) Upload schematic(s) of wiring diagram depicting the power distribution and the signal networking.
- (**?% Bonus**) Self-Soldered PCB of TBot control relay.

### 3.3. Software Design (10% Base + Bonus)
- (?%) Describe the logic of the navigation using a list of steps, or a [algorithm table](https://i.sstatic.net/6hfCG.png), or a [flowchart](https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/LampFlowchart.svg/960px-LampFlowchart.svg.png).
- (**?% Bonus**) Fuse the IMU measurement with the encoders'. Explain your sensor fusion approach with math language. 

### 3.4. Coding (60% Base + Bonus)
1. (?%) Initialization (System Check).
   - (?%) On power-up, verify sensors are functional.
     - Button GPIO pin reads its configured default resting logic level (0 for PULL_DOWN, 1 for PULL_UP)
     - Ultrasonic sensor (if applied) returns a non-zero, valid distance reading.
     - IMU (if applied) returns non-zero, reasonable motion data.
   - (?%) Verify actuators are functional.
     - Spin mobile base exactly 90 degrees CCW or CW in place, then spin it back (to also verify the encoders are functional)
     - Spin servo (if applied) exactly 90 degrees CCW or CW, then spin it back.
   - If all of the above conditions are met, blink all status LEDs simultaneously at 5 Hz for 2 seconds.
   - Automatically transition into `PAUSE` mode upon successful self-test completion.
 > [!IMPORTANT]
 > If any initialization check fails, the robot **must not** proceed to active navigation.

2. (3%) When `PAUSE` mode is activated:
  - (1%) Stop all actuators.
  - (1%) Modulate the $\color{green}\text{green}$ LED with a breathing/fading effect at 1 Hz (allocating equal duration to fade-in and fade-out cycles).
  - (1%) Switch to `WORK` mode at the moment the tactile button is **released**.

3. (3%) When `WORK` mode is activated:
  - (1%) Solid $\color{green}\text{green}$ LED continuously lit.
  - (?%) Calculate reasonable velocity commands based on the sensors' measurements to guide your robot navigating towards the goal. 
  - (1%) Switch to `PAUSE` mode at the moment the tactile button is **released**.

4. (?%) Terminate the navigation if the robot thinks it reached the destination.
   Lit solid $\color{purple}\text{purple}$ to indicate end of journey.  

- (**?% Bonus**) Adjust brightness of the LEDs and behavior of the robot based on the battery voltage.
  - For 8.4 V and above: only $\color{green}\text{green}$ LED with full brightness
  - From 7.4 V to 8.4 V: $\color{green}\text{green}$ LED brightness from 50% to maximum, while $\color{red}\text{red}$ LED brightness from 50% to 0.
  - From 6.4 V to 7.4 V: $\color{green}\text{green}$ LED brightness from 0 to 50%, while $\color{red}\text{red}$ LED brightness from maximum to 50%.
  - Shut down the system/robot if battery voltage fell below 6.4 V.

- (**?% Bonus**) Implement proposed sensor fusion approach as described in [Section 3.3.](#3.3.-software-design-10-base-+-bonus). 


> [!IMPORTANT]
>
> - If the robot failed to finish the navigation inside of the "Home Base", and $d$ (in meters) is the distance between the navigation ending location and the "Home Base". $30 - d /0.46$ points will be will be given to the navigation coding.
> - If the navigation finished inside of the "Home Base", 30% **bonus** points will be given.
> - Traveling in-between the "Tracks" is highly recommended (5% bonus if the robot can do so).
> - You have the freedom to configure your robot to fulfill the requirements.

## Documentation
>
> [!TIP]
> Please refer to Github's [Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Mechanical Designs

#### Base Tech Draw

![base_tech_draw](base_tech_draw.jpg)

#### Motor Bracket Tech Draw

![motor_bracket_tech_draw](motor_bracket_tech_draw.jpg)

#### Driving Wheel Tech Draw

![drive_wheel_tech_draw](drive_wheel_tech_draw.jpg)

#### Caster Wheel Tech Draw

![caster_tech_draw](caster_tech_draw.jpg)

### Electrical Designs

![wiring](wiring.jpg)

### Software Designs

![algorithm](algorithm.jpg)

### Broader Impact
