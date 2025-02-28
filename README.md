# samsung-riscv
6-week training program on RISC-V and semiconductor technologies. An initiative by Samsung Semiconductor India Research (SSIR) in collaboration with VLSI System Design (VSD), it aims to nurture young talented minds through an intensive training program. This course is instructed by Kunal Ghosh Sir of VLSI System Design.

## 
**Samsung RISC-V Internship by VSD**  

---

## Personal Information  
**Name**: Dhruva R 

**Email**: dhruvarangaswamy07@gmail.com  
**College**: Dayananda Sagar College of Engineering, 5th semester 

---

## Task 1 - Compilation Differences Between -O1 and -Ofast

### -O1 Optimization
- Prioritizes readable and understandable code with basic optimizations.
- Larger number of instructions due to minimal optimization.
- Keeps intermediate calculations and variables in memory.
- Detailed code flow makes it easier to follow and debug.

### -Ofast Optimization
- Aggressive optimization for maximum performance, potentially sacrificing strict adherence to standards.
- Fewer instructions as redundant operations are removed.
- More compact code layout with streamlined computations.
- Reduced intermediate steps, making the code harder to debug but faster to execute.

---

## Task 2 - Optimization Flags -O1 and -Ofast Performance

### -O1 Optimization
- Takes longer route with more detailed steps.  
- Starts at memory address `0x10184`.  
- More instructions and steps visible.  
- Easier to debug and follow the program flow.  
- Good for development and testing phase.  

### -Ofast Optimization
- Takes shorter, faster route.  
- Starts at memory address `0x100b0`.  
- Fewer instructions to do the same task.  
- Harder to debug but better performance.  
- Perfect for final production code.  

### Main Differences
- Memory addresses are organized differently.  
- `-Ofast` uses fewer registers more efficiently.  
- Instruction count is lower in `-Ofast`.  
- Both reach the same result (e.g., 120) but through different paths.  

### Memory & Performance
- `-Ofast` has a more compact code layout.  
- Better register management in `-Ofast`.  
- Less memory usage in the `-Ofast` version.  
- Faster execution due to optimization.  

### Trade-offs
- **O1**: Better debugging vs slower performance.  
- **Ofast**: Better performance vs harder debugging.  
- `-O1` shows a clear instruction flow.  
- `-Ofast` focuses on speed over readability.  

---
## 🚀 Task 3: Decoding RISC-V Instructions: A Visual Guide


## 📖 Introduction Section:

RISC-V (Reduced Instruction Set Computer - V) is an open standard instruction set architecture (ISA) based on established reduced instruction set computing principles. Unlike proprietary ISAs, RISC-V is free and open, enabling unrestricted academic and commercial use without licensing fees. This has made RISC-V an attractive option for research, education, and industry applications, fostering innovation and development across various domains.

## 🔍 Importance of Understanding Instruction Formats

Understanding instruction formats is crucial for several reasons:

Instruction Decoding ✅ Knowing the structure of different instruction formats enables the correct decoding of instructions, which is essential for the CPU to execute them correctly.
Pipeline Design ⚙️ Instruction formats impact the design of the CPU pipeline. Proper handling ensures efficient instruction fetch, decode, execution, memory access, and write-back stages.
Compiler Design 📝 Compilers generate machine code that adheres to the ISA's instruction formats, optimizing performance and efficiency.
Debugging and Verification 🛠️ Helps in identifying issues related to incorrect instruction execution or pipeline hazards.
Extensibility and Customization 🎨 RISC-V's modular nature allows for custom extensions, making it essential to understand the base instruction formats.

## 👨‍💻 Register Naming in RISC-V
RISC-V has 32 registers, named x0 through x31. However, they have descriptive names based on their typical usage:
x0 (zero): Always holds the constant value 0.
x1 (ra): Return Address register.
x2 (sp): Stack Pointer register.
x3 (gp): Global Pointer register.
x4 (tp): Thread Pointer register.

## 🎯 Saved, Temporary, and Argument Registers
Saved Registers (s0-s11): x8, x9, x18-x27 (Preserved across function calls).
Temporary Registers (t0-t6): Used for intermediate calculations.
Argument Registers (a0-a7): x10-x17 (Used to pass function arguments & store return values).

🌟 "Understanding I-Type, S-Type, B-Type, U-Type, and J-Type Instructions"

## ⚖️ ABI: Application Binary Interface

## 🎓 BASICS

## 🔢 Instruction Types and Fields

The RISC-V instructions are categorized based on their field organization:

R-type: Register type
I-type: Immediate type
S-type: Store type
B-type: Branch type
U-type: Upper immediate type
J-type: Jump type

# RISC-V Instruction Format 🚀

This guide provides an overview of the RISC-V instruction format, including different types of instructions, how to extract immediate values, and a breakdown of the opcode, funct3, and funct7 fields.


## **1. Opcode and Function Fields 🎯**

- **Opcode**: Determines the type of instruction.
- **func3 & func7**: Further specify the operation within the instruction type.

### Example:
- In **R-type** instructions, `func3` and `func7` differentiate between operations like addition and subtraction.


## **2. Immediate Values and Registers 💾**

- **Immediate Values**: Encoded in specific fields within the instruction.
  - **Example**: In **I-type** instructions, the immediate value field is 12 bits long along with source and destination registers.
  
- **Registers**: Specified in fields like `rd` (destination register), `rs1` (source register 1), and `rs2` (source register 2).


## **3. Example: U-Type Instruction 🏗️**

### `lui x5, 0x12345`
- **Encoding**: The immediate value `0x12345` is placed in the instruction’s immediate field, and `x5` is specified in the `rd` field.
- **Machine Execution**: Loads the upper 20 bits of the immediate value into the upper 20 bits of register `x5`.

## **4. Arithmetic Instructions ➕**

- **ADD**: Adds values in two registers and stores the result in a third register.
  - Example: `ADD rd, rs1, rs2` → `rd = rs1 + rs2`
  
- **ADDI**: Adds a register and an immediate value (constant) and stores the result.
  - Example: `ADDI rd, rs1, imm` → `rd = rs1 + imm`


## **5. Logical Instructions 🔲**

- **AND**, **OR**, **XOR**: Perform bitwise operations.
  - Example: `AND rd, rs1, rs2` → `rd = rs1 & rs2`

## **6. Branch Instructions ↩️**

- **BEQ**: Branch if equal.
  - Example: `BEQ rs1, rs2, offset` → If `rs1 == rs2`, `PC = PC + offset`
  
- **BNE**: Branch if not equal.
  - Example: `BNE rs1, rs2, offset` → If `rs1 != rs2`, `PC = PC + offset`

## **7. Load and Store Instructions 📦**

- **LW**: Load word from memory.
  - Example: `LW rd, offset(rs1)` → `rd = memory[rs1 + offset]`
  
- **SW**: Store word to memory.
  - Example: `SW rs1, offset(rs2)` → `memory[rs2 + offset] = rs1`

## **8. Special Instructions 🌟**

- **AUIPC**: Add upper immediate to PC.
  - Example: `AUIPC rd, imm` → `rd = PC + imm << 12`

## **9. Branch and Jump Instructions 🚶‍♂️**

- **Jump (J)**: Unconditional branch to a specified address.
- **Branch (B)**: Conditional branch based on a comparison.


## **10. RV32I Extensions ➗**

RISC-V allows optional extensions for additional functionality:

- **M**: Integer multiplication and division.
- **A**: Atomic instructions.
- **F, D, Q**: Floating-point operations (32-bit, 64-bit, 128-bit).
- **C**: Compressed instructions.

## **11. RISC-V R-Type Instructions 💡**

R-type instructions are used for operations that involve only registers (arithmetic, logical, shift operations).

### Format:
- **opcode**: Specifies the operation (e.g., `0110011` for integer register-register operations).
- **rd**: Destination register.
- **funct3**: Further specifies the operation.
- **rs1**: First source register.
- **rs2**: Second source register.
- **funct7**: Further specifies the operation.

## **12. I-Type Instructions 🔢**

I-Type instructions are used for immediate arithmetic, load operations, and certain control flow instructions.

### Extracting Immediate Value:
- The immediate value spans bits `[31:20]`.
- Example: `imm_i = (instruction & 0xFFF00000) >> 20`

### Example: `ADDI rd, rs1, imm`
- **opcode**: `0010011` (for immediate arithmetic operations)
- **funct3**: `000` (for ADDI)
- **imm**: Immediate value
- **rs1**: Source register 1
- **rd**: Destination register

## **13. S-Type Instructions 🔄**

### Example: `SW rs2, imm(rs1)`
- **opcode**: `0100011` (for store operations)
- **funct3**: `010` (for SW)
- **imm**: Immediate value (split into `imm[11:5]` and `imm[4:0]`)
- **rs1**: Base address register
- **rs2**: Source register to be stored


## **14. B-Type Instructions 🔁**

### Example: `BEQ rs1, rs2, imm`
- **opcode**: `1100011` (for branch operations)
- **funct3**: `000` (for BEQ)
- **imm**: Immediate value (split into `imm[12]`, `imm[10:5]`, `imm[4:1]`, `imm[11]`)
- **rs1**: Source register 1
- **rs2**: Source register 2


## **15. U-Type Instructions 🛠️**

U-Type instructions are used for operations like loading upper immediate (LUI) and adding upper immediate to PC (AUIPC).

### Extracting Immediate Value:
- The immediate value spans bits `[31:12]`.
- To extract, apply the mask `0xFFFFF000`.
  - Example: For instruction `0x12345000`, the extracted value is `0x12345000`.
  - 
# RISC-V Instruction Encoding and Decoding 📘

This document outlines the encoding and usage of RISC-V instructions, including examples with machine code and binary representations.

## **1. U-Type Instructions 🏗️**

### **Encoding and Usage**
- The immediate value extracted directly forms part of the **U-type** instruction.
  - For **LUI** (Load Upper Immediate), this value is loaded into the destination register.
  - For **AUIPC** (Add Upper Immediate to PC), this value is added to the current **Program Counter (PC)**.

### **Example: LUI**
- **Assembly**: `LUI rd, imm`
- **Opcode**: `0110111` (for LUI)
- **Immediate**: Upper 20 bits of the immediate value.
- **rd**: Destination register.

## **2. J-Type Instructions 🔄**

### **Example: JAL**
- **Assembly**: `JAL rd, imm`
- **Opcode**: `1101111` (for JAL)
- **Immediate**: Immediate value (split into `imm[20]`, `imm[10:1]`, `imm[11]`, `imm[19:12]`).
- **rd**: Destination register (stores the return address).


##  15 Unique RISC-V Instructions Decoding 🔍**

### **Machine Code for addi sp, sp, -16**

#### **addi (Add Immediate)**: 
This instruction adds an immediate value to a register, storing the result in the destination register.

- **Instruction**: `addi sp, sp, -16`
- **Opcode**: `0010011` (7 bits)
- **Immediate**: `-16` (12 bits, two's complement)
- **Source Register (rs1)**: `sp` (x2, 5 bits)
- **Destination Register (rd)**: `sp` (x2, 5 bits)
- **Function (funct3)**: `000` (3 bits)

**Breakdown**:
- Immediate (-16): `111111111000` (12 bits, two's complement)
- `rs1` (sp = x2): `00010`
- `funct3`: `000`
- `rd` (sp = x2): `00010`
- **Opcode**: `0010011`

**Machine Code Breakdown for `addi sp, sp, -16`**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-------------|-----------------|
| 111111111000        | 00010        | 000             | 00010       | 0010011         |

**Binary Representation**:
- **Binary**: `111111111000 00010 000 00010 0010011`
- **Hex**: `ff5013`



### **Machine Code for sd ra, 8(sp)**

#### **sd (Store Doubleword)**: 
This instruction stores a 64-bit value from a source register into memory.

- **Instruction**: `sd ra, 8(sp)`
- **Opcode**: `0100011` (7 bits)
- **Immediate**: `8` (12 bits, split into two parts: `imm[11:5]` and `imm[4:0]`)
- **Source Register (rs2)**: `ra` (x1, 5 bits)
- **Base Register (rs1)**: `sp` (x2, 5 bits)
- **Function (funct3)**: `011` (3 bits)

**Breakdown**:
- Immediate (8): `000000001000` (split into `imm[11:5] = 0000000` and `imm[4:0] = 01000`)
- `rs2` (ra = x1): `00001`
- `rs1` (sp = x2): `00010`
- `funct3`: `011`
- **Opcode**: `0100011`

**Machine Code Breakdown for `sd ra, 8(sp)`**:
| imm[11:5] (7 bits) | rs2 (5 bits) | rs1 (5 bits) | funct3 (3 bits) | imm[4:0] (5 bits) | Opcode (7 bits) |
|--------------------|--------------|--------------|-----------------|-------------------|-----------------|
| 0000000            | 00001        | 00010        | 011             | 01000             | 0100011         |

**Binary Representation**:
- **Binary**: `0000000 00001 00010 011 01000 0100011`
- **Hex**: `0001023f`

---

### **Machine Code for li a5, 500**

#### **li (Load Immediate)**: 
This instruction loads a 32-bit immediate value into a register.

- **Instruction**: `li a5, 500`
- **Opcode**: `0010011` (7 bits)
- **Immediate**: `500` (12 bits, sign-extended)
- **Destination Register (rd)**: `a5` (x15, 5 bits)
- **Function (funct3)**: `000` (3 bits)

**Breakdown**:
- Immediate (500): `000000111110100` (12 bits)
- `rd` (a5 = x15): `01111`
- `funct3`: `000`
- **Opcode**: `0010011`

**Machine Code Breakdown for `li a5, 500`**:
| Immediate (12 bits) | rd (5 bits) | funct3 (3 bits) | Opcode (7 bits) |
|---------------------|-------------|-----------------|-----------------|
| 000000111110100     | 01111       | 000             | 0010011         |

**Binary Representation**:
- **Binary**: `000000111110100 01111 000 0010011`
- **Hex**: `01f30313`


##  **addiw a5, a5, -1** ➕  
**Instruction**: Adds a 32-bit immediate value to a register and stores the result in the destination register.

**Opcode**: 0010011 (7 bits)  
**Immediate**: -1 (12 bits, two's complement)  
**Source Register (rs1)**: a5 (x15, 5 bits)  
**Destination Register (rd)**: a5 (x15, 5 bits)  
**Funct3**: 001 (3 bits)

**Machine Code Breakdown**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-------------|-----------------|
| 111111111111        | 01111        | 001             | 01111       | 0010011         |

**Binary**: `111111111111 01111 001 01111 0010011`  
**Hex**: `fff30313`


##  **bnez a5, 10190 <main+0xc>** ⬇️  
**Instruction**: Branch if Not Equal to Zero. This instruction performs a branch if the value in the source register is not zero.

**Opcode**: 1100011 (7 bits)  
**Immediate**: 10190 (12 bits, sign-extended)  
**Source Register (rs1)**: a5 (x15, 5 bits)  
**Funct3**: 001 (3 bits)

**Machine Code Breakdown**:
| imm[12|10:5] (7 bits) | rs1 (5 bits) | funct3 (3 bits) | imm[4:1|11] (5 bits) | Opcode (7 bits) |
|-----------------------|--------------|-----------------|-----------------------|-----------------|
| 0000000               | 01111        | 001             | 01001110              | 1100011         |

**Binary**: `0000000 01111 001 01001110 1100011`  
**Hex**: `000f13f3`


##  **lui a2, 0x1f** 💾  
**Instruction**: Loads a 20-bit immediate value into the upper 20 bits of a register, setting the lower 12 bits to zero.

**Opcode**: 0110111 (7 bits)  
**Immediate**: 0x1f (20 bits, upper 20 bits of the immediate value)  
**Destination Register (rd)**: a2 (x6, 5 bits)

**Machine Code Breakdown**:
| imm[19:12] (8 bits) | imm[11:0] (12 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|---------------------|-------------|-----------------|
| 00000000            | 0000000001111111    | 00110       | 0110111         |

**Binary**: `00000000000000000000 00110 0110111`  
**Hex**: `00030337`


##  **addi a2, a2, -1726** ➗  
**Instruction**: Adds an immediate value to a register.

**Opcode**: 0010011 (7 bits)  
**Immediate**: -1726 (12 bits, two's complement)  
**Source Register (rs1)**: a2 (x6, 5 bits)  
**Destination Register (rd)**: a2 (x6, 5 bits)  
**Funct3**: 000 (3 bits)

**Machine Code Breakdown**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-------------|-----------------|
| 111111101110        | 00110        | 000             | 00110       | 0010011         |

**Binary**: `111111101110 00110 000 00110 0010011`  
**Hex**: `ffd30393`


##  **li a1, 500** 📥  
**Instruction**: Loads an immediate value into a register.

**Opcode**: 0010011 (7 bits)  
**Immediate**: 500 (12 bits)  
**Destination Register (rd)**: a1 (x11, 5 bits)  
**Funct3**: 000 (3 bits)

**Machine Code Breakdown**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-------------|-----------------|
| 000000011111        | 00000        | 000             | 01011       | 0010011         |

**Binary**: `000000011111 00000 000 01011 0010011`  
**Hex**: `01f30393`


##  **lui a0, 0x21** 💻  
**Instruction**: Loads a 20-bit immediate value into the upper 20 bits of a register.

**Opcode**: 0110111 (7 bits)  
**Immediate**: 0x21 (20 bits)  
**Destination Register (rd)**: a0 (x10, 5 bits)

**Machine Code Breakdown**:
| imm[19:12] (8 bits) | imm[11:0] (12 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|---------------------|-------------|-----------------|
| 00000000            | 000000100001        | 01010       | 0110111         |

**Binary**: `00000000000000000000 01010 0110111`  
**Hex**: `00052137`


##  **addi a0, a0, 400** ➗  
**Instruction**: Adds an immediate value to a register.

**Opcode**: 0010011 (7 bits)  
**Immediate**: 400 (12 bits)  
**Source Register (rs1)**: a0 (x10, 5 bits)  
**Destination Register (rd)**: a0 (x10, 5 bits)  
**Funct3**: 000 (3 bits)

**Machine Code Breakdown**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-------------|-----------------|
| 000000011001        | 01010        | 000             | 01010       | 0010011         |

**Binary**: `000000011001 01010 000 01010 0010011`  
**Hex**: `00066093`


## **jal ra, 10418** 🔄  
**Instruction**: Jump and Link. This instruction performs a jump to a target address, saving the return address in the link register (ra).

**Opcode**: 1101111 (7 bits)  
**Immediate**: 10418 (20 bits, sign-extended)  
**Destination Register (rd)**: ra (x1, 5 bits)

**Machine Code Breakdown**:
| imm[19:12] (8 bits) | imm[11:1] (11 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|---------------------|-------------|-----------------|
| 00000000            | 00101001110         | 00001       | 1101111         |

**Binary**: `00000000000000000000 00001 1101111`  
**Hex**: `0005286f`


##  **li a0, 0** 📥  
**Instruction**: Loads an immediate value into a register.

**Opcode**: 0010011 (7 bits)  
**Immediate**: 0 (12 bits)  
**Destination Register (rd)**: a0 (x10, 5 bits)  
**Funct3**: 000 (3 bits)

**Machine Code Breakdown**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-------------|-----------------|
| 000000000000        | 00000        | 000             | 01010       | 0010011         |

**Binary**: `000000000000 00000 000 01010 0010011`  
**Hex**: `00030393`


##  **ld ra, 8(sp)** 📥  
**Instruction**: Loads a 64-bit value from memory into a register.

**Opcode**: 0000011 (7 bits)  
**Immediate**: 8 (12 bits)  
**Base Register (rs1)**: sp (x2, 5 bits)  
**Destination Register (rd)**: ra (x1, 5 bits)  
**Funct3**: 011 (3 bits)

**Machine Code Breakdown**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-------------|-----------------|
| 000000000010        | 00010        | 011             | 00001       | 0000011         |

**Binary**: `000000000010 00010 011 00001 0000011`  
**Hex**: `00028283`


##  **addi sp, sp, 16** ➗  
**Instruction**: Adds an immediate value to a register.

**Opcode**: 0010011 (7 bits)  
**Immediate**: 16 (12 bits)  
**Source Register (rs1)**: sp (x2, 5 bits)  
**Destination Register (rd)**: sp (x2, 5 bits)  
**Funct3**: 000 (3 bits)

**Machine Code Breakdown**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-------------|-----------------|
| 000000010000        | 00010        | 000             | 00010       | 0010011         |

**Binary**: `000000010000 00010 000 00010 0010011`  
**Hex**: `00050393`


##  **ret** 🔙  
**Instruction**: Returns from a function by jumping to the address stored in ra.

**Opcode**: 1100111 (7 bits)  
**Immediate**: 0 (12 bits)  
**Source Register (rs1)**: ra (x1, 5 bits)

**Machine Code Breakdown**:
| Immediate (12 bits) | rs1 (5 bits) | funct3 (3 bits) | Opcode (7 bits) |
|---------------------|--------------|-----------------|-----------------|
| 000000000000        | 00001        | 000             | 1100111         |

**Binary**: `000000000000 00001 000 1100111`  
**Hex**: `00008067`

---

## ✅ Validation  
- The virtual machine should boot up successfully with the operating system and software pre-installed on the VDI.  
- Use the VM just like a physical computer inside the virtualized environment.  
# Task 4: RISC-V Core Functional Simulation

## Progress Overview
- Retrieved and configured the Verilog netlist and testbench files.
- Established a simulation setup utilizing `iverilog` and `gtkwave`.
- Conducted functional simulations to validate the RISC-V Core behavior.
- Captured and reviewed waveform outputs to confirm proper core operation.
- Developed and compiled a basic C program using RISC-V GCC with `-O1` and `-Ofast` optimization levels.
- Created and examined object dumps for both optimization settings.
- Uploaded waveform snapshots, simulation outcomes, and compiled binaries to the GitHub repository.

- ## Task 5
# 🚀 Multi-Mode Counter Using ESP8266 & VSD Squadron Mini  
**A Smart Counter Controlled via Blynk Web Dashboard**  

## 📌 Project Overview  
This project implements a **4-bit multi-mode counter** using an **ESP8266 NodeMCU** and **VSD Squadron Mini (CH32V0xx)**. The counting mode is controlled via **Blynk Web Dashboard**, and the output is displayed using **LEDs connected to PC0-PC3**.  

## 🔥 Features  
✅ **4 Counting Modes:**  
- **00 → Up Counter** (0-15)  
- **01 → Down Counter** (15-0)  
- **10 → Ring Counter** (Shifting '1')  
- **11 → BCD Counter** (0-9 in BCD)  

✅ **Remote Control via Blynk**  
✅ **ESP8266 & VSD Integration**  
✅ **Real-time LED Display (PC0-PC3)**  

## 🛠️ Hardware Requirements  
- **ESP8266 NodeMCU**  
- **VSD Squadron Mini (CH32V0xx)**  
- **4 LEDs (PC0-PC3)**  
- **Resistors (330Ω)**  
- **Jumper Wires**  
- **Power Supply (5V)**  

## 🔌 Circuit Connections  
- **ESP8266 → VSD Squadron Mini:**  
  - **D2 → PC5 (Mode Select 1)**  
  - **D3 → PC6 (Mode Select 2)**  
- **VSD Squadron Mini → LEDs:**  
  - **PC0, PC1, PC2, PC3 → LED Indicators**  

## 📜 Code  
The full Arduino code is available in [`code/multi_mode_counter.ino`](code/multi_mode_counter.ino).  

## 📊 Results  
| **Mode**       | **LED Output (PC0-PC3)** |  
|---------------|----------------------|  
| Up Counter    | Counts 0000 → 1111 |  
| Down Counter  | Counts 1111 → 0000 |  
| Ring Counter  | Single '1' shifts cyclically |  
| BCD Counter   | Counts 0000 → 1001 (0-9) |  

## 🌍 Blynk Web Dashboard  
- **V0** → PC5 (Mode Select 1)  
- **V1** → PC6 (Mode Select 2)  

## 📌 Future Enhancements  
🚀 **OLED Display for Count Output**  
🚀 **Mobile App Integration**  
🚀 **Expand to 8-bit Counting**  
