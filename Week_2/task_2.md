Certainly! Here's a clean and professional version of your **Week 2 – Task 2 Practical Lab Session** report that you can include in your GitHub repository (e.g., in a `README.md` or `task2.md` file):

---

## 🧪 Week 2 - Task 2: Pre-Synthesis Simulation of VSDBabySoC

### 👋 Welcome to Task 2!

In this practical lab session, we simulate the `VSDBabySoC` design **before synthesis** using the open-source Verilog simulator **Icarus Verilog** and visualize the waveforms using **GTKWave**.

This task demonstrates how to:

* Compile a SystemVerilog testbench using `iverilog`
* Run the simulation using `vvp`
* View the output waveforms using `gtkwave`

---

### 🛠️ Step-by-Step Commands Used

```bash
# Step 1: Navigate to project directory
cd ~/Desktop/VLSI/VSDBabySoC

# Step 2: Create output directory (if not already created)
mkdir -p output/pre_synth_sim

# Step 3: Compile the testbench using Icarus Verilog
iverilog \
  -o output/pre_synth_sim/pre_synth_sim.out \
  -DPRE_SYNTH_SIM \
  -I src/include \
  -I src/module \
  src/module/testbench.v

# Step 4: Run the compiled simulation
vvp output/pre_synth_sim/pre_synth_sim.out

# Output:
# VCD info: dumpfile pre_synth_sim.vcd opened for output.
# testbench.v:63: $finish called at 84999000 (1ps)

# Step 5: View the waveform using GTKWave
gtkwave pre_synth_sim.vcd
```

---

### 📊 Waveform Description

The generated waveform (`pre_synth_sim.vcd`) shows the behavior of the `vsdbabysoc_tb` testbench. Key signals observed:

* **ENb_CP**, **ENb_VCO**: Toggle between 0 and 1, enabling/disabling charge pump and VCO blocks.
* **REF**: A regular clock signal used as a reference input.
* **OUT**: Output signal from the SoC; toggles less frequently than REF.
* **reset**: Remains low, indicating the system is not under reset.
* **VREFH**: Holds steady at 3.3V.
* **VREFL**: Remains low or unused in this run.

This confirms the SoC's control and clock signals are functioning correctly under pre-synthesis simulation.

---

### ✅ Conclusion

Task 2 successfully demonstrated how to compile, simulate, and analyze the VSDBabySoC design. The simulation ran without errors, and GTKWave helped visualize the expected signal transitions.

This simulation step is critical to verify the functional correctness of the design **before synthesis** and proceeding to the next stage of the VLSI design flow.

---

Let me know if you'd like me to help turn this into a Markdown file or upload format for your GitHub repo!

