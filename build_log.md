# Week 1 - Design and Plan
## 7/9/2025 - project begins

### Summary
To begin the project, research on reaction wheel systems was done, exploring how they operate and their usage. Also looked at previous designs for inspiration to lay down the foundations for the beginning of the project. Chose to use a one-axis based reaction wheel due to simplicity and time-restraints. 

### What was done:
- set up folders (firmware/, hardware/, media/)
- created build log
- researched reaction wheel systems
- watched How Reaction Wheels Actually Work & Understanding Reaction Wheels
- Read Kepler Mission Operations Response to Wheel Anomalies, Introduction to Reaction Wheels by Space Steps
- Looked at past projects such as a single-axis reaction wheel self-balancing system and Charles' Labs - reaction wheel attitude control
- chose basic concept of design: one-axis (z-axis) based reaction wheel
- began preliminary brainstorming for designs (looked at different balancing geometrys)
- sketched 3 very basic possible designs

### Topics Studied:
- basic physics of reaction wheel s(conservation of angular momentum)
- difference between rw and thrusters
- design requirements for full 3 axis control (3+ wheels)
- Real world example: Kepler Space Telescope

### Key Takeaways:
- reaction wheels have fine precisions, don't require fuel, and are lightweight
- don't work well with outside forces that throw off the center of gravity
- center of gravity and balance are crucial
- Angular momentum exchange is how movement is achieved

### Equations + Concepts:
- Conservation of angular momentum:
  I(fly) * w(fly) + I(sat) * w(sat) = k
-  Moment of intertia (cylinder):
  I = .5mR^2

### Design Considerations: 
- Reaction wheel must be rigidly mounted and spin smoothly
- Motor must have strong torque and minimal jitter
- IMU feedback is essential for real-time correction
- Eventually, will implement a PID control loop

### Z-Axis Design choice:
- It would be an easier design to work with; I am unexperienced in personal projects so I thought it would be important to start with something easier
- One degree of freedom: this means I only have to utilize one reaction wheel, soley accounting for one way the object could move

### Hardware updates:
Three possible design layouts were brainstormed (see `hardware/initial_sketch_7-9.jpg`). 
- The leading candidate is a tripod style balance beam, which provides extra x/y axis support while isolating the z-axis for rotational testing and PID specialization

### Notes:
A one-axis design seemed the most reasonable option for the level of expertise currently aquired. No issues so far.

## 7/10/2025 - intial design 
### Summary
Initial designs were formulated and compared based on previous research. The principles of PID control, vital to reaction wheels, was also explored as a means to begin the software of the system. 

### What was done:
- researched principles of PID
- made a document describing the thought process behind preliminary reaction wheel designs
- made a documet describing all the parts I have
- asked questions about what parts are still needed

### Topics studied:
- core priniples + equations of PID (proportional-integral-derivative) controller

### key takeaways:
- A **PID controller** is a proportional integrative derivative controller that works by controlling an output to bring a process value to a setpoint
- **Set point (SP):** a user entered value/target value (upright orientation)
- **Process value:** value that is being controlled/ current sensor reading (current angle)
- **Output:** the controlled value of a PID controller
- **Error:** error value used to determine how to manipulate the output to bring the process value to the set point
- **P or Proportional:** Used to have a large immediate reaction on the output; Error is smaller, influence of proportional value on output is less
- **D or Derivative:** Used to predict where the process value is going; Bias the output in the opposite direction of proportional and integral
- **I or Integral:** Doesn’t have as much immediate influence on output as proportional; continuously accumulating; Takes longer for process value to reach set point -> More effect integral will have on output

### Equations + concepts:
- \[Error = setpoint - process value\]

kP = proportional gain, SP = set point, PV = process value, Err = Error, P = proportional
- \[Err = SP - PV\]
- \[P = kP x Err\]

I = Integral, kI = Integral Gain, dt = cycle time of the controller, It = integral total
- \[I = kI x Err x dt\]
- \[It = It + I\]

D = derivative, kD = derivative gain, dt = cycle time of controller, pErr = previous Error
- \[D = kD x (Err - pErr) / dt\]
- Output:
\[P + It + D\]

**key note:** You may need to tune kP, kI, kD through trial and error

### Preliminary reaction wheel designs:
Design considerations: 
- Keep the geometry simple
- Make sure that the design is symmetric
- Ex: equilateral triangle, square, circle
- Z-axis: the y- and x-axis must be fixed
- focus on stabilization
- No rotational efforts:
- Only has one wheel
- can only be stabilized along one axis
- can only be one degree of freedom

Cardboard or 3d:
- more precise through 3D printing
- More precise dimensions = more accurate C.O.M

### Brainstorming design ideas:
- Rectangular prism that balances on one edge
- Triangular prism that balances on one edge
- Cylinder balancing on two beams stabilising y- and x- axis

## 7/13/2025 - finalize design + parts
### Summary:
Researched and ordered the components necessary for the wheel, including the MPU 6050, a motor driver, and a higher functioning motor. The rectangular prism frame was chosen after evaluation using a design matrix. 

### What was done:
- updated parts list
- found amazon links for necessary parts that are still needed
- created a parts list on Git (docs/parts_list.md)
- made a decision matrix comparing the 3 initial designs
- chose to use the rectangular prism frame based on a set of 5 criteria

### Updated Parts list:
What I have:
- Arduino Uno (brain)
- brainstorming (breadboard/ jumperwires)
- basic DC motor (good for testing)

What I need:
- MPU-6050 (sensor)
- DC motor-12V (motor)
- Driver (L298N)
- 2S LiPo battery (Power)
- Flywheel (3D printed)
- Frame (3D printed)

***Decision Matrix Results and Output***

The design I am going to be pursing is the **rectangular prism** design based on its ease of manufacturing, especially with my limited supplies, its structural soundness, and the ability to fit electronic components. 

The **cylinder with two beams** was a close second, but ultimately was not chosen because it required higher manufacturing skills to build accurately.

The **triangular prism** ranked the lowest due to its limited ability to fit the electronic compoents and balance concerns.

Criteria:
- Ease of construction
- balance stability
- component fit
- center of mass control
- aesthetics


| **Criteria**             | **Weight (1–5)** | **Rectangular Prism** | **Triangular Prism** | **Cylinder on Beams** |
| ------------------------ | ---------------- | --------------------- | -------------------- | --------------------- |
| Ease of Manufacturing    | 5                | 5 (25)                | 4 (20)               | 2 (10)                |
| Structural Stability     | 4                | 4 (16)                | 3 (12)               | 4 (16)                |
| Component Fit/Layout     | 3                | 5 (15)                | 3 (9)                | 4 (12)                |
| Weight Distribution      | 4                | 4 (16)                | 3 (12)               | 4 (16)                |
| Aesthetic Appeal         | 2                | 3 (6)                 | 2 (4)                | 5 (10)                |
| **Total Weighted Score** |                  | **78**                |  **57**                   | **64**                      |

The ranking:
- Rectangular Prism (84 points)
- Cylinder on balance beams (74 points)
- Triangular Prism (61)

## 7/14/2025 - Edit final Design + test electronics
### Summary:
Took time to understand how each of the electronic components worked together and began formulating the plan to wire those components. 

### What was done:
- looked at the specs of every electronic and how they interacted with eachother
- Made an electronics summary folder (docs/electronics_summary.md)
- redrew electronic layout, considering the dimensions of each electronic as well as space needed for wiring

# Week 2 - Early Hardware Integration and PID Loop Development
## 7/15/2025 to 7/21/2025 

### What was done:
- Created initial PID loop code and ran simulations to verify control logic  
- Ordered and received necessary hardware: motor, motor driver (L298N), IMU (MPU-6050), and flywheel  
- Finalized preliminary electronics design, including wiring diagrams and component layout planning  
- Decided to prototype physical frame using LEGO bricks for rapid iteration and easy adjustments  
- Started basic motor tests via Arduino with PWM control to confirm motor functionality  
- Ran example sketches on IMU and monitored sensor data through serial monitor to understand output behavior  
- Updated GitHub repo structure; began drafting README and documentation (to be expanded)  

### Topics studied:  
- PID loop implementation on Arduino  
- Motor driver interfacing and control via PWM and direction pins  
- IMU calibration and filtering for stable sensor feedback  
- Rapid prototyping methods for mechanical assembly (LEGO frame)  
- Basic motor balancing and mounting considerations  

### Key takeaways:  
- PID controller must be tuned with real sensor feedback for accurate attitude control  
- LEGO frame provides a quick and flexible method to protoprototype mechanical setup  
- Independent testing of motor and IMU components helps identify issues before full integration  
- Maintaining detailed build logs improves project organization and motivation  

### Next steps planned:  
- Build LEGO test frame and securely mount motor + flywheel  
- Wire motor driver and IMU to Arduino and verify integrated operation  
- Port PID loop code to hardware and begin iterative tuning with sensor input  
- Document wiring and physical setup with photos for GitHub upload  
- Conduct initial system testing focusing on stability and disturbance response  

# Week 3 - Prototype Assembly and PID Hardware Integration

## 7/22/2025 

### Summary:
Began integrating core hardware components into a temporary test rig made out of LEGOs in order to validatemotor function and system layout before finalizing the flywheel design. This mark the transition from designing/ planning into initial system prototyping.

### What was done:
- constructed a LEGO-based testing rig to mount the DC motor and other electronic hardware
   - Frame includes 2 vertical towers supporting the DC motor as well as the flywheel
   - the Baseplate holds the Arduino Uno, motor driver, and the MPU-6050 to be held securely
 - the motor was offset in the testing rig, to exposes its 12 mm long shaft for flywheel attachment
 - created a temporary flywheel outof cardboard, electric tape, and some bolts
    - placed on the shaft of the motor
    - designed to simulate inertial load for initial test spinning

### Topics Studied
- prototyping techniques with LEDOs
- motor shaft alignment considerations

### Notes:
This initial prototyping emphasized conveinence - parts were limited so the test rig was created using household items and LEGO components. While a temporary measure, this step allows early testing and software management before commiting to a final flywheel desing.

A picture of the test rig has been added in '/media/' for documentation. 

## 7/24/2025 - initial testing
Double-check the flywheel is properly balanced and attached firmly to the motor shaft.

Ensure the motor is mounted securely to avoid wobble or misalignment.

Run basic spin tests at low speeds, observe behavior (vibration, noise, smoothness).

Note any issues and start thinking about how to troubleshoot or improve.
Finalize frame requirements (dimensions, motor mounting points, sensor placement)

Start CAD model of the frame (rectangular prism design)

Make sure to leave space for wiring and components

Export initial CAD drawings for review

Backup/save your CAD files in organized folder







