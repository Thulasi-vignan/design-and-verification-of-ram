# 🚀 RAM Design and Verification using SystemVerilog

This project implements a 16x8-bit synchronous RAM in Verilog and verifies it using a modular SystemVerilog testbench with class-based components. It is suitable for beginners and intermediate learners aiming to understand functional verification using mailbox-based communication and DUT interaction.

---

## 🧠 Design Overview

### 📂 Module: `ram.v`

**Ports:**
- `input clk, rst, enb, wr, rd` — Control signals  
- `input [4:0] w_addr, r_addr` — Write/Read address  
- `input [7:0] w_data` — Data to write  
- `output reg [7:0] r_data` — Output read data  

**Behavior:**
- Memory size: `16 x 8-bit`  
- Reset (`rst=0`) initializes memory to `8'bx`  
- If `enb=1`:  
  - `wr=1, rd=0` → Write  
  - `wr=0, rd=1` → Read  
  - `wr=1, rd=1` → Write and Read simultaneously  
  - `wr=0, rd=0` → No operation

---

## 🧪 Verification Environment (SystemVerilog)

### ✅ Testbench Structure:
- `interface.sv` — Shared signals  
- `transaction.sv` — Transaction object  
- `generator.sv` — Generates test inputs  
- `driver.sv` — Drives DUT through interface  
- `monitor.sv` — Monitors outputs from DUT  
- `scoreboard.sv` — Checks DUT outputs against expected values  
- `environment.sv` — Connects and runs all components  
- `testbench.sv` — Top-level module

### 📦 Stimuli:
- Write-only
- Read-only
- Write-then-Read (Read-After-Write)
- Invalid operations (optional extension)

---



