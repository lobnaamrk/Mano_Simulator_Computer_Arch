# Mano Basic Computer Simulator

A browser-based simulator of the **Mano Basic Computer**, implemented entirely with **HTML, CSS, and JavaScript**.

The simulator reproduces the main functionality of the Mano Basic Computer architecture, including its instruction set, memory, registers, assembler, and fetch-decode-execute cycle.

## Features

* 🖥️ Interactive Mano Basic Computer simulator
* ⚙️ Step-by-step **Fetch → Decode → Execute** simulation
* ▶️ **Run All** mode for automatic execution
* 💾 Memory table with live register tracking
* 🔢 Two-pass assembler
* 🏷️ Support for labels and symbolic addresses
* 🔗 Direct and indirect addressing
* 📖 Micro-operation narration explaining each execution step
* 🎨 Interactive visual interface with phase indicators
* 🐰 Animated mascot and visual feedback
* 🎉 Completion animation when `HLT` is executed

## Supported Instruction Set

### Memory-Reference Instructions

| Instruction | Description                       |
| ----------- | --------------------------------- |
| `AND`       | AND AC with memory                |
| `ADD`       | Add memory value to AC            |
| `LDA`       | Load memory value into AC         |
| `STA`       | Store AC in memory                |
| `BUN`       | Branch unconditionally            |
| `BSA`       | Branch and save return address    |
| `ISZ`       | Increment memory and skip if zero |

### Register-Reference Instructions

| Instruction | Description              |
| ----------- | ------------------------ |
| `CLA`       | Clear AC                 |
| `CLE`       | Clear E                  |
| `CMA`       | Complement AC            |
| `CME`       | Complement E             |
| `CIR`       | Circulate right AC and E |
| `CIL`       | Circulate left AC and E  |
| `INC`       | Increment AC             |
| `SPA`       | Skip if AC is positive   |
| `SNA`       | Skip if AC is negative   |
| `SZA`       | Skip if AC is zero       |
| `SZE`       | Skip if E is zero        |
| `HLT`       | Halt execution           |

The simulator also supports **indirect addressing** using the `I` notation.

## Assembler

The project includes a two-pass assembler capable of processing Mano Basic Computer assembly programs.

Supported assembler directives include:

* `ORG` — Set the starting memory address
* `DEC` — Store a decimal value
* `HEX` — Store a hexadecimal value
* `END` — End the program

### Example

```asm
ORG 100

LDA NM1
ADD NM2
STA RESULT
HLT

NM1, DEC 5
NM2, DEC 10
RESULT, HEX 0

END
```

The assembler resolves labels and converts the instructions into their corresponding machine-code representation.

For example:

```text
LDA NM1  →  0x2124
ADD NM2  →  0x1125
STA RESULT → 0x3126
HLT      → 0x7001
```

## How It Works

The simulator models the main stages of the Mano Basic Computer instruction cycle.

### 1. Assemble

The assembly source code is parsed and translated into machine instructions. Labels are resolved and the resulting instructions are loaded into memory.

### 2. Fetch

The simulator performs the fetch micro-operations, including transferring the program counter value to the address register and fetching the instruction from memory.

### 3. Decode

The instruction register is decoded to determine:

* Opcode
* Address
* Addressing mode
* Memory-reference vs. register-reference instruction

### 4. Execute

The appropriate micro-operations are executed according to the instruction.

The simulator allows the execution process to be observed **one micro-step at a time**, making the internal operation of the Mano Basic Computer easier to understand.

## Architecture

The simulator represents important Mano Basic Computer components such as:

* **PC** — Program Counter
* **AR** — Address Register
* **IR** — Instruction Register
* **AC** — Accumulator
* **DR** — Data Register
* **TR** — Temporary Register
* **INPR** — Input Register
* **OUTR** — Output Register
* **E** — Extended Accumulator / Carry bit
* **Memory**

The interface provides live visualization of register and memory changes during execution.

## Technologies

* **HTML5** — Structure
* **CSS3** — Interface and animations
* **JavaScript** — Assembler, CPU simulation, instruction execution, and UI logic

No backend or external server is required.

## Running the Project

Because this is a browser-based project, it can be run directly from a local machine.

### Using VS Code

1. Clone or download the repository.
2. Open the project in **Visual Studio Code**.
3. Open `manosimmm.html`.
4. Run it using **Live Server** or open the HTML file directly in a browser.

The simulator will run entirely in the browser.

## Project Purpose

This project was developed to provide an interactive way to understand the **Mano Basic Computer architecture** and the relationship between assembly language, machine code, registers, memory, and CPU micro-operations.

Instead of only studying the instruction cycle theoretically, the simulator allows each operation to be observed as it happens.

## Example Workflow

```text
Assembly Code
      ↓
Two-Pass Assembler
      ↓
Machine Code
      ↓
Memory
      ↓
Fetch
      ↓
Decode
      ↓
Execute
      ↓
Register / Memory Updates
```

## Author

**Lobna Amr**

Computer & Communication Engineering Student

---

⭐ If you find this project useful for studying Computer Organization and Architecture, consider giving the repository a star!
