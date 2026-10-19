# 🚀 Affan - RTL Design & FPGA

<div align="center">

![Header](https://raw.githubusercontent.com/platane/snk/output/github-contribution-grid-snake-dark.svg)

<h3>🛰️ Verilog | SystemVerilog | Vivado | Functional Verification</h3>

*"A passing waveform is not a passing design. The checker, the golden model, and the timing report have to agree."*

[![GitHub followers](https://img.shields.io/github/followers/AffanMhz?label=Followers&style=social)](https://github.com/AffanMhz)
[![LinkedIn](https://img.shields.io/badge/-LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/affan-danish-08a144353/)
[![Twitter](https://img.shields.io/badge/-Twitter-1DA1F2?style=flat&logo=twitter&logoColor=white)](https://x.com/AffanMhz)
[![Email](https://img.shields.io/badge/-Email-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:affan2304788@st.jmi.ac.in)


</div>

---

## 👨‍🚀 About Me

I'm an **Electronics and Communication** student at Jamia Millia Islamia, pointed at **RTL design and FPGA**. I write synchronous datapaths and control FSMs in Verilog and SystemVerilog, check them with a testbench or a Python golden model, and read the Vivado post-route report before I call a block done.

I interned as an embedded engineer at Flywheel Aerospace (Oct 2024 to May 2026) and did research at IIT Delhi's MDIT Lab (SeNSE) in 2026. I lead the tech team of IEEE JMI. The CubeSat ADCS work and the IIT Delhi ranging debug are still here. Both were a wrong number chased down to the cycle that produced it. That is the same job as a failing testbench.

```python
class RtlDesigner:
    def __init__(self):
        self.name = "Affan"
        self.focus = "RTL design and functional verification"
        self.core_skills = ["Verilog", "SystemVerilog", "Vivado", "Python golden models"]
        self.philosophy = "If the hex files differ by one word, the test fails"

    def current_projects(self):
        return [
            "INT8 MAC and 4x4 dense layer, bit-exact against Python",
            "RV32I single-cycle CPU, ModelSim",
            "9x9 maze explorer FSM, explore then shortest exit",
            "Basys 3 clock, stopwatch, and alarm (FSM, XDC, UART)",
        ]
```

---

## 🛠️ Technical Arsenal

<div align="center">

### 🔧 HDL and FPGA
![Verilog](https://img.shields.io/badge/-Verilog-1C3A6E?style=flat)
![SystemVerilog](https://img.shields.io/badge/-SystemVerilog-0B3D91?style=flat)
![Vivado](https://img.shields.io/badge/-Xilinx_Vivado-E31C23?style=flat)
![Artix7](https://img.shields.io/badge/-Artix--7-333333?style=flat)

### 🐍 Verification and scripting
![Python](https://img.shields.io/badge/-Python-3776AB?style=flat&logo=Python&logoColor=white)
![Icarus](https://img.shields.io/badge/-Icarus_Verilog-555555?style=flat)
![ModelSim](https://img.shields.io/badge/-ModelSim-0077C8?style=flat)
![C++](https://img.shields.io/badge/-C++-00599C?style=flat&logo=c%2B%2B&logoColor=white)

### 🚀 Still on the bench
![STM32](https://img.shields.io/badge/-STM32-03234B?style=flat&logo=stmicroelectronics&logoColor=white)
![SPI](https://img.shields.io/badge/-SPI_%7C_I2C_%7C_UART-444444?style=flat)
![KiCad](https://img.shields.io/badge/-KiCad-314CB0?style=flat)
![MATLAB](https://img.shields.io/badge/-MATLAB-0076A8?style=flat&logo=mathworks&logoColor=white)

</div>

---

## 🌟 Featured Projects

### 🛰️ INT8 MAC and 4x4 dense layer
**Golden-model verification, then two microarchitectures in Vivado**

> The testbench prints a pass only when every output word matches the Python integer model.

- **🎯 Design**: Signed INT8 multiply-accumulate (16-bit product, 32-bit accumulator), a 4-tap ReLU neuron, and a 4x4 layer in SystemVerilog.
- **🔬 Verification**: Directed corners (`-128 * 127`, `-128 * -128`, ReLU clamp) plus 10,000 random vectors. 40,000 outputs, **0 mismatches**.
- **⚙️ Implementation**: Artix-7 `xc7a35tcpg236-1`, 10 ns constraint, out-of-context.
- **📊 Result**: Parallel maps to **16 DSP48E1**, 1-cycle compute, Fmax **57.4 MHz** (four DSPs in series on the critical path). Folded maps to **1 DSP48E1** and a 17-cycle FSM, Fmax **90.9 MHz**. Neither netlist meets 100 MHz. That miss is part of the result.

**Technologies**: `SystemVerilog` `Python` `Vivado` `Icarus Verilog` `DSP48E1`

---

### 🖥️ RV32I single-cycle CPU
**Datapath and control, checked in ModelSim**

> Every instruction finishes in one clock: fetch, decode, execute, memory, write-back.

- **🎯 Design**: Program counter, instruction memory, 32×32 register file, immediate generator, ALU, data memory, and a split control unit (main decoder and ALU decoder).
- **🔬 What it runs**: RV32I integer ops, loads and stores, branches, and jumps. Control mapping is the usual one: `lw` writes from memory, `sw` asserts MemWrite, `beq` redirects on Zero, `jal` writes PC+4.
- **📊 Verification**: A cycle-accurate testbench ran a RISC-V assembly program. ALU results, register writes, memory, and PC updates were checked in ModelSim. There is no synthesis or Fmax number for this core.

**Technologies**: `Verilog` `RV32I` `Datapath` `Control unit` `ModelSim`

---

### 🧭 9×9 maze explorer
**One FSM explores, then takes the exit**

> Unknown maze. Three wall sensors. Five move commands.

- **🎯 Design**: Dual-mode Verilog FSM. Explore mode marks cells in a weight matrix. Exit mode follows that matrix. One counter covers boot delay, dead-ends, and the mode switch. Moves are stop, forward, left, right, and u-turn.
- **🔬 Verification**: ModelSim run of a full explore-and-exit on the maze in the testbench. Fixed 9×9 grid. No timing report.

**Technologies**: `Verilog` `FSM` `ModelSim`

---

### ⏱️ Digital clock, stopwatch, and alarm
**Multi-clock RTL on a Basys 3**

> Milliseconds, a lap timer, and an alarm, on a 4-digit display and a UART line.

- **🎯 Design**: BCD timebase, stopwatch FSM (`IDLE / RUN / LAP / STOP`), alarm FSM, multiplexed 7-segment scan, 8N1 UART at 115200 baud.
- **⚡ Clocking**: Clocking Wizard divides 100 MHz into 20 MHz (datapath and UART) and 10 MHz (debounce and display). The time bus crosses with a toggle handshake.
- **📡 Constraints**: XDC for package pins, LVCMOS33, and a 10 ns primary clock.
- **🔬 Verification**: 11 self-checking testbenches for FSM arcs, UART bit timing, debounce, and the top-level alarm path.

**Technologies**: `Verilog` `FSM` `XDC` `Clocking Wizard` `UART` `CDC`

---

### ⚙️ Sensor interface FSMs
**Pulse-width measurement and a checksummed sensor read**

- **🎯 Design**: Timing-accurate Verilog FSMs for an ultrasonic ranger and a digital temperature-humidity sensor.
- **🔬 Verification**: RTL simulation on a 50 MHz clock, including the checksum check.

**Technologies**: `Verilog` `FSM` `RTL simulation`

---

### 🛰️ [CubeSat ADCS testbed](https://github.com/AffanMhz/Learn_Sat_basics)
**Earlier work, still the best debug story I had before RTL**

> Yaw drift, then a timestamp mixed across cycles. Same habit as a failing testbench.

- **🎯 What it was**: Yaw estimation and PD stabilization with an MPU-9250, complementary / Madgwick / Mahony filters, and LoRa telemetry.
- **⚡ Result**: Yaw drift went from about 5-10°/min to under 0.05°/min after the filter and the magnetometer path were fixed.
- **🔬 Same kind of chase**: At IIT Delhi, a DW1000 timestamp mixed across cycles (`DX_TIME`) took a thousands-of-metres ranging error back to sub-metre.

**Technologies**: `IMU` `LoRa` `STM32` `SPI` `Python logs`

---

## 🧑‍💼 Experience, Training and Leadership

### Experience

- **Research Intern, IIT Delhi, MDIT Lab (SeNSE)** (May to Aug 2026): wrote a register-level DW1000 SPI driver (RF configuration, CPLOCK-gated dual-speed SPI), ran SS-TWR/DS-TWR ranging on an STM32, traced a thousand-metre ranging error to timestamps mixed across cycles (fixed with delayed transmission on `DX_TIME`), and fused BNO055 IMU data with ZUPT dead-reckoning, validated with Python logs.
- **Embedded System Engineer Intern, Flywheel Aerospace** (Oct 2024 to May 2026): C/C++ firmware on ESP32 and STM32 for several robotics projects (sensors, motors, encoders, displays), plus a nanosatellite On-Board Computer (OBC): peripheral interfacing, sensor and communication integration, data handling, and hardware/firmware testing.
- **India Space Lab, Summer Internship and Technical Training** (online, 17 Jun to 31 Jul 2026): drone technology, CanSat/CubeSat, remote sensing and GIS, rocketry. Submitted reports on PID tuning for drone altitude and autonomous navigation (Python), a CanSat ground-control dashboard, and a SimScale structural analysis of a rocket fin.

### Training and leadership

- **Workshop trainer, Jamia Millia Islamia**: appointed trainer for two official workshops, Robotics and Drone Technology & Flight Training. Before that, 6 months of drone flight training at [Bamboo Copter](https://bamboocopter.in/about-us/).
- **Tech Team Head, IEEE JMI.**
- **Captain, Department Volleyball Team.**

---

## 📈 GitHub Analytics

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=AffanMhz&show_icons=true&theme=radical&hide_border=true&bg_color=0D1117&title_color=F85D7F&icon_color=F8D866)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=AffanMhz&layout=compact&theme=radical&hide_border=true&bg_color=0D1117&title_color=F85D7F)

![GitHub Streak](https://github-readme-streak-stats.herokuapp.com/?user=AffanMhz&theme=radical&hide_border=true&background=0D1117&stroke=F85D7F&ring=F85D7F&fire=F8D866&currStreakLabel=F8D866)

</div>

---

## 🌌 A few things that are actually true

- **🔴** The parallel INT8 layer uses 16 DSP48E1 and is slower than the folded layer with 1 DSP. Four DSPs in series lost to a shorter path.
- **🛰️** I can say what failed: both netlists miss a 10 ns clock. 57.4 MHz and 90.9 MHz are the measured Fmax values, not a timing-closed design.
- **⚡** A test passes only when the hex matches the Python model. 10,000 vectors, 40,000 outputs, 0 mismatches.
- **📡** The 72-hour gyroscope story was real. The fix was calibration, not a new algorithm.
- **🔧** I still track the ISS. The job I am applying for now is RTL, a testbench, or a timing report.

---

## 🎯 What I am doing now

```python
mission_goals = {
    "rtl": [
        "Pipeline the parallel INT8 neuron so Fmax is not stuck on four DSPs in series",
        "Move weights out of DONT_TOUCH registers and into a load path",
        "Add a second clock-domain design with an explicit synchronizer and a failing case",
    ],
    "verification": [
        "Keep a golden model next to every datapath, not only a waveform",
        "Learn assertion checks on the FSMs I already have",
    ],
    "looking_for": [
        "An internship in RTL design or FPGA verification",
    ],
}
```

---

## 🚀 Let's connect

<div align="center">

I am looking for an internship where the work is RTL, a testbench, or a timing report. The satellite projects are real. They are not the job I am applying for now.

### 📬 Reach me
[![LinkedIn](https://img.shields.io/badge/-LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/affan-danish-08a144353/)
[![Email](https://img.shields.io/badge/-Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:affan2304788@st.jmi.ac.in)
[![Twitter](https://img.shields.io/badge/-Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://x.com/AffanMhz)

[![Contact Me](https://img.shields.io/badge/-Contact%20Me-blue?style=for-the-badge&logo=googleforms&logoColor=white)](https://forms.gle/Yiuq2CYsoSZvgQ1RA)

### 🌟 Current status
```
Currently working on: INT8 datapath, parallel vs folded, and the Basys 3 clock
Learning: setup/hold from real Vivado paths, not from a slide
Looking to collaborate on: RTL blocks with a checker, not a demo-only waveform
Ask me about: why 16 DSPs were slower than 1 DSP on that Artix-7 netlist
```

</div>

---

<div align="center">

![Footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=100&section=footer&text=RTL%20first&fontSize=20&fontColor=ffffff)

**Thanks for reading.**

</div>
