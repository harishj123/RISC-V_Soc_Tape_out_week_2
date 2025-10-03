
---

## 🧪 Task 2 – Pre-Synthesis Simulation of VSDBabySoC

### 👋 Welcome to Task 2!

In this lab, we perform a **pre-synthesis simulation** of the `VSDBabySoC` design using **Icarus Verilog** and visualize the waveforms with **GTKWave**. This step helps verify functional correctness before moving to synthesis.

---

### 🔧 Steps Performed

```bash
# Navigate to project directory
cd ~/Desktop/VLSI/VSDBabySoC

# Create output directory for simulation
mkdir -p output/pre_synth_sim

# Compile the design and testbench
iverilog -o output/pre_synth_sim/pre_synth_sim.out \
  -DPRE_SYNTH_SIM \
  -I src/include \
  -I src/module \
  src/module/testbench.v

# Run the simulation
vvp output/pre_synth_sim/pre_synth_sim.out

# Open waveform in GTKWave
gtkwave pre_synth_sim.vcd
```

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
