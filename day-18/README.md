# 100 Days Verification Challenge - Day 18 - Microprocessors & Microcontrollers

## 1. Explain the common components of a microprocessor (IO unit, control unit, ALU, register, cache).

### I/O Unit (Input/Output Unit)
- **Function**: Manages communication between the microprocessor and external devices (e.g., keyboards, displays, storage).
- **Components**: Includes ports and interfaces like USB, serial, and parallel ports.

### Control Unit
- **Function**: Directs the operation of the processor by fetching instructions from memory, decoding them, and executing them.
- **Components**: Instruction decoder, control logic, and timing circuits.

### ALU (Arithmetic Logic Unit)
- **Function**: Performs all arithmetic (addition, subtraction) and logical (AND, OR, NOT) operations.
- **Components**: Adder, subtractor, logic gates, and shift registers.

### Register
- **Function**: Small, fast storage locations within the CPU used to hold data, instructions, and addresses temporarily during execution.
- **Types**: General-purpose registers (e.g., AX, BX in x86), special-purpose registers (e.g., Program Counter, Stack Pointer).

### Cache
- **Function**: A small, fast memory located close to the CPU to temporarily store frequently accessed data and instructions to speed up processing.
- **Levels**: Typically includes multiple levels (L1, L2, L3) with L1 being the smallest and fastest.

## 2. Difference Between Microprocessor & Microcontroller

- **Microprocessor**:
  - A general-purpose computing unit that requires external components (RAM, ROM, I/O devices) to function.
  - Used in PCs, laptops, and servers.
  - Emphasis on processing power and versatility.

- **Microcontroller**:
  - An integrated computing unit with CPU, memory (RAM, ROM), and peripherals (I/O ports, timers) on a single chip.
  - Used in embedded systems (e.g., home appliances, automotive controls).
  - Emphasis on specific control applications and low power consumption.

## 3. What Distinguishes a Microcontroller's Timer from its counter?

A microcontroller's timer is a built-in peripheral designed to measure time intervals, generate precise delays, and trigger events at specific times. Key features distinguishing it include:

- **Hardware-based timing**: Operates independently of the main CPU, allowing for precise timing operations without CPU intervention.
- **Modes of operation**: Supports various modes like counting up, counting down, and generating PWM signals.
- **Interrupts**: Can trigger interrupts when specific conditions are met, enabling real-time response to timing events.

## 4. What is program counter?

The Program Counter (PC) is a special-purpose register that holds the address of the next instruction to be executed. It automatically increments after each instruction fetch, ensuring the CPU processes instructions sequentially unless a branch, jump, or interrupt changes its value.

## 5. Explain Tri-state Logic.

Tri-state logic refers to a type of digital circuit that has three output states: 1 (high), 0 (low), and Z (high-impedance). The high-impedance state effectively disconnects the output from the circuit, allowing multiple outputs to share the same connection without interfering with each other.

## 6. What are the different types of interrupts in a microprocessor system? 

1. **Maskable Interrupts**: Can be enabled or disabled by the software. Used for less critical tasks.
   - Example: I/O interrupts.
2. **Non-Maskable Interrupts (NMI)**: Cannot be disabled by software. Used for critical events that need immediate attention.
   - Example: Power failure alerts.
3. **Software Interrupts**: Triggered by executing specific instructions. Used for system calls and debugging.
   - Example: INT instruction in x86.
4. **Hardware Interrupts**: Triggered by external hardware devices.
   - Example: Keyboard interrupt.

## 7. What's the difference between interrupt service routine and subroutine?

- **Interrupt Service Routine (ISR)**:
  - A special function that is executed in response to an interrupt.
  - Typically, hardware or software-triggered.
  - Executes asynchronously with the main program.
  - Has higher priority and pre-empts the main program.
  - Example: Handling a keyboard input interrupt.

- **Subroutine**:
  - A regular function called by the main program.
  - Executes synchronously as part of the main program flow.
  - Does not pre-empt the main program; the program waits for its completion.
  - Example: A function to calculate the square root of a number.

ISRs handle urgent tasks that require immediate attention, while subroutines perform regular tasks as part of the program's logical flow.
