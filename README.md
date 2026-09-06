# PID Motor Speed Controller

A DC motor speed controller using an Arduino Uno, TB6612FNG motor driver, and a 6 V encoder motor. Built and tested on a breadboard, then recreated as a schematic and custom PCB in KiCad.

## Materials

- 1x [ELEGOO Uno R3](https://www.amazon.ca/Elegoo-Board-ATmega328P-ATMEGA16U2-Arduino/dp/B01EWOE0UU/)
- 1x [MECCANIXITY 6 V DC Gear Motor with Encoder](https://www.amazon.ca/MECCANIXITY-Encoder-Gearbox-Electric-Reduction/dp/B0F8NH1M4Z/)
- 1x [TB6612FNG Motor Driver Module](https://www.amazon.ca/Hyuduo-Motors-Driver-Controller-TB6612FNG/dp/B09PGJ8J8K/)
- 1x [2.1 mm DC Jack Screw Terminal](https://www.amazon.ca/2-1mm-Screw-Terminal-Power-Connector/dp/B07MQTCZBG/)
- 1x [Solderless Breadboard](https://www.amazon.ca/Breadboard-Solderless-Prototype-Distribution-Connecting/dp/B01EV6LJ7G/)
- 1x [5x AA Battery Holder](https://www.amazon.ca/LampVPath-Battery-Holder-Leads-Wires/dp/B07WRQ44YK/)
- [Jumper Wires](https://www.amazon.ca/2-54mm-Dupont-Jumper-Cables-Female/dp/B09SXM64Z8/)
- 5x AA Batteries

## Project Gallery

## Wiring

### Power

| From | To |
|---|---|
| Arduino 5V | Breadboard (+) rail |
| Arduino GND | Breadboard (-) rail |

### Battery

| From | To |
|---|---|
| Battery + | Driver VM |
| Battery - | Driver GND / common ground |

### TB6612FNG Motor Driver

| Driver Pin | Arduino Connection |
|---|---|
| VCC | 5V breadboard rail |
| GND | GND breadboard rail |
| STBY | Pin 9 |
| AIN1 | Pin 8 |
| AIN2 | Pin 7 |
| PWMA | Pin 6 |

### Motor

| Motor Wire | Driver Pin |
|---|---|
| M1 (white) | AO1 |
| M2 (red) | AO2 |

### Encoder

| Encoder Wire | Arduino Connection |
|---|---|
| VCC (black) | 5V breadboard rail |
| GND (purple) | GND breadboard rail |
| C1 (green) | Pin 2 |
| C2 (orange) | Pin 12 |

## 1. PID Control

The Arduino reads the motor encoder and compares the measured speed with a target speed. The PID controller then adjusts the PWM output sent to the TB6612FNG motor driver.

The PID values used during testing were:

```cpp
float kp = 0.5;
float ki = 0.05;
float kd = 0.01;
```

### 2. Serial Monitoring

Motor speed, target speed, and PWM output were monitored through the Arduino Serial Monitor while testing and tuning the PID controller.

Example output:

```text
Speed: 1980 | Target: 2100 | PWM: 146
Speed: 2050 | Target: 2100 | PWM: 137
Speed: 2080 | Target: 2100 | PWM: 131
Speed: 2110 | Target: 2100 | PWM: 126
Speed: 2090 | Target: 2100 | PWM: 129
```

*Example format of the Serial Monitor output during PID testing.*

## Circuit Design

### 3. The Schematic

![Schematic](images/Screenshot%202026-09-05%20204639.png)

*KiCad schematic based on the tested breadboard circuit.*

### 4. The PCB

![PCB Layout](images/Screenshot%202026-09-05%20205500.png)

*Custom PCB layout designed in KiCad for the motor control circuit.*

### 5. PCB 3D View

![PCB 3D View](images/Screenshot%202026-09-05%20210238.png)

*3D view of the PCB design.*

## Skills Learned

- PID control and tuning
- Encoder feedback and motor speed measurement
- PWM motor control
- Arduino programming in C++
- TB6612FNG motor driver interfacing
- Breadboard prototyping and circuit testing
- Schematic design in KiCad
- 4-layer PCB design and routing
- Hardware debugging and testing
