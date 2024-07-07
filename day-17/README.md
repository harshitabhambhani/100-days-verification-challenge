# 100 Days Verification Challenge - Day 17 - Instructions & Buses

## 1. Can you tell at least 5 common rules of assembly language?

1. **Labels**: Labels are used to mark positions in the code, which can be referred to for jumps and loops. They typically end with a colon (`:`).

2. **Mnemonics**: Mnemonics represent the operation codes (opcodes). Each mnemonic corresponds to a specific machine language instruction (e.g., `MOV`, `ADD`, `SUB`).

3. **Operands**: Operands specify the data to be operated on. They can be registers, memory addresses, or immediate values.

4. **Comments**: Comments are used to explain the code. In many assembly languages, comments start with a semicolon (`;`).

5. **Directives**: Directives provide instructions to the assembler on how to process the assembly code. Common directives include `.data`, `.text`, `.globl`, etc.

## 2. Explain 3 major fields in an instruction: the operation field, the address field, and the mode field. 

1. **Operation Field**: This field specifies the operation to be performed (e.g., ADD, SUB, MOV). It determines the action the processor will take.

2. **Address Field**: This field specifies the location of the data required for the operation. It can be a register address, memory address, or an immediate value.

3. **Mode Field**: This field specifies how the operand should be accessed or interpreted. It defines the addressing mode (e.g., immediate, direct, indirect, register).

## 3. Explain types of micro-operations (Register transfer, Shift, Logic, Arithmetic) with example.

1. **Register Transfer Micro-Operations**: These involve moving data from one register to another.
   - Example: `R1 <- R2` (Contents of register R2 are transferred to register R1)

2. **Shift Micro-Operations**: These involve shifting the bits in a register left or right.
   - Example: `R1 <- shl R1` (Shift the contents of register R1 left by one bit)

3. **Logic Micro-Operations**: These involve performing logical operations like AND, OR, XOR, NOT on data.
   - Example: `R1 <- R1 AND R2` (Logical AND operation between registers R1 and R2, result stored in R1)

4. **Arithmetic Micro-Operations**: These involve performing arithmetic operations like addition, subtraction, increment, and decrement on data.
   - Example: `R1 <- R1 + R2` (Add the contents of registers R1 and R2, result stored in R1)

## 4. What is a horizontal microcode? Why do we use it?

Horizontal microcode is a type of microcode where each bit in the microinstruction directly controls a single micro-operation or a small set of micro-operations. It provides fine-grained control over the CPU’s internal operations.

**Usage**: Horizontal microcode is used because it allows for highly parallel and efficient control of the CPU, enabling multiple micro-operations to be performed simultaneously. This leads to faster execution of instructions but at the cost of larger microinstruction sizes.

## 5. Explain 3 major types of buses - address, data & control bus with an example. 

1. **Address Bus**: Carries the memory address from the CPU to other components (like RAM) to specify where data should be read or written.
   - Example: In a 32-bit address bus, the CPU can address up to \(2^{32}\) memory locations.

2. **Data Bus**: Transfers actual data between the CPU and other components.
   - Example: A 64-bit data bus can transfer 64 bits of data in parallel from memory to the CPU or vice versa.

3. **Control Bus**: Carries control signals from the CPU to other components to manage operations (e.g., read, write, interrupt).
   - Example: Control signals like Read/Write enable, interrupt requests, and clock signals.

## 6. Give one example of below instructions:

### a. Arithmetic Instructions
- **ADD R1, R2**: Adds the contents of register R2 to register R1 and stores the result in R1.

### b. Branch Instructions
- **JMP LABEL**: Jumps to the instruction at the location specified by LABEL.

### c. Data Transfer Instructions
- **MOV R1, R2**: Moves the contents of register R2 to register R1.

### d. Logic Instructions
- **AND R1, R2**: Performs a logical AND operation between the contents of register R1 and register R2, storing the result in R1.

### e. Bit-oriented Instructions
- **SETB C**: Sets the carry flag bit to 1 (specific to certain architectures like 8051 microcontrollers).

These instructions form the basic building blocks of assembly language programming, enabling a wide range of operations on the CPU.
