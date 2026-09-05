# PID Motor Speed Controller

A DC motor speed control system built using an Arduino Uno, TB6612FNG motor driver, and a 6 V DC motor with an encoder.

The system uses encoder feedback and a PID controller to adjust the motor speed through PWM. The circuit was first tested on a breadboard and then recreated as a schematic and custom PCB in KiCad.

---

## Project Overview

The goal of this project was to learn how PID control and encoder feedback can be used to control the speed of a DC motor.

The encoder measures the motor speed and sends this information to the Arduino. The Arduino compares the measured speed with the target speed and uses a PID controller to adjust the PWM signal sent to the motor driver.

The project was first built and tested on a breadboard before designing the schematic and PCB in KiCad.

---

## Hardware

| Component | Purpose |
|---|---|
| [MECCANIXITY 6 V DC Gear Motor with Encoder](https://www.amazon.ca/MECCANIXITY-Encoder-Gearbox-Electric-Reduction/dp/B0F8NH1M4Z/) | DC motor with encoder feedback |
| [TB6612FNG Motor Driver Module](https://www.amazon.ca/Hyuduo-Motors-Driver-Controller-TB6612FNG/dp/B09PGJ8J8K/) | Controls motor speed and direction |
| Arduino Uno R3 | Runs the PID controller and reads the encoder |
| [2.1 mm DC Jack Screw Terminal](https://www.amazon.ca/2-1mm-Screw-Terminal-Power-Connector/dp/B07MQTCZBG/) | Connects the motor power supply |
| [Solderless Breadboard](https://www.amazon.ca/Breadboard-Solderless-Prototype-Distribution-Connecting/dp/B01EV6LJ7G/) | Used for initial prototyping |
| Jumper Wires | Circuit connections |
| 7.5 V Battery Pack | Motor power supply |

---

## Breadboard Prototype

The circuit was first assembled on a breadboard to make sure the Arduino, motor driver, motor, and encoder worked correctly before designing the PCB.

### Breadboard Setup

![Breadboard Prototype](images/breadboard.jpg)

---

## How It Works

The system uses a feedback loop to continuously adjust the motor speed.

```text
Target Speed
     |
     v
PID Controller
     |
     v
PWM Output
     |
     v
TB6612FNG
     |
     v
DC Motor
     |
     v
Encoder
     |
     v
Measured Speed
     |
     +--------> PID Controller
```

The process works by:

1. Setting a target motor speed
2. Reading pulses from the motor encoder
3. Measuring the current motor speed
4. Comparing the measured speed with the target speed
5. Calculating the error
6. Using the PID controller to determine the PWM output
7. Sending the PWM signal to the TB6612FNG motor driver
8. Repeating the process as the motor runs

---

## PID Controller

The PID controller uses three values:

- **Kp** responds to the current error
- **Ki** responds to error that builds up over time
- **Kd** responds to how quickly the error is changing

The error is calculated by comparing the target speed with the measured motor speed.

The result of the PID calculation is used to control the PWM signal sent to the motor driver.

The Arduino PWM output ranges from:

```text
0   = Minimum output
255 = Maximum output
```

The PID values were tested and tuned while viewing the motor speed and PWM output through the Arduino Serial Monitor.

---

## Arduino Code

The Arduino program:

- Reads the motor encoder
- Measures motor speed
- Calculates the difference between the target and measured speed
- Runs the PID calculation
- Adjusts the PWM output
- Displays speed and PWM data through Serial Monitor

The main Arduino code can be found in:

```text
firmware/PID_Motor_Controller.ino
```

---

## Serial Monitoring

The Arduino Serial Monitor was used to view the target speed, measured speed, and PWM output while testing and tuning the controller.

Example output:

```text
Target: 2100  Speed: 2050  PWM: 132
Target: 2100  Speed: 2080  PWM: 128
Target: 2100  Speed: 2110  PWM: 124
```

> Replace the example above with actual Serial Monitor data from testing.

### Serial Monitor

![Serial Monitor](images/serial-monitor.png)

---

## Circuit Schematic

After getting the circuit working on the breadboard, the same circuit was recreated as a schematic in KiCad.

The schematic includes connections for:

- Arduino Uno
- TB6612FNG motor driver
- DC motor
- Encoder
- Motor power supply
- PWM control
- Motor direction control
- Common ground

### KiCad Schematic

![Circuit Schematic](images/schematic.png)

The full schematic can also be included as:

```text
hardware/schematic.pdf
```

---

## PCB Design

After completing the schematic, I designed a custom PCB in KiCad based on the tested breadboard circuit.

The PCB provides connections for the Arduino, motor driver, motor encoder, and external motor power supply.

### PCB Layout

![PCB Layout](images/pcb-layout.png)

### PCB 3D View

![PCB 3D View](images/pcb-3d.png)

The KiCad project files are available in:

```text
hardware/kicad/
```

---

## Final Setup

The completed setup combines the Arduino, motor driver, encoder motor, and power supply.

![Final Setup](images/final-setup.jpg)

---

## Project Structure

```text
PID-Motor-Speed-Controller/
│
├── README.md
│
├── firmware/
│   └── PID_Motor_Controller.ino
│
├── hardware/
│   ├── schematic.pdf
│   │
│   └── kicad/
│       ├── PID_Motor_Controller.kicad_pro
│       ├── PID_Motor_Controller.kicad_sch
│       └── PID_Motor_Controller.kicad_pcb
│
└── images/
    ├── breadboard.jpg
    ├── serial-monitor.png
    ├── schematic.png
    ├── pcb-layout.png
    ├── pcb-3d.png
    └── final-setup.jpg
```

---

## What I Learned

Through this project, I gained experience with:

- Arduino programming in C++
- PID control
- Encoder feedback
- PWM motor control
- DC motor drivers
- Breadboard prototyping
- Circuit design
- KiCad schematic design
- PCB design
- Hardware testing and debugging

---

## Future Improvements

- Convert encoder counts to RPM
- Continue improving PID tuning
- Test the controller at different target speeds
- Test the motor under different loads
- Manufacture and test the custom PCB

---

## Tools and Technologies

`Arduino` `C++` `PID Control` `PWM` `Encoders` `Motor Control` `KiCad` `PCB Design` `Circuit Design`
