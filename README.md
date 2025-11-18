# Lab Rover

## Background Story

On the surface of the planet LSC-001e, our brave rover R1B has successfully secured a volatile sample of "Element M2-5", a crucial resource to build planetary engines.
Now begins the perilous return journey to the Base Station, a navigation challenge that would fry the circuits of lesser bots.
R1B must traverse the extraterrestrial terrain, relying on its sensors to differentiate between solid ground and deceptively steep cliffs.
The good news is, on the way to the sampling site, R1B memorized the surrounding environment and made a map.
R1B shared this information to its trustworthy human partner, you, and is waiting on a reliable plan to start the journey back home.

![lab_nav](images/lab_nav.jpg)

## Preparation Instructions

## Requirements

- Complete [Documentation](#documentation) to show off your designs.
- Upload scripts controlling the robot to this repository.

### 1. (15%) Mechanical Design

- (7%) Technical drawing of the robot base.
- (3%) Technical drawing of the motor bracket.
- (3%) Technical drawing of the driving wheel.
- (2%) Technical drawing of the caster wheel.

> [!TIP]
>
> - People are supposed to follow these drawing to replicate an identical physical structure of the robot.
> - Please refer to the [image insertion guide](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#images)

### 2. (10%) Electrical Design

- (7%) Diagram of signal wire connections in-between Pico, motor driver, motors, encoders, distance sensors and other sensors.
- (3%) Wiring diagram for all electrical components.

> [!TIP]
>
> - You can use one diagram for all.
> - People are supposed to follow these diagrams to get the electrical components to work.

### 3. (10%) Software Design

- Describe the control logic of the navigation using a list of steps, or a algorithm table, or a flowchart.

### 4. (70%) Coding

- Code a class to include both "differential drive controller" and "distance sensor" instances.
- Initialize the robot by checking all the sensors and actuators are functional.

> [!TIP]
> Use the RGB LED on the board to indicate the functionality of the components.

- While your robot is running, use Green LED's brightness to indicate distance sensor's detection.
- **The robot's behavior will only be regulated by the referenced linear and angular velocities**.

### 5. (5%) Broader Impact

![layout](link)

## Documentation

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
