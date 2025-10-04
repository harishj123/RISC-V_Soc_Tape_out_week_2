
---

## 🧪 Task 2 – Pre-Synthesis Simulation of VSDBabySoC

### 👋 Welcome to Task 2!

In this lab, we perform a **pre-synthesis simulation** of the `VSDBabySoC` design using **Icarus Verilog** and visualize the waveforms with **GTKWave**. This step helps verify functional correctness before moving to synthesis.

---

### 🔧 Steps Performed

```bash
# Navigate to project directory
cd ~/Desktop/VLSI/VSDBabySoC

# clone git
git clone https://github.com/manili/VSDBabySoC.git

```

![image alt](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/command_1.png?raw=true)

```bash

# Step 1: Install python3-venv 
sudo apt update
sudo apt install python3-venv python3-pip

# Step 2: Create and activate a virtual environment
cd ~/VLSI/VSDBabySoC/
python3 -m venv sp_env
source sp_env/bin/activate

# Step 3: Install SandPiper-SaaS inside the virtual environment
pip install pyyaml click sandpiper-saas

# Step 4: Convert rvmyth.tlv to Verilog
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/

```

![image alt](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/command_2.png?raw=true)


# Pre-Synthesis Simulation

```bash
# change directory
cd VLSI/VSDBabySoC/src/module

# iverilog
 iverilog \ -o /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out \ 
-DPRE_SYNTH_SIM \
-I /home/username/Desktop/VLSI/VSDBabySoC/src/include \
-I /home/username/Desktop/VLSI/VSDBabySoC/src/module \
/home/username/Desktop/VLSI/VSDBabySoC/src/module/testbench.v

# move directory
mkdir -p /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim

# To confirm iverilog worked properly
ls -l /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out

# VCD Waveform is created
vvp /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out

# gtkwave
gtkwave pre_synth_sim.vcd

```
![image alt](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/vsdbabysoc_tb_gtkwave.png?raw=true)

We can observe that the **REF** signal is a consistent clock, while the **OUT** signal is toggling at a different frequency, indicating active behavior from the SoC's output logic. The **reset** signal remains low, meaning the system is operating normally (not in reset). `ENb_VCO` is high (disabled), and `ENb_CP` is undefined (`x`), which may affect charge pump activity. The analog reference `VREFH` is held at 3.3V, while `VREFL` remains at 0V, as expected. Overall, the simulation shows stable operation of the digital and analog control signals under normal (non-reset) conditions.


## The DAC output

![image alt](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/dac_gtkwave.png?raw=true)

From this waveform, we can observe the behavior of signals inside the **DAC (Digital-to-Analog Converter)** block of the `vsdbabysoc_tb` testbench. The digital inputs `D[9:0]` and `Dext[10:0]` are changing values over time, indicating active digital data being fed into the DAC. The **`EN`** signal is high (`=1`), which means the DAC is enabled. The analog output signal **`OUT`** shows varying real values (e.g., `0.396`, `0.369`, `0.343`), confirming that the DAC is converting the digital input into a corresponding analog voltage. The reference voltages are correctly set, with **`VREFH` = 1** and **`VREFL` = 0**. Overall, the waveform shows the DAC is functioning correctly, converting digital codes to analog output when enabled.


## To get analog output

```bash
Right click -> Out in waveform
click Data format -> analog ->step
```

![image alt](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/analog_gtkwave.png?raw=true)

The above waveform shows the simulation of a DAC (Digital-to-Analog Converter) module. The digital inputs `D[9:0]` and `Dext[10:0]` are active and changing with time, while the enable signal `EN` is kept high (`1`), meaning the DAC is enabled. The reference voltages are set as `VREFH = 1` and `VREFL = 0`. The DAC output `OUT` is a real-valued signal that varies smoothly in a waveform pattern, converting the digital input values into an analog-like sinusoidal signal between 0 and 1. The presence of a `NaN` signal indicates an undefined or unused value in the testbench, but the important point is that the DAC is correctly generating an analog output corresponding to the digital inputs.

---

### 📈 Waveform Summary

* **ENb_CP** and **ENb_VCO** toggle during simulation, indicating active control logic.
* **REF** shows a stable reference clock.
* **OUT** toggles periodically, indicating system response.
* **reset** remains low (inactive), allowing normal operation.
* **VREFH** is steady at 3.3V, and **VREFL** stays low.

The simulation ends successfully with `$finish`, confirming that the design runs as expected.

---

### ✅ Conclusion

This task demonstrates a successful pre-synthesis simulation of the VSDBabySoC. Key signals are behaving correctly, and the waveform confirms that the design is functionally active and stable.

---
