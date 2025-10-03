
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
vvp /home/harish/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out

# gtkwave
gtkwave pre_synth_sim.vcd

```
![image alt](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/vsdbabysoc_tb_gtkwave.png?raw=true)

## The DAC output

![image alt](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/dac_gtkwave.png?raw=true)

## To get analog output

```bash
Right click -> Out in waveform
click Data format -> analog ->step
```

![image alt](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/analog_gtkwave.png?raw=true)

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

Let me know if you’d like this saved as a `.md` file!
