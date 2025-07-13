# 📦 Parts List – Reaction Wheel Balancing Project

This document outlines all the components used in the one-axis reaction wheel balancing system. It is divided into what I already have, what I need to order, and the final planned system configuration.

---

## ✅ What I Already Have

| Component                  | Description                              | Notes                          |
|---------------------------|------------------------------------------|--------------------------------|
| Arduino Uno R3            | Microcontroller (brain)                  | Rockbee kit                    |
| Servo Motor (SG90)        | Positional control (not used for RW)     | Not suitable for flywheel use  |
| "Direct Current Machine"  | Small DC motor                           | Testing usability              |
| Jumper Wires              | For breadboarding                        | Female-to-male + male-to-male  |
| Resistors                 | Various values (220R–1M)                 | Useful for sensor filtering    |
| USB Cable                 | For Arduino power and programming        |                                |
| Breadboard                | For prototyping circuits                 |                                |
| 9V Battery + Snap         | For basic testing                        | Not ideal for full system      |
| Hall Sensor               | Magnetic field detection                 | Not used in current design     |
| IR Receiver + Remote      | For IR signal decoding                   | Not used in this build         |
| 5V Relay Module           | Switch circuit (not used in RW)          | Not needed for motor control   |
| Tilt Switch               | Simple angle detection                   | Replaced by IMU                |
| Transistors + Diodes      | General circuit components               | Optional                       |
| Power Supply Module       | Breadboard-compatible regulator          | Optional for sensor isolation  |
| Prototype Expansion Board | Additional prototyping space             |                                |

---

## 📦 What I Need to Order

| Component         | Description                             | Suggested Link / Specs                                             | Status   |
|------------------|-----------------------------------------|--------------------------------------------------------------------|----------|
| **DC Motor (12V)**| High-RPM brushed motor                  | [AUTOTOOLHOME 6–12V](https://www.amazon.com/dp/B078S4P1GV)         | ❌       |
| **Motor Driver**  | L298N Dual H-Bridge                     | [WWZMDiB L298N](https://www.amazon.com/dp/B087CJK4MG)              | ❌       |
| **IMU Sensor**    | MPU-6050 (gyro + accelerometer)         | [EPLZON GY-521](https://www.amazon.com/dp/B01M0N8BW7)              | ❌       |
| **Battery**       | 2S LiPo 7.4V + charger                  | [AMZZN 2000mAh w/ XT60](https://www.amazon.com/dp/B09FJ9YQ28)      | ❌       |
| **Flywheel**      | 3D printed or metal disc                | To be custom designed and printed                                 | 🔄 In Progress |
| **Frame**         | 3D printed or cardboard mockup          | Tripod balancing frame design                                     | 🔄 In Progress |

---

## 🔧 Final Target Configuration

| Subsystem        | Component                     |
|------------------|-------------------------------|
| Controller       | Arduino Uno R3                |
| Sensor           | MPU-6050                      |
| Motor            | 12V DC Motor                  |
| Driver           | L298N Motor Driver            |
| Power Supply     | 2S LiPo (7.4V) Battery        |
| Flywheel         | 3D Printed Heavy Disk         |
| Frame            | 3D Printed Tripod Structure   |

---

## 🧠 Notes

- Servo motors are **not** suitable for this project due to their limited rotation.
- Relay modules and IR receivers are unnecessary for a closed-loop balancing system.
- Use LiPo batteries instead of alkaline or carbon-based due to **higher current output**, lighter weight, and **rechargeability**.
- The L298N is widely used, but consider heat dissipation for continuous use.

---

*Last updated: 2025-07-12*
