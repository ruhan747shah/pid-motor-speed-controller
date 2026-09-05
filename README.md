# PID Motor Speed Controller

I built a PID motor speed controller using an Arduino Uno, a TB6612FNG motor driver, and a 6 V DC motor with an encoder. I first built and tested the circuit on a breadboard, then created the schematic and PCB in KiCad.

The encoder is used to measure the motor speed, and the Arduino adjusts the PWM output based on the PID calculation.

## Hardware

| Component | Purpose |
|---|---|
| [MECCANIXITY 6 V DC Gear Motor with Encoder](https://www.amazon.ca/MECCANIXITY-Encoder-Gearbox-Electric-Reduction/dp/B0F8NH1M4Z/) | Motor and encoder |
| [TB6612FNG Motor Driver](https://www.amazon.ca/Hyuduo-Motors-Driver-Controller-TB6612FNG/dp/B09PGJ8J8K/) | Motor driver |
| Arduino Uno R3 | Runs the controller |
| [2.1 mm DC Jack](https://www.amazon.ca/2-1mm-Screw-Terminal-Power-Connector/dp/B07MQTCZBG/) | Power connection |
| [Breadboard](https://www.amazon.ca/Breadboard-Solderless-Prototype-Distribution-Connecting/dp/B01EV6LJ7G/) | Prototyping |
| 7.5 V Battery Pack | Motor power |

## Breadboard Prototype

I started by getting the motor running through the TB6612FNG and then connected the encoder for speed feedback.

![Breadboard Setup](images/breadboard.jpg)

## PID Control

The Arduino reads the encoder every 100 ms and uses the change in encoder counts to measure the motor speed.

I set a target speed and calculate the difference between the target and measured speed. The PID controller uses this error to change the PWM output from 0 to 255.

The three PID values I used are:

```cpp
float kp = 0.5;
float ki = 0.05;
float kd = 0.01;
```

I tested different values while watching the speed and PWM output in the Serial Monitor.

### Serial Monitor

![Serial Monitor](images/serial-monitor.png)

## Arduino Code

The main code is located in:

`firmware/PID_Motor_Controller.ino`

The main loop handles the encoder reading, PID calculation, and PWM output to the motor driver.

## Schematic

Once the breadboard circuit was working, I recreated the same connections in KiCad.

![KiCad Schematic](images/schematic.png)

The schematic PDF is also available in:

`hardware/schematic.pdf`

## PCB

I used the schematic to design a custom PCB for the circuit.

![PCB Layout](images/pcb-layout.png)

### 3D View

![PCB 3D View](images/pcb-3d.png)

The KiCad files are in:

`hardware/kicad/`

## Final Setup

![Final Setup](images/final-setup.jpg)

## What I Learned

This project helped me learn more about PID control, encoder feedback, PWM motor control, and using a motor driver with an Arduino. It was also my first time taking a working breadboard circuit and turning it into a schematic and PCB in KiCad.

## Project Files

```text
PID-Motor-Speed-Controller/
├── firmware/
│   └── PID_Motor_Controller.ino
├── hardware/
│   ├── schematic.pdf
│   └── kicad/
└── images/
    ├── breadboard.jpg
    ├── serial-monitor.png
    ├── schematic.png
    ├── pcb-layout.png
    ├── pcb-3d.png
    └── final-setup.jpg
```
