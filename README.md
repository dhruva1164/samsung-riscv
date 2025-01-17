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
         
