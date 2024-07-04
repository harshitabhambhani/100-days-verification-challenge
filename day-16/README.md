# 100 Days Verification Challenge - Day 16 - Types of Computer Architecture

## 1. Explain 3 major types of computer architecture - System Design, ISA (Instruction Set Architecture) & Microarchitecture.

### System Design
System design architecture refers to the overall design and organization of a computer system. It encompasses all the hardware components and their interactions to ensure efficient performance. This includes the CPU, memory, input/output devices, storage, and the bus that connects these components. The design must account for factors like power consumption, thermal management, and cost.

### Instruction Set Architecture (ISA)
ISA defines the part of the processor that is visible to the programmer or compiler writer. It includes the set of instructions the processor can execute, addressing modes, data types, registers, and the hardware support for managing interrupts and exceptions. Popular examples of ISAs are x86, ARM, and MIPS.

### Microarchitecture
Microarchitecture refers to the implementation of the ISA at the hardware level. It defines how the processor will execute instructions and manage data. This includes decisions on pipelining, cache design, the execution units (ALUs, FPUs), branch prediction, and more. Microarchitecture determines the performance, power efficiency, and complexity of the CPU.

## 2. Explain Von Neumann and Harvard architecture in detail.

### Von Neumann Architecture
In Von Neumann architecture, both data and program instructions are stored in the same memory space and use the same bus for both data and instructions. This means that a single read/write line is shared for fetching instructions and data, leading to the Von Neumann bottleneck.

Key Features:
- Shared memory for data and instructions.
- Single bus for data transfer.
- Simplifies design and control.
- Suitable for general-purpose computing.

### Harvard Architecture
In Harvard architecture, data and instructions are stored in separate memory spaces and use different buses. This allows simultaneous access to data and instructions, which can improve performance.

Key Features:
- Separate memory for data and instructions.
- Separate buses for data and instructions.
- More complex design.
- Often used in specialized applications like DSPs (Digital Signal Processors).

## 3. List down pros & cons of Von Neumann and Harvard architecture.

### Von Neumann Architecture
**Pros:**
- Simpler design and control.
- More flexible memory usage.
- Easier to implement and debug.

**Cons:**
- The Von Neumann bottleneck limits performance.
- Potential for slower execution speed due to shared memory access.

### Harvard Architecture
**Pros:**
- Faster access to data and instructions due to separate buses.
- Reduces the risk of data corruption.

**Cons:**
- More complex and expensive design.
- Less flexible memory usage since memory is split between data and instructions.

## 4. Modified Harvard Architecture

Modified Harvard Architecture combines elements of both Von Neumann and Harvard architectures. It allows data and instructions to be stored in separate caches but uses a unified memory space. This architecture can fetch data and instructions simultaneously while simplifying memory management compared to pure Harvard architecture.

## 5. RISC & CISC Architecture

### RISC (Reduced Instruction Set Computer)
RISC architecture uses a small set of simple instructions that are executed within a single clock cycle. The design emphasizes efficiency and speed, allowing for more straightforward pipelining and higher performance.

Key Features:
- Small, highly optimized set of instructions.
- Uniform instruction format.
- Emphasis on software to manage complexity.
- Examples: ARM, MIPS.

### CISC (Complex Instruction Set Computer)
CISC architecture uses a large set of instructions, including many complex ones that can perform multiple operations in a single instruction. This design aims to reduce the number of instructions per program, at the cost of more complex hardware.

Key Features:
- Large set of instructions, including complex ones.
- Variable instruction format.
- Emphasis on hardware to manage complexity.
- Examples: x86, VAX.

## 6. Pros & Cons of RISC vs CISC

### RISC Architecture
**Pros:**
- Simpler hardware design.
- Easier to pipeline, leading to higher performance.
- Lower power consumption.

**Cons:**
- More instructions required to perform a task, increasing code size.
- Increased reliance on software for complex tasks.

### CISC Architecture
**Pros:**
- Fewer instructions per program, reducing memory usage.
- Complex instructions can perform multiple tasks.

**Cons:**
- More complex hardware design.
- Harder to pipeline, potentially reducing performance.
- Higher power consumption.

## 7. RISC-V Processor

RISC-V is an open-source RISC ISA that is designed to be scalable and customizable. It allows for extensions and modifications to suit specific needs, making it highly versatile for various applications.

## 8. Why Use RISC-V?

RISC-V offers several benefits:
- Open-source and free to use, reducing licensing costs.
- Scalable and modular, allowing customization for specific applications.
- Simplified instruction set for easier implementation and optimization.
- Strong community support and growing ecosystem.

## 9. SIMD Architecture in GPU

SIMD (Single Instruction, Multiple Data) architecture in GPUs allows a single instruction to operate on multiple data points simultaneously. This parallelism makes SIMD particularly effective for tasks like graphics rendering, scientific computations, and machine learning.

## 10. Advantages of SIMD Over SISD

**SIMD (Single Instruction, Multiple Data):**
- Higher performance for parallel tasks.
- Better utilization of hardware resources.
- Efficient for data-parallel applications.

**SISD (Single Instruction, Single Data):**
- Simpler programming model.
- Easier to debug and maintain.
- More suitable for sequential processing tasks.

Overall, SIMD provides significant performance improvements for parallelizable tasks by leveraging data-level parallelism, making it a powerful architecture for GPUs and other parallel processing applications.
