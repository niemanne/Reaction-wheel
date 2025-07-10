# Week 1 - Design and Plan
## 7/9/2025 - project begins
What was done:
- set up folders (firmware/, hardware/, media/)
- created build log
- researched reaction wheel systems
- watched How Reaction Wheels Actually Work & Understanding Reaction Wheels
- Read Kepler Mission Operations Response to Wheel Anomalies, Introduction to Reaction Wheels by Space Steps
- Looked at past projects such as a single-axis reaction wheel self-balancing system and Charles' Labs - reaction wheel attitude control
- chose basic concept of design: one-axis (z-axis) based reaction wheel
- began preliminary brainstorming for designs (looked at different balancing geometrys)
- sketched 3 very basic possible designs

Topics Studied:
- basic physics of reaction wheel s(conservation of angular momentum)
- difference between rw and thrusters
- design requirements for full 3 axis control (3+ wheels)
- Real world example: Kepler Space Telescope

Key Takeaways:
- reaction wheels have fine precisions, don't require fuel, and are lightweight
- don't work well with outside forces that throw off the center of gravity
- center of gravity and balance are crucial
- Angular momentum exchange is how movement is achieved

Equations + Concepts:
- Conservation of angular momentum:
  I(fly) * w(fly) + I(sat) * w(sat) = k
-  Moment of intertia (cylinder):
  I = .5mR^2

Design Considerations: 
- Reaction wheel must be rigidly mounted and spin smoothly
- Motor must have strong torque and minimal jitter
- IMU feedback is essential for real-time correction
- Eventually, will implement a PID control loop

Z-Axis Design choice:
- It would be an easier design to work with; I am unexperienced in personal projects so I thought it would be important to start with something easier
- One degree of freedom: this means I only have to utilize one reaction wheel, soley accounting for one way the object could move

Hardware updates:
Three possible design layouts were brainstormed (see `hardware/initial_sketch_7-9.jpg`). 
- The leading candidate is a tripod style balance beam, which provides extra x/y axis support while isolating the z-axis for rotational testing and PID specialization

## 7/10/2025 - intial design 
What was done:
- researched principles of PID
- made a document describing the thought process behind preliminary reaction wheel designs

Topics studied:
- priniples of PID

key takeaways:
- A PID is a proportional integrative derivative controller that works by controlling an output to bring a process value to a setpoint
**Set point (SP):** a user entered value/target value (upright orientation)
**Process value:** value that is being controlled/ current sensor reading (current angle)
**Output:** the controlled value of a PID controller
**Error:** error value used to determine how to manipulate the output to bring the process value to the set point
- **P or Proportional:** Used to have a large immediate reaction on the output; Error is smaller, influence of proportional value on output is less
- **D or Derivative:** Used to predict where the process value is going; Bias the output in the opposite direction of proportional and integral
- **I or Integral:** Doesn’t have as much immediate influence on output as proportional; continuously accumulating; Takes longer for process value to reach set point -> More effect integral will have on output

Equations + concepts:
\[Error = setpoint - process value\]
- kP = proportional gain, SP = set point, PV = process value, Err = Error, P = proportional
\[Err = SP - PV\]
\[P = kP x Err\]
- I = Integral, kI = Integral Gain, dt = cycle time of the controller, It = integral total
\[I = kI x Err x dt\]
\[It = It + I\]
- D = derivative, kD = derivative gain, dt = cycle time of controller, pErr = previous Error
\[D = kD x (Err - pErr) / dt\]
- Output:
\[P + It + D\]

**key note:** You may need to tune kP, kI, kD through trial and error

Preliminary reaction wheel designs:
- Design considerations: Keep the geometry simple; Make sure that the design is symmetric; Ex: equilateral triangle, square, circle;
- Only has one wheel: can only be stabilized along one axis; can only be one degree of freedom
- Z-axis: the y- and x-axis must be fixed
- focus on stabilization
- No rotational efforts:
- Cardboard or 3d: more precise through 3D printing; More precise dimensions = more accurate C.O.M

Brainstorming design ideas:
- Rectangular prism that balances on one edge
- Triangular prism that balances on one edge
- Cylinder balancing on two beams stabilising y- and x- axis









