# 100 Days Verification Challenge - Day 50 - RTL Design

## 1. What are the main factors that affect testability of a design?

1. **Controllability**: The ease with which a signal can be controlled to a desired value from primary inputs.
2. **Observability**: The ease with which the effects of a signal can be observed at the primary outputs.
3. **Sequential Depth**: The number of sequential elements between the input and the point of observation.
4. **Complexity of Combinatorial Logic**: Complex logic can obscure faults, making them harder to detect.
5. **Clock Domain Crossings**: Signals crossing multiple clock domains can be difficult to test.
6. **Reset Mechanisms**: Asynchronous resets can complicate test patterns and fault detection.
7. **Tri-state Buses**: These can be difficult to control and observe during testing.
8. **Scan Chain Design**: Presence and quality of scan chains impact testability.

## 2. Some Flip-Flops in my chip have their resets driven by other Flip-Flops within the chip. How will this affect the testability, and what's the workaround?

This can create issues with testability because the reset signal is not directly controllable from the primary inputs, leading to unpredictable states during testing. 

**Workaround**: 

Implement a test mode that forces the reset signals to a known state or use a global reset during test operations.

## 3. I have derived clocks in my chip. What are the testability implications, and what is the workaround for it?

Derived clocks can complicate test pattern generation and timing analysis. 

**Workaround**: 

Use clock gating or control signals to manage derived clocks during testing. Ensure that all derived clocks can be controlled and observed.

## 4. My chip is power sensitive, and, hence, there are gated clocks in it. What are its testability implications and workaround?

Gated clocks can prevent certain parts of the circuit from being tested if the clocks are gated off. 

**Workaround**: 

Design the gating control to be bypassed during test mode, ensuring all parts of the circuit can be clocked and tested.

## 5. What is the implication of a combinatorial feedback loops in design testability?

Combinatorial feedback loops can create unstable states and make fault detection difficult. 

**Workaround**: 

Avoid combinatorial loops or break them with registers. Ensure proper timing and control mechanisms are in place.

## 6. How does the presence of latches affect the testability, and what's the workaround?

Latches can create race conditions and timing issues that are hard to test. 

**Workaround**: 

Use scan chains to convert latches into scan-friendly flip-flops during test mode or implement latch-based design-for-test (DFT) techniques.

## 7. What is LSFR(Linear Shift Feedback Register? What are its applications?

An LFSR is a shift register whose input bit is a linear function of its previous state. 

**Applications**: 

Used for pseudo-random number generation, built-in self-test (BIST), and error detection/correction.

## 8. Design a 4-bit LFSR using Verilog.

```verilog
module lfsr (
    input wire clk,
    input wire reset,
    output reg [3:0] lfsr_out
);
    wire feedback = lfsr_out[3] ^ lfsr_out[2]; // Feedback function

    always @(posedge clk or posedge reset) begin
        if (reset)
            lfsr_out <= 4'b0001; // Initial state
        else begin
            lfsr_out <= {lfsr_out[2:0], feedback}; // Shift and feedback
        end
    end
endmodule
```

## 9. What is clock gating? What are its advantages?

Clock gating is a technique to save power by disabling the clock to portions of the circuit when they are not in use. 

**Advantages**: 

Reduces dynamic power consumption, minimizes heat dissipation, and extends battery life in portable devices.

## 10. What is difference between a flop & a scan flop?

- **Flop**: A basic flip-flop used to store a single bit of data.
- **Scan Flop**: A flip-flop designed for testability, incorporating an additional input for scan chains that allows it to be set or read during test mode.

## 11. What is burn-in test? Why is it done?

A burn-in test involves operating a device at elevated temperature and voltage for an extended period to detect early failures. 

**Purpose**: 

To ensure reliability and weed out defective components that would fail early in their lifecycle.

## 12. What do you mean by fault simulation?

Fault simulation is the process of simulating a digital circuit with various fault models injected to evaluate the effectiveness of test vectors in detecting faults. **Purpose**: To ensure test coverage and identify weaknesses in the test patterns.

## 13. Why do we have multiple clock domains in an RTL design?

Multiple clock domains are used to:
- **Optimize Performance**: Different parts of the design may require different clock frequencies.
- **Power Management**: Lower clock frequencies in certain domains reduce power consumption.
- **Functional Requirements**: Certain operations may need to be synchronized with external interfaces operating at different clock rates.

Handling multiple clock domains requires careful design to manage clock domain crossings and ensure data integrity and timing correctness.
