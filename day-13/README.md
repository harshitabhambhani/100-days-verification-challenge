# 100 Days Verification Challenge - Day 13 - Processor pipelining

## 1. Why do we need processor pipelining?

Processor pipelining is used to increase the instruction throughput (the number of instructions that can be processed in a unit of time) by allowing multiple instructions to overlap in execution. Instead of waiting for one instruction to complete before starting the next, pipelining allows a new instruction to begin before the previous one has finished. This overlapping increases the efficiency and speed of the processor, making better use of the CPU resources.

## 2. What will happen if we don't use any processor pipelining at all?

If we don't use any processor pipelining, each instruction must be completed before the next one begins, leading to sequential processing. This results in lower instruction throughput and overall slower execution. The CPU would spend a significant amount of time idle, waiting for each instruction to complete all its stages, which decreases the efficiency and performance of the processor.

## 3. Draw 5-Stage Pipeline and Explain Operation of Each Stage

A typical 5-stage pipeline in a processor consists of the following stages:

1. **Fetch (IF)**
   - It reads the next expected instruction into the buffer.
  ```
IR → Mem [PC] ;
PC → PC + 4 ;
```

2. **Decode (ID)**
   - In this, there are following steps:
     - Instruction Decoding, in which determines opcode and operand specifiers.
     - Calculate Operand, in which calculates effective address of each source operand.
     - Fetch Operands, in which fetch each operand from memory.
    ```
    A → Regs [IR6,  10] ;
    B → Regs [IR11, ...,  15] ;
    Immediate → (IR16)16## (IR16, ..., 31)
    ```

3. **Execute (EX)**
   - It performs indicated operation.
```
Memory ref:   ALUoutput  →  A + Immediate ;
Reg-Reg ALU:  ALU  →  A func B ;
Reg-Imm ALU:  ALUoutput  →  A op Immediate ;
Branch:       ALUoutput  →  PC + Immediate;  Cond * (A op 0)
```

4. **Memory Access (MEM)**
   - If the instruction requires access to memory, the required data is read from or written to memory.
```
Memory ref:  LMD  →  Mem [ALUoutput]  or Mem (ALUoutput)  →  B
Branch:      if (cond) PC  →  ALUoutput
```

5. **Write Back (WB)**
   - The result of the instruction execution is written back to the register file or memory.
```
Reg-Reg ALU:   Regs [R16, ...., 20]  →  ALUoutput ;
Reg-Imm ALU:   Regs [R11, ..., 15] → ALUoutput ;
Reg-Reg ALU:   Regs [R11, ...., 15]  →  LMD ;
```

## 4. Advantages and Disadvantages of Processor Pipelining

**Advantages:**

- **Increased Throughput**: Multiple instructions can be processed simultaneously, increasing the number of instructions executed per unit time.
- **Improved CPU Utilization**: The CPU resources are utilized more efficiently, as different stages of multiple instructions are processed concurrently.
- **Higher Performance**: Leads to better overall system performance and faster program execution.

**Disadvantages:**

- **Pipeline Hazards**: Situations such as data hazards, control hazards, and structural hazards can cause delays in the pipeline.
- **Complexity**: Implementing a pipeline increases the complexity of the CPU design.
- **Debugging Difficulty**: Troubleshooting and debugging pipelined processors can be more challenging than non-pipelined processors.

## 5. Pipeline Cycle Time and Non-Pipeline Execution Time

Given the durations of each phase and the latch delay:

- Fetch: 60 ns
- Decode: 50 ns
- Execute: 90 ns
- Memory Access: 100 ns
- Write back: 150 ns
- Latch delay: 25 ns

### i. Pipeline Cycle Time

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/f800f5c4-5615-4358-a5b5-8313113bacfc)

### (i). Pipeline Cycle Time:

Pipeline cycle time = max (60, 50, 90, 100, 150) + latch delay
                    = 150 + 25
                    = 175 ns

### (ii). Non-pipeline Execution Time:

Non-pipeline execution time = Σ (5 phases)
                            = 60 + 50 + 90 + 100 + 150
                            = 450 ns
