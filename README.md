# Multiprogramming Operating System (MOS) Simulator in C++ ⚙️🖥️

A full C++ implementation of a simulated **Multiprogramming Operating System (MOS)** virtual hardware environment built across 3 distinct architectural phases: **Basic Execution**, **Virtual Memory & Interrupt Handling**, and **Multiprogramming with Spooling**.

---

## 📌 Architectural Phase Breakdown

### 🔹 Phase 1: Basic MOS Architecture & Execution
- **Core CPU Registers**: Instruction Register (`IR`), General Purpose Register (`R`), Instruction Counter (`IC`), Compare Flag (`C`).
- **Memory**: 100 blocks of 4 bytes each (`M[100][4]`).
- **Service Interrupts (`SI`)**:
  - `SI = 1`: Get Data (`GD` - Read input line into memory)
  - `SI = 2`: Put Data (`PD` - Write memory line to output)
  - `SI = 3`: Halt (`H` - Program termination)
- **Instruction Set**: `GD`, `PD`, `H`, `LR` (Load Register), `SR` (Store Register), `CR` (Compare Register), `BT` (Branch on True).

---

### 🔹 Phase 2: Virtual Memory, Paging & Interrupt Handling
- **Expanded Memory**: 300 blocks of 4 bytes (`M[300][4]`).
- **Page Table Register (`PTR`)**: Translates virtual addresses to physical frame addresses dynamically.
- **Process Control Block (`PCB`)**: Tracks `PID`, `TTL` (Total Time Limit), `TLL` (Total Line Limit), `TTC` (Time Counter), and `LLC` (Line Counter).
- **Expanded Interrupt Engine**:
  - **Time Interrupt (`TI`)**: Triggered when `TTC >= TTL` (Time limit exceeded).
  - **Program Interrupt (`PI`)**:
    - `PI = 1`: Operation Code Error
    - `PI = 2`: Operand Error
    - `PI = 3`: Page Fault (Handled via frame allocation or termination)

---

### 🔹 Phase 3: Multiprogramming, Spooling & Channel I/O
- **Supervisor Memory & Buffer Queues**: Manages `EmptyBuffers`, `InputFullBuffers`, and `OutputFullBuffers`.
- **Spooling System**: Asynchronous Input Spooling, Output Spooling, and Job Execution queues.
- **Channel Simulation**: Simulates concurrent I/O operations (Channel 1, Channel 2, Channel 3) between secondary storage (disk/drum) and main memory.

---

## 📜 Assembly Instruction Set

| Op-Code | Instruction | Description |
| :--- | :--- | :--- |
| `GD` | Get Data | Reads 40 bytes of input into specified memory address |
| `PD` | Put Data | Writes 40 bytes from specified memory address to output |
| `LR` | Load Register | Loads word from memory address into Register `R` |
| `SR` | Store Register | Stores word from Register `R` into memory address |
| `CR` | Compare Register | Compares word in Register `R` with memory content (Sets Flag `C`) |
| `BT` | Branch on True | Branches instruction counter to address if Flag `C` is true |
| `H`  | Halt | Terminates job execution |

---

## 🚀 How to Compile & Run

### Compiling Phase 1
```bash
cd phase1
g++ phase1.cpp -o phase1
./phase1
```

### Compiling Phase 2
```bash
cd phase2
g++ phase2.cpp -o phase2
./phase2
```

### Compiling Phase 3
```bash
cd phase3
g++ phase3.cpp -o phase3
./phase3
```

