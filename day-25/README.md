# 100 Days Verification Challenge - Day 25 - STA Basics

## 1. What do you mean by clock skew and clock jitter?

### Clock Skew
Clock skew is the difference in timing between clock signals reaching different components of a digital circuit. This difference can cause synchronization issues where data might be incorrectly latched or propagated.

### Clock Jitter
Clock jitter refers to the variations in the timing of clock edges from their ideal positions. This can lead to timing errors as the clock signal deviates from its expected frequency, affecting the reliable operation of the circuit.

## 2. What are the different types of skews used in VLSI?

- **Local Skew**: The difference in arrival times of the clock signal at different flip-flops within a small area or module.
- **Global Skew**: The difference in arrival times of the clock signal at different flip-flops across the entire chip.
- **Intra-Clock Skew**: The skew within the same clock domain.
- **Inter-Clock Skew**: The skew between different clock domains.
- **Useful Skew**: When clock skew is intentionally used to improve the performance or meet timing constraints of the design.

## 3. What is slack in VLSI? What is negative slack & positive slack?

Slack is the difference between the required arrival time and the actual arrival time of a signal. It indicates how much margin there is before a timing constraint is violated.

### Negative Slack
Negative slack occurs when the actual arrival time of a signal exceeds the required arrival time, indicating a timing violation.

### Positive Slack
Positive slack occurs when the actual arrival time of a signal is earlier than the required arrival time, indicating that the timing constraint is met with some margin.

## 4. What are ideal characteristics of a clock during STA?

- **Zero Skew**: The clock reaches all parts of the circuit simultaneously.
- **Zero Jitter**: The clock edges are consistent with no variations.
- **Fixed Duty Cycle**: The high and low phases of the clock signal are equal.
- **Stable Frequency**: The clock frequency is constant and does not vary.
- **Minimal Latency**: The clock signal has minimal delay from the source to the destination.

## 5. Explain:

### i. Setup Time
Setup time is the minimum time before the clock edge that the data input to a flip-flop must be stable and valid to ensure it is correctly captured.

### ii. Hold Time
Hold time is the minimum time after the clock edge that the data input to a flip-flop must remain stable to ensure it is correctly captured.

### iii. Rise Time
Rise time is the time taken for a signal to change from a low voltage level (typically 10% of its maximum value) to a high voltage level (typically 90% of its maximum value).

### iv. Fall Time
Fall time is the time taken for a signal to change from a high voltage level (typically 90% of its maximum value) to a low voltage level (typically 10% of its maximum value).

## 6. How can you avoid setup & hold time violations?

### Setup Time Violations
- **Increase Clock Period**: Increasing the clock period provides more time for data to settle before the next clock edge.
- **Reduce Data Path Delay**: Optimize the logic in the data path to reduce delay.
- **Pipeline the Circuit**: Add intermediate registers to break long combinational paths into shorter ones.
- **Use Faster Cells**: Use faster combinational cells to reduce propagation delay.
- **Adjust Clock Skew**: Utilize useful skew to shift the clock edges favorably.

### Hold Time Violations
- **Add Delay Buffers**: Insert buffers in the data path to increase the delay.
- **Reduce Clock Skew**: Minimize the skew to ensure that the clock reaches all flip-flops simultaneously.
- **Use Slower Cells**: Use slower combinational cells to increase propagation delay if necessary.
- **Ensure Proper Circuit Design**: Design the circuit with sufficient hold time margins from the beginning to avoid violations.
