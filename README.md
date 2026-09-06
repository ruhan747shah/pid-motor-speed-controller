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

### 1. Breadboard Prototype

![Breadboard Prototype](images/breadboard.jpg)

*Initial breadboard setup used to test the Arduino, motor driver, motor, and encoder.*

### 2. Serial Monitoring

![Serial Monitor](images/serial-monitor.png)

*Motor speed, target speed, and PWM output displayed while tuning the PID controller.*

### 3. The Schematic

![Schematic](images/schematic.png)

*KiCad schematic based on the tested breadboard circuit.*

### 4. The PCB

![PCB Layout](images/pcb-layout.png)

*Custom PCB layout designed in KiCad for the motor control circuit.*

### 5. PCB 3D View

![PCB 3D View](images/pcb-3d.png)

*3D view of the PCB design.*


## PID Control

The Arduino reads the motor encoder and compares the measured speed with a target speed. The PID controller then adjusts the PWM output sent to the TB6612FNG motor driver.

The PID values used during testing were:

```cpp
float kp = 0.5;
float ki = 0.05;
float kd = 0.01;
