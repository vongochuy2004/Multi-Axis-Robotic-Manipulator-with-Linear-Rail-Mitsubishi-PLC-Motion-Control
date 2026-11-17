# Multi-Axis-Robotic-Manipulator-with-Linear-Rail-Mitsubishi-PLC-Motion-Control
Development of a 3DOF robotic manipulator integrated with a linear sliding rail, controlled by Mitsubishi FX3U/FX3G PLCs and FX3U-1PG positioning module. The project focuses on multi-axis motion control, pulse-based positioning, forward and inverse kinematics, coordinated movement, and sequential point-to-point operation.
# 3DOF Robotic Manipulator with Linear Rail using Mitsubishi PLC

## 1. Project Overview

This project involves the development of a **3-DOF robotic manipulator integrated with a linear sliding rail**, using Mitsubishi FX-series PLCs for multi-axis motion control.

The system consists of a three-axis robotic arm and an additional linear rail axis, providing an extended workspace and enabling the robot to perform positioning tasks at multiple locations.

The control architecture combines Mitsubishi FX3G PLC, FX3U PLC, and FX3U-1PG positioning module to control four stepper motor axes through pulse-based motion control.

The project focuses on robotic kinematics, multi-axis positioning, motion sequencing, pulse generation, and PLC-based automation.

## 2. System Architecture

The system is divided into the following main components:

### 2.1. Robotic Manipulator
- Three degrees of freedom (3-DOF).
- Three stepper motors for joint actuation.
- Forward Kinematics (FK) for calculating end-effector position.
- Inverse Kinematics (IK) for converting Cartesian coordinates into joint angles.
- Point-to-point robotic positioning.

### 2.2. Linear Sliding Rail
- One additional linear motion axis.
- Extends the robot's operating workspace.
- Uses an independent positioning coordinate for each movement.
- Integrates with the robot's motion sequence.

### 2.3. PLC Motion Control
- Mitsubishi FX3G PLC generates pulse and direction signals for the three robotic axes.
- Mitsubishi FX3U PLC works with the FX3U-1PG positioning module for the linear rail axis.
- TB6600 stepper motor drivers interface with the stepper motors.
- PLC programs manage positioning commands, motion sequences, and operating conditions.

## 3. Hardware Configuration

| Component | Quantity | Function |
|---|---:|---|
| Mitsubishi FX3U PLC | 1 | Main positioning control |
| Mitsubishi FX3G PLC | 1 | 3-axis robot motion control |
| FX3U-1PG | 1 | Linear rail positioning |
| Stepper motors | 4 | Three robot joints and one rail axis |
| TB6600 drivers | 4 | Stepper motor drivers |
| Limit switches | 4 | Homing and travel limit detection |
| Relay modules | 2 | Conveyor and vacuum pump control |

### Additional I/O
- Four limit switches for the four motion axes.
- Relay output for conveyor control.
- Relay output for vacuum pump control.

## 4. Motion Control

### 4.1. Pulse-Based Positioning

The system uses pulse and direction signals to control stepper motor movement.

For the three robotic axes:
- Y0–Y2: Pulse outputs.
- Y4–Y6: Direction outputs.

The linear rail is controlled separately through the FX3U-1PG positioning module.

### 4.2. Multi-Axis Motion

The robot executes a sequence of predefined Cartesian target positions.

The motion control program calculates the required joint positions and generates corresponding pulse commands.

The rail axis maintains its own target coordinates for each movement segment.

The example test sequence is:

**Origin → P1 → P2 → P1 → P3 → P4 → P3**

The sequence contains:
- Four predefined Cartesian robot test points.
- Six independent rail target positions.
- Sequential point-to-point positioning.

### 4.3. Motion Speed Calculation

The project explores coordinated speed calculation for multiple axes.

The objective is to synchronize axis movement based on the required displacement and movement time, rather than simply commanding each axis at an independent constant speed.

## 5. Robot Kinematics

### Forward Kinematics (FK)
Calculates the end-effector Cartesian position based on the robot's joint angles.

### Inverse Kinematics (IK)
Converts a target Cartesian position into the corresponding joint angles.

The calculated joint positions are converted into pulse commands for PLC motion control.

## 6. PLC Communication and Data Handling

The system uses a PC-to-PLC communication interface to transfer motion parameters and target coordinates.

The PLC receives positioning data and executes the corresponding motion sequence.

The positioning data structure includes:
- Cartesian coordinates for four robot test points.
- Independent rail coordinates for six movement segments.
- 32-bit positioning values stored across consecutive PLC registers.

### Rail Position Data

The rail target positions are assigned to the following PLC register addresses:

| Movement | Starting address |
|---|---|
| Rail Point 1 | D338 |
| Rail Point 2 | D342 |
| Rail Point 3 | D346 |
| Rail Point 4 | D350 |
| Rail Point 5 | D354 |
| Rail Point 6 | D358 |

Each rail coordinate uses two consecutive 16-bit registers.

## 7. Homing and Auxiliary Control

- Four limit switches provide home-position detection.
- Homing routines establish reference positions for the robot and linear rail.
- Relay outputs control the conveyor and vacuum pump.
- Sequential control coordinates robotic movement with auxiliary equipment.

## 8. Software and Technologies

| Technology | Application |
|---|---|
| Mitsubishi FX3G | Three-axis pulse motion control |
| Mitsubishi FX3U | PLC positioning system |
| FX3U-1PG | Linear axis positioning |
| GX Works2 | PLC programming |
| Python | Motion data processing and PLC communication |
| pymcprotocol | Mitsubishi PLC communication |
| MATLAB / Python | Kinematics calculation and verification |
| TB6600 | Stepper motor driving |

## 9. Key Engineering Skills

- Mitsubishi PLC programming.
- Stepper motor pulse and direction control.
- Multi-axis motion control.
- Robotic Forward and Inverse Kinematics.
- Cartesian-to-joint coordinate transformation.
- Point-to-point positioning.
- Motion sequence programming.
- PLC communication using Python.
- Industrial sensor and actuator integration.
- Homing and limit switch configuration.

## 10. Project Scope

This project is developed as an educational robotic automation system to explore the integration of robotic kinematics, PLC-based motion control, and linear-axis positioning.

The implementation focuses on the coordination of a 3-DOF robotic manipulator and an independent linear rail axis using Mitsubishi PLC hardware.

---

**Technologies:** Mitsubishi FX3U | FX3G | FX3U-1PG | GX Works2 | Python | pymcprotocol | TB6600 | Stepper Motors | Robot Kinematics | Motion Control
