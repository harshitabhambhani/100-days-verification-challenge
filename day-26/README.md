# 100 Days Verification Challenge - Day 26 - STA terminologies

## 1. What is the difference between time borrowing & time stealing?

### Time Borrowing
Time borrowing occurs in sequential circuits with level-sensitive latches, where part of the setup time of a subsequent stage is borrowed to complete the current stage's processing. This can help to mitigate timing violations by utilizing the transparent phase of the latch.

### Time Stealing
Time stealing refers to the redistribution of slack among adjacent pipeline stages. It typically occurs in flip-flop-based designs, where slack from one stage is "stolen" by a subsequent stage to help meet timing requirements.

## 2. What is timing path? What are start & end points?

A timing path is a path through which a signal travels in a digital circuit from a starting point to an endpoint, passing through various logic elements and interconnects.

- **Start Point**: The point where the timing path begins, usually at the clock edge triggering a flip-flop, latch, or an input port.
- **End Point**: The point where the timing path ends, typically at the input of a flip-flop, latch, or an output port.

## 3. Explain following concepts:

### i. Launch Edge
The launch edge is the clock edge that triggers the data to leave the start point (usually a flip-flop or latch) and start propagating through the combinational logic towards the endpoint.

### ii. Capture Edge
The capture edge is the clock edge at the endpoint (usually a flip-flop or latch) that captures the propagated data. The data must arrive and be stable before this edge to ensure proper functionality.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/c8b8f130-33a7-42d5-b474-4834b8da4d92)

- The data is launched on the launch edge and must be captured by the capture edge.

### iii. Reset Assertion
Reset assertion refers to the activation of the reset signal in a digital circuit, which forces certain components (like flip-flops and latches) into a known state, usually zero.

### iv. Reset De-assertion
Reset de-assertion refers to the deactivation of the reset signal, allowing the circuit components to return to normal operation and start responding to clock signals and data inputs.

### v. Critical Path
The critical path is the longest timing path in a circuit, determining the maximum clock frequency at which the circuit can operate without timing violations. It dictates the overall performance of the digital system.

### vi. False Path
A false path is a timing path that does not need to meet timing requirements because it does not affect the functional operation of the circuit. These paths can be ignored during timing analysis to avoid unnecessary timing constraints.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/baf8f9c7-a446-4fa4-9f8d-210bf8fdea86)

Falsepath between two MUX

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/55e174d0-2bfb-420c-b68f-e8afbd70d348)

Falsepath between two flops

### vii. Multicycle Path
A multicycle path is a timing path that is designed to take multiple clock cycles to propagate data from the start point to the endpoint. This is typically used to reduce the complexity of certain operations that cannot be completed within a single clock cycle.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/c9def72d-6faa-4859-8136-cd9015b2efe0)

- The data launched on one clock cycle is intended to be captured multiple clock cycles later.


