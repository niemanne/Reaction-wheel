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




