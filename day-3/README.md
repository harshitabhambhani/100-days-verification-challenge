### 1. Design & Explanation

#### a. BCD to Decimal Encoder

A BCD (Binary-Coded Decimal) to Decimal encoder converts a 4-bit binary input representing a decimal digit (0-9) into a corresponding single active output line. 

Working:
1. Inputs: BCD (A3, A2, A1, A0) where A3 is the most significant bit (MSB) and A0 is the least significant bit (LSB).
2. Outputs: Decimal (D0 to D9), where each output line corresponds to a decimal digit (0 to 9).

Truth Table:

| A3 | A2 | A1 | A0 | D0 | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| 0  | 0  | 0  | 0  | 1  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |
| 0  | 0  | 0  | 1  | 0  | 1  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |
| 0  | 0  | 1  | 0  | 0  | 0  | 1  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |
| 0  | 0  | 1  | 1  | 0  | 0  | 0  | 1  | 0  | 0  | 0  | 0  | 0  | 0  |
| 0  | 1  | 0  | 0  | 0  | 0  | 0  | 0  | 1  | 0  | 0  | 0  | 0  | 0  |
| 0  | 1  | 0  | 1  | 0  | 0  | 0  | 0  | 0  | 1  | 0  | 0  | 0  | 0  |
| 0  | 1  | 1  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 1  | 0  | 0  | 0  |
| 0  | 1  | 1  | 1  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 1  | 0  | 0  |
| 1  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 1  | 0  |
| 1  | 0  | 0  | 1  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 1  |

Logic Circuit:
- Each output line (D0 to D9) is driven by an AND gate combination of the input lines (A3 to A0).
- For example, D0 is activated when A3, A2, A1, and A0 are all 0. D1 is activated when A3, A2, and A1 are 0, and A0 is 1, etc.
