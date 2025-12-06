# **1. Finite State Machines (FSMs)**

### **Moore vs Mealy**

* **Moore Machine:** Output depends *only on current state*.
  `Output = f(State)`
* **Mealy Machine:** Output depends on *state + inputs*.
  `Output = f(State, Input)`
* **Mealy reacts faster** because output changes immediately with input.

---

### **State Transition Table (STT) & Output Table**

* STT lists:
  `Present State | Input | Next State | Output`
* Use binary-encoded states (00, 01, 10, …) unless otherwise specified.

---

### **Boolean Equations for Next State & Output**

To derive:

1. Encode states.
2. Use next-state columns to write equations for each state bit.
   Example: `Q1⁺ = Q0·X + Q1·X'`
3. For outputs, use the output table:

   * Moore → outputs based on state encoding.
   * Mealy → outputs based on (state + input).

---

### **FSM Schematic**

* Blocks:

  1. **State registers** (Flip-flops holding Q bits)
  2. **Next-state logic** (combinational)
  3. **Output logic** (Moore → from Q; Mealy → from Q and input)

Diagram structure:

```
       +----------------+
Input →| Next-State     |→ D inputs of flip-flops
       | Logic          |
       +----------------+
              ↑
              | Q outputs
       +----------------+
       | State Register |
       +----------------+
              ↓
       +----------------+
       | Output Logic   |
       +----------------+
```

---

# **2. Waveforms for Sequential Circuits**

### **Sketching output from input waveforms**

* Track how outputs change **on the triggering clock edge**.
* Rising-edge triggered flip-flop: output updates at ↑ edges only.
* **D Flip-Flop:** `Q(next) = D (just before clock edge)`
* **JK Flip-Flop:**

  * J=0 K=0 → no change
  * J=0 K=1 → reset
  * J=1 K=0 → set
  * J=1 K=1 → toggle

---

### **Determining device from waveform**

Look for clues:

* **Transparent when clock high** → D latch
* **Updates only on edges** → Flip-flop
* **Output toggles** → likely T or JK with J=K=1
* **Output follows D directly except when disabled** → gated latch

---

# **3. Time & Delay / Clock Period / Frequency**

### **Clock relationships**

* **Clock period:** `T = 1 / f`
* **Frequency:** `f = 1 / T`
* **Propagation delay:** time for output to stabilize after input changes.
* **Setup time:** input must be stable *before clock edge.*
* **Hold time:** input must remain stable *after clock edge.*

Max safe clock frequency:

```
fmax = 1 / (t_pd + t_setup)
```

Clock period constraint:

```
Tmin = t_pd + t_setup
```

---

# **4. Memory Calculations**

### **Memory size formula**

```
Memory size (bits) = (Number of addresses) × (Data bits per address)
```

If address lines = *n*, then:

```
Number of addresses = 2^n
```

Example: 16 data bits, 10 address bits
→ size = 2¹⁰ × 16 = 16384 bits = 2 KB

---

# **5. Simple Verilog (similar to demos)**

### Essential Patterns

**D Flip-Flop**

```verilog
always @(posedge clk) begin
    Q <= D;
end
```

**Moore FSM skeleton**

```verilog
always @(posedge clk) state <= next_state;

always @(*) begin
    case (state)
        S0: begin next_state = S1; out = 0; end
        S1: begin next_state = S0; out = 1; end
    endcase
end
```

**Mealy FSM skeleton**

```verilog
always @(posedge clk) state <= next_state;

always @(*) begin
    case (state)
        S0: begin next_state = X ? S1 : S0; out = X & 1; end
    endcase
end
```

---

# ✅ **Practice Questions (One per Topic)**

### **FSM – Identify type**

**Q1:** Given a state diagram where arrows are labeled `(input/output)`, is it a Moore or Mealy machine?

---

### **FSM – Construct STT + Output Table**

**Q2:** An FSM has states A, B, C and input X. Transitions:

* A → B if X=0, else A
* B → C if X=1, else A
* C → C always
  Outputs: 1 only in state C.
  **Construct the full state transition and output table.**

---

### **FSM – Boolean Equations**

**Q3:** For the machine above encoded as A=00, B=01, C=10, derive Boolean equations for `Q1⁺` and `Q0⁺`.

---

### **FSM – Schematic**

**Q4:** Sketch a schematic for a 2-bit Moore FSM with states S0, S1, S2. Show registers + next-state logic.

---

### **Waveforms – Output Sketching**

**Q5:** Given a D flip-flop and input waveform D(t) and clock edges, sketch Q(t).

---

### **Waveforms – Identify Circuit Type**

**Q6:** A waveform shows output Q following input D only when CLK is high; otherwise Q holds.
**Which device is this?**

---

### **Clock / Delay**

**Q7:** A system has propagation delay 12 ns and setup time 3 ns.
**What is the maximum clock frequency?**

---

### **Memory Calculation**

**Q8:** A memory has 12 address bits and stores 32-bit words.
**Find total memory size in bytes.**

---

### **Verilog**

**Q9:** Write Verilog for a positive-edge triggered T flip-flop where T=1 toggles Q.

---

If you'd like, I can format this into a printable **one-page PDF**, **Google Doc**, or **two-sided cheat sheet**.
