# 👋 Welcome to Week 2 – Task 1: Exploring SoC Design with VSDBabySoC

This repository documents my learning journey into **System on Chip (SoC) design fundamentals**, with a special focus on the **VSDBabySoC** — a compact, open-source SoC built on the RISC-V architecture. In this task, I explored how digital components, analog interfaces, and synchronization mechanisms come together to form a functional SoC. Below is a detailed summary of key concepts and how VSDBabySoC helped me understand them hands-on.

---

## 🚀 Understanding SoC Design Fundamentals

### 📘 What is a System on Chip (SoC)?

A **System on Chip (SoC)** is a complete computing system — including a processor, memory, input/output interfaces, and sometimes analog components — all packed into a **single chip**.

Unlike traditional systems that use separate components, an SoC combines everything into one integrated circuit. This makes devices **smaller, faster, more efficient, and lower in power consumption** — perfect for smartphones, wearables, IoT gadgets, and embedded systems.

### 🔑 Key Benefits of SoCs:
- ✅ **Compact** – Saves space in devices
- 🔋 **Power-efficient** – Uses less battery
- ⚡ **High-speed** – Faster data transfer internally
- 💰 **Cost-effective** – Fewer components to manufacture
- 🔧 **Reliable** – Fewer connections mean fewer failure points

---

## 🔧 SoC Design Flow – Step-by-Step

Understanding SoC design means knowing the full process from concept to chip:

1. **Requirement Specification** – What will the chip do?
2. **Architecture Design** – Choosing the right blocks (CPU, memory, I/O, etc.)
3. **RTL Design (Verilog/VHDL)** – Describing behavior in hardware code
4. **Functional Verification** – Simulating to check for correctness
5. **Synthesis** – Converting code to actual logic gates
6. **Physical Design** – Laying out parts on the chip
7. **DFT (Design for Testability)** – Adding logic to make testing easier
8. **Timing & Power Analysis** – Ensuring performance and efficiency
9. **Tape-out** – Sending the final design for manufacturing
10. **Fabrication, Testing & Packaging** – Making and validating the real chip

---

## 👶 Introduction to VSDBabySoC

As part of my learning journey, I explored **VSDBabySoC** — a minimal yet fully functional SoC based on **RISC-V**, designed for educational and test purposes.

### 🧩 Core Components of VSDBabySoC:

- **🧠 RVMYTH CPU (RISC-V Core):**  
  A simple open-source CPU that runs instructions and handles data processing. It uses register `r17` to hold values that are passed to the DAC.

- **⏱️ Phase-Locked Loop (PLL):**  
  Generates a **stable clock signal** to synchronize the entire system — ensuring that the CPU and DAC work together smoothly.

- **🎚️ 10-bit Digital-to-Analog Converter (DAC):**  
  Converts **digital data** from the CPU into **analog signals** — useful for output to devices like speakers, displays, or other analog electronics.

---

## 🔁 How VSDBabySoC Works

1. **Initialization:**  
   - The SoC receives an input signal.  
   - The **PLL** activates and generates a stable clock.

2. **Data Processing:**  
   - The **RVMYTH processor** cycles through data using the `r17` register.  
   - It prepares the digital values to be sent out.

3. **Analog Output:**  
   - The **DAC** receives these digital values and converts them into analog signals.  
   - These signals are saved in a file named `OUT` or sent to external devices like TVs or phones.

---

## 🎚️ DAC – Digital to Analog Converter (Simplified)

- **What it does:** Converts binary (digital) values into smooth analog voltages.
- **Input:** A series of bits (e.g., 10-bit = 1024 levels).
- **Output:** Continuous analog voltage.

### 🔧 Common Types of DACs:
- **Weighted Resistor DAC:** Uses resistors with values based on each bit’s weight.
- **R-2R Ladder DAC:** Uses a simple, repeating resistor structure — ideal for scalability and easier to design.

BabySoC uses a **10-bit DAC**, meaning it can represent **1024 levels** of analog output.

---

## 💡 What I Learned

Working with **VSDBabySoC** helped me understand key aspects of SoC development:

- ✅ RISC-V processor integration and CPU design
- ✅ Clock synchronization with PLLs
- ✅ Digital-to-analog data flow and peripheral integration
- ✅ SoC architecture planning and RTL design
- ✅ Real-world application: how small SoCs power large systems

---

## 📚 Conclusion

**VSDBabySoC** is more than just a simple chip — it’s a **complete learning platform**. It bridges the gap between digital logic, analog interfaces, and real-world system design. Through this task, I developed a deeper understanding of SoC architecture, open-source hardware, and the digital-to-analog pipeline that powers modern electronics.

I'm excited to continue exploring **RISC-V**, hardware design, and SoC innovation in upcoming tasks. 💻🔧

---

✅ *Thanks for reading! Explore the project files above to see how the internals work.*

