# 100 Days Verification Challenge - Day 5 - Multiplexer and Demultiplexer

## 1. Design 16:1 MUX using 2:1 MUX

To design a 16:1 MUX using 2:1 MUX, we can use a hierarchical approach by combining several 2:1 MUXes in multiple stages.

Step-by-Step Design:

1. First Stage: Use eight 2:1 MUXes to select 8 groups of 2 inputs each.
2. Second Stage: Use four 2:1 MUXes to select from the outputs of the first stage.
3. Third Stage: Use two 2:1 MUXes to select from the outputs of the second stage.
4. Fourth Stage: Use one 2:1 MUX to select from the outputs of the third stage.

### Diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/ef3a1364-30e6-4746-9a04-3a1986b5de15)


```
    Inputs: D0 to D15
    Select lines: S3, S2, S1, S0

    First Stage:
    MUX0: (D0, D1), S0 -> Y0
    MUX1: (D2, D3), S0 -> Y1
    MUX2: (D4, D5), S0 -> Y2
    MUX3: (D6, D7), S0 -> Y3
    MUX4: (D8, D9), S0 -> Y4
    MUX5: (D10, D11), S0 -> Y5
    MUX6: (D12, D13), S0 -> Y6
    MUX7: (D14, D15), S0 -> Y7

    Second Stage:
    MUX8: (Y0, Y1), S1 -> Z0
    MUX9: (Y2, Y3), S1 -> Z1
    MUX10: (Y4, Y5), S1 -> Z2
    MUX11: (Y6, Y7), S1 -> Z3

    Third Stage:
    MUX12: (Z0, Z1), S2 -> W0
    MUX13: (Z2, Z3), S2 -> W1

    Fourth Stage:
    MUX14: (W0, W1), S3 -> Output (F)
```

### Output Equation:
F = MUX(W0, W1, S3)
Where W0 and W1 are the outputs from the third stage.

## 2. Design D-FF using MUX

A D Flip-Flop (D-FF) can be designed using a MUX to select between the current input (D) and the previous output (Q) based on the clock signal.

### Diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/a0736ed9-e92c-4d30-95e7-141c1785ba3d)

### Working:

- The MUX selects between the input D and the current state Q.
- When CLK is high, the MUX selects D.
- When CLK is low, the MUX selects Q.

### Truth Table:

| CLK | Input to MUX | Q (Next State) |
|-----|--------------|----------------|
|  0  |      Q       |        Q       |
|  1  |      D       |        D       |

## 3. Design a 1:2 DEMUX that can be used as an Inverter and Buffer

A 1:2 DEMUX can be designed to act as both an inverter and a buffer by controlling the select line.

### Diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/948a1bc6-4d9b-47cd-8bf9-ba6dd4c79948)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/8a97585f-db36-4907-8173-6436578ec7e7)

### Logic:

- If S = 0, A = I (acts as a buffer).
- If S = 1, B = ¬I (acts as an inverter).

### Implementation:

- A = I AND ¬S
- B = I AND S

## 4. Design NAND Gate using 1:2 DEMUX

To design a NAND gate using a 1:2 DEMUX, we use the select lines as inputs A and B, and the input I is connected to logic 1.

### Diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/ce4a080a-ab22-4e82-8b56-4706d5f50b61)

### Truth Table:

| A | B | Y (NAND) |
|---|---|----------|
| 0 | 0 |    1     |
| 0 | 1 |    1     |
| 1 | 0 |    1     |
| 1 | 1 |    0     |

### Connections:

- Connect the select lines A and B to the inputs of the DEMUX.
- Connect the input I to logic 1.
- The output corresponding to A=1, B=1 (Y3) will give the NAND output.

## 5. Difference between Decoder and Demux

### Decoder:
- Converts binary information from n input lines to a maximum of \(2^n\) unique output lines.
- Used for decoding encoded data.

### Demultiplexer (Demux):
- Takes a single input and routes it to one of \(2^n\) output lines based on select lines.
- Used for data distribution.


## 6. If D0 input of a 2:1 MUX is connected to ground, what is the output?

- If D0 is connected to ground (0) and depending on the select line (S):
  - If S = 0, the output will be 0 (ground).
  - If S = 1, the output will be D1.

## 7. If D1 input of a 2:1 MUX is connected to 1, what is the output?

- If D1 is connected to logic 1 and depending on the select line (S):
  - If S = 0, the output will be D0.
  - If S = 1, the output will be 1.

## 8. Applications of:

### a. Multiplexer

- Data Selection: Selects data from multiple sources and routes it to a single line.
- Communication Systems: Combines multiple signals for transmission over a single line.
- Arithmetic Operations: Used in ALUs for selecting different operations.
- Signal Routing: Directs signals in digital circuits and systems.

### b. Demultiplexer

- Data Distribution: Routes data from a single source to multiple destinations.
- Communication Systems: Distributes received data to different destinations.
- Memory Access: Selects specific memory locations or devices in computer systems.
- Signal Demultiplexing: Splits a single data stream into multiple streams for further processing.
