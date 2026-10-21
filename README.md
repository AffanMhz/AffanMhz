<div align="center">

# Affan Danish

### Embedded Systems · Robotics · Aerospace · RTL/FPGA · Sensor Fusion

I build systems that connect **physical hardware, firmware, digital logic and data**.

<p>
  <a href="https://github.com/AffanMhz"><img src="https://img.shields.io/badge/GitHub-AffanMhz-181717?style=for-the-badge&logo=github"></a>
  <a href="https://www.linkedin.com/in/affan-danish-08a144353/"><img src="https://img.shields.io/badge/LinkedIn-Affan%20Danish-0A66C2?style=for-the-badge&logo=linkedin"></a>
  <a href="mailto:danishaffan678@gmail.com"><img src="https://img.shields.io/badge/Email-Contact%20me-EA4335?style=for-the-badge&logo=gmail"></a>
  <a href="https://affan-danish-embedded.netlify.app/"><img src="https://img.shields.io/badge/Embedded%20Portfolio-0F766E-222222?style=for-the-badge&logo=netlify"></a>
  <a href="https://affan-danish-digital-fpga.netlify.app/"><img src="https://img.shields.io/badge/RTL%20%2F%20FPGA%20Portfolio-0E7490-222222?style=for-the-badge&logo=netlify"></a>
</p>

<p>
  <img src="https://img.shields.io/badge/Verilog%20%7C%20SystemVerilog-RTL%20Design-1C3A6E?style=flat-square">
  <img src="https://img.shields.io/badge/STM32%20%7C%20ESP32-Firmware-03234B?style=flat-square">
  <img src="https://img.shields.io/badge/UWB%20%7C%20IMU-Localization-6A1B9A?style=flat-square">
  <img src="https://img.shields.io/badge/Drones%20%7C%20Satellites-Aerospace-0B6623?style=flat-square">
</p>

</div>

---

## Who I am

I am an Electronics and Communication Engineering student at **Jamia Millia
Islamia, New Delhi**, working across embedded systems, robotics, aerospace
electronics and digital hardware.

My work has ranged from writing register-level drivers for a DW1000 UWB
transceiver at **IIT Delhi's MDIT Lab (SeNSE)** to building STM32/ESP32
robotics systems at **Flywheel Aerospace**, validating an Arduino-based
one-axis ADCS testbed, and designing RTL datapaths and processors for FPGA.

I care about the boundary between an idea and a working system:

- a sensor driver that survives real timing and bus constraints;
- a ranging system that works in a GPS-denied environment;
- an attitude-estimation loop whose drift can be measured and explained;
- an RTL block whose checker, waveform and timing report agree;
- a workshop where students learn by assembling, testing and debugging real hardware.

> **A demo is the beginning. A measured, repeatable and explainable system is the result.**

---

## Engineering focus

| Area | What I work on |
|---|---|
| **Embedded firmware** | STM32, ESP32, Arduino, Embedded C/C++, HAL, bare-metal drivers, interrupts, timers, PWM, ADC and watchdog-oriented systems |
| **Interfaces and buses** | SPI, I2C, UART, GPIO, Bluetooth, Wi-Fi, ESP-NOW, LoRa, ELRS and serial telemetry |
| **Localization and sensing** | DW1000/DWM1000 UWB ranging, GPS-denied positioning, magnetic-induction positioning, IMUs, barometers, GPS and sensor fusion |
| **Robotics** | Motors, encoders, servo control, obstacle avoidance, line following, wireless control, actuator integration and field debugging |
| **Aerospace systems** | One-axis ADCS, CubeSat concepts, nanosatellite OBC documentation, telemetry, drones, CanSat, rocketry and mission systems |
| **RTL and FPGA** | Verilog, SystemVerilog, FSMs, datapaths, RV32I, FPGA prototyping, UART, CDC, XDC constraints and timing analysis |
| **Verification and analysis** | Self-checking testbenches, Python golden models, randomized vectors, serial logging, plotting, MATLAB-style analysis and hardware validation |

---

## Current RTL philosophy — in Verilog, not Python

```systemverilog
module design_is_not_done;
    logic checker_passed, timing_closed, hardware_validated;
    logic design_complete;

    assign design_complete = checker_passed
                           && timing_closed
                           && hardware_validated;

    // A waveform that looks correct is evidence, not a proof.
endmodule
```

For firmware and hardware, I follow the same rule:

```systemverilog
always_ff @(posedge clk) begin
    if (rst) begin
        state <= IDLE;
    end else begin
        state <= next_state;
    end
end

assert property (@(posedge clk) disable iff (rst)
    state != ERROR |-> ##1 valid_output);
```

---

## Experience

### Research Intern — MDIT Lab, SeNSE, IIT Delhi
**May–August 2026 · Embedded systems, UWB localization and sensor fusion**

- Implemented a register-level **DW1000/DWM1000 SPI driver** on STM32G070RB.
- Worked through RF initialization, register/sub-register addressing and
  CPLOCK-gated dual-speed SPI operation.
- Implemented and debugged **SS-TWR/DS-TWR** ranging using the
  POLL–RESPONSE–FINAL exchange.
- Traced a kilometre-scale ranging failure to timestamps being mixed across
  transmission cycles and corrected delayed-transmission timing through
  `DX_TIME`.
- Integrated a BNO055 IMU and worked on IMU-based ZUPT dead reckoning.
- Built Python serial-logging and plotting workflows for repeatable analysis.
- Studied UWB and magnetic-induction approaches for localization in
  GPS-denied drone and robotics environments.

### Embedded Systems Engineer (part-time) — Flywheel Aerospace
**October 2024–May 2026 · Robotics, aerospace electronics and firmware**

- Developed and tested C/C++ firmware for ESP32, STM32 and Arduino-based
  robotics and aerospace prototypes.
- Worked with sensors, motors, encoders, displays, wireless links and
  actuator-control systems.
- Contributed to nanosatellite **on-board computer (OBC)** documentation and
  a one-axis ADCS testbed.
- Built and debugged wireless communication paths over Bluetooth and Wi-Fi,
  moved to **ESP-NOW** for improved data rate, and later evaluated **LoRa**
  for long-range and efficient telemetry.
- Interfaced EMG sensors to control servo motors using hand gestures.
- Worked on educational robotics kits as well as real-world engineering
  prototypes, including client communication and technical explanation.
- Used STM32CubeIDE, STM32 HAL, Blue Pill and Nucleo boards, ST-LINK and
  practical hardware bring-up workflows.

### India Space Lab — Summer Internship and Technical Training
**June–July 2026 · Drones, satellites, remote sensing and rocketry**

- Studied drone technology, CanSat/CubeSat systems, remote sensing, GIS and
  rocketry.
- Worked on PID-based drone altitude control and autonomous navigation
  analysis in Python.
- Developed a CanSat ground-control dashboard concept.
- Performed a SimScale structural study of a rocket fin.
- Built wider working knowledge of orbiters, landers, Apollo missions,
  launch systems, rocket engines and mission architecture.

---

## Selected engineering work

### UWB two-way ranging and GPS-denied localization

An embedded ranging platform built around STM32 and a DW1000/DWM1000 UWB
module. The project combined register-level firmware, RF configuration, SPI
timing, two-way ranging, serial data capture and IMU-based motion analysis.

**Stack:** `Embedded C` `STM32G070RB` `DW1000` `SPI` `UART` `BNO055` `Python`

### One-axis ADCS testbed

A ground-based attitude-determination and control testbed using an Arduino
Nano, MPU-9250 IMU and LoRa telemetry. The work covered attitude sensing,
roll/pitch/yaw estimation, gyroscope integration, calibration, control-signal
generation and wireless telemetry.

I worked with complementary, Madgwick and Mahony-style estimation approaches
and investigated drift caused by calibration and magnetometer-path issues.

**Stack:** `Arduino Nano` `MPU-9250` `IMU` `ADCS` `PD control` `LoRa`

### INT8 MAC and 4×4 dense layer

SystemVerilog datapaths verified against a Python integer reference model.

- Signed INT8 multiplication with 16-bit products and 32-bit accumulation.
- Directed corner cases including `-128 × 127`, `-128 × -128` and ReLU clamp.
- 10,000 randomized vectors and 40,000 output comparisons with **0 mismatches**.
- Parallel implementation: 16 DSP48E1 blocks, one-cycle compute, 57.4 MHz Fmax.
- Folded implementation: one DSP48E1, 17-cycle FSM, 90.9 MHz Fmax.
- Both results missed the 100 MHz target; the timing miss is documented rather
  than hidden.

**Stack:** `SystemVerilog` `Python` `Vivado` `Icarus Verilog` `DSP48E1`

### RV32I single-cycle CPU

A Verilog CPU datapath with program counter, instruction memory, register
file, immediate generator, ALU, data memory, main decoder and ALU decoder.
The testbench exercised integer operations, loads, stores, branches and jumps
in ModelSim.

### Basys 3 digital clock, stopwatch and alarm

A multi-clock RTL system with BCD timekeeping, stopwatch states
(`IDLE`, `RUN`, `LAP`, `STOP`), alarm control, 7-segment multiplexing and an
8N1 UART at 115200 baud. The design includes XDC constraints, Clocking Wizard
outputs, debounce logic and a toggle-handshake crossing for the time bus.

### FPGA maze explorer

A dual-mode Verilog FSM that explores a 9×9 maze using wall sensors, stores
cell information and then computes an exit path. It handles dead ends,
intersection memory, coordinate tracking, backtracking and five movement
commands.

---

## Robotics, drones and wireless systems

My embedded work has included:

- motor drivers, encoders, servo motors and display interfaces;
- line-following and obstacle-avoidance robots;
- Bluetooth, Wi-Fi, ESP-NOW and LoRa telemetry;
- EMG-controlled gesture interfaces;
- IMU drivers and attitude estimation;
- GPS, barometer and multi-sensor integration;
- drone protocols and ecosystems including **ELRS**;
- drone flight and hands-on systems training;
- serial tools and **Serial Lab** for observing, logging and understanding
  real hardware communication.

---

## Workshop trainer and technical educator

### D.A.R.E. Workshop Series — Jamia Millia Islamia

I was selected as a trainer for two official **Drone and Robotics Electrical
(D.A.R.E.)** workshops organized by the Department of Electrical Engineering,
Faculty of Engineering and Technology, Jamia Millia Islamia.

1. **Arduino and Robotics Workshop** — practical electronics, Arduino,
   sensors, motor control, Bluetooth communication, assembly, debugging and
   robot testing.
2. **Drone Workshop** — drone fundamentals, components, flight systems,
   practical demonstrations and technical orientation.

The workshops were built around hands-on learning, trial-and-error debugging
and making students assemble and test systems themselves. Trainer feedback
was rated **4.71/5 for the first workshop** and **5/5 for the drone workshop**.

Feedback highlighted that I was well prepared, patient, engaging,
knowledgeable and willing to repeat explanations in English so students
from different language backgrounds could participate. Students specifically
mentioned clear explanations, calm implementation support and learning
through experimentation.

Learn more: [D.A.R.E. Workshop Series](https://www.linkedin.com/company/dare-workshop/)
· [Jamia Millia Islamia](https://www.linkedin.com/in/jmiofficial/)

### Bamboo Copter — six-month drone training

Completed approximately six months of hands-on drone training with
[Bamboo Copter](https://bamboocopter.in/about-us/), covering drone technology,
flight, systems, practical assembly and the wider drone ecosystem. Bamboo
Copter combines drone education, workshops, competitions and product
development to make drone technology more accessible.

---

## Leadership and communities

- **Head, Technical Team — IEEE JMI**
- **Trainer — D.A.R.E. Workshop Series, Jamia Millia Islamia**
- **Captain — Department Volleyball Team**
- Participant in hackathons and engineering challenges, including Hack JMI,
  Smart India Hackathon-related work and ISRO hackathon activities.
- In ISRO-related work, explored improving planetary-surface mapping using
  multiple data sources such as SAR and hyperspectral imagery with machine
  learning and data fusion concepts.

---

## Tools and technologies

<div align="center">

### Embedded and hardware

![C](https://img.shields.io/badge/C-00599C?style=flat-square&logo=c)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=flat-square&logo=cplusplus)
![STM32](https://img.shields.io/badge/STM32-03234B?style=flat-square&logo=stmicroelectronics)
![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=flat-square&logo=espressif)
![Arduino](https://img.shields.io/badge/Arduino-00979D?style=flat-square&logo=arduino)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=flat-square&logo=mathworks)

### Digital design

![Verilog](https://img.shields.io/badge/Verilog-1C3A6E?style=flat-square)
![SystemVerilog](https://img.shields.io/badge/SystemVerilog-0B3D91?style=flat-square)
![Vivado](https://img.shields.io/badge/Vivado-E31C23?style=flat-square)
![ModelSim](https://img.shields.io/badge/ModelSim-0077C8?style=flat-square)
![Icarus Verilog](https://img.shields.io/badge/Icarus%20Verilog-555555?style=flat-square)

### Interfaces, sensing and communications

`SPI` `I2C` `UART` `GPIO` `PWM` `ADC` `DMA` `UWB` `IMU` `GPS`
`Barometer` `Bluetooth` `Wi-Fi` `ESP-NOW` `LoRa` `ELRS`

</div>

---

## What I am building next

```verilog
module next_iteration;
    logic add_sva;
    logic close_timing;
    logic build_real_hil;
    logic improve_documentation;

    assign engineering_growth = add_sva
                              && close_timing
                              && build_real_hil
                              && improve_documentation;
endmodule
```

- Pipeline the parallel INT8 datapath and investigate the critical path.
- Add assertions, coverage and stronger randomized verification to existing
  RTL blocks.
- Build an explicit CDC/FIFO design with a reproducible failing case.
- Extend embedded work toward RTOS scheduling, DMA, CAN and hardware-in-loop
  validation.
- Keep turning aerospace and robotics ideas into measurable systems.

---

## Open to

- Embedded firmware and embedded systems roles
- Robotics and UAV systems
- Aerospace electronics, avionics and flight systems
- UWB, wireless localization and sensor-fusion research
- RTL design, FPGA and digital verification
- Hardware bring-up, validation and technical systems engineering
- Collaborations involving real hardware, a checker and a timing report

<div align="center">

### Let us build something that survives contact with hardware.

<a href="mailto:danishaffan678@gmail.com">Email</a> ·
<a href="https://www.linkedin.com/in/affan-danish-08a144353/">LinkedIn</a> ·
<a href="https://github.com/AffanMhz">GitHub</a> ·
<a href="https://affan-danish-embedded.netlify.app/">Embedded portfolio</a> ·
<a href="https://affan-danish-digital-fpga.netlify.app/">RTL / FPGA portfolio</a>

</div>
