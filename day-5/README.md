# 100 Days Verification Challenge - Day 5

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
\[ F = \text{MUX}(W0, W1, S3) \]
Where \( W0 \) and \( W1 \) are the outputs from the third stage.
