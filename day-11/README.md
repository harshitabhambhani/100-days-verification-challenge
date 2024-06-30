# 100 Days Verification Challenge - Day 11 - Miscellaneous Digital Electronics FAQs

## 1. Design a BCD to Gray Code Converter

To design a BCD (Binary-Coded Decimal) to Gray Code converter, you need to map each BCD digit to its corresponding Gray Code. BCD is a binary encoding of decimal numbers where each decimal digit is represented by a four-bit binary number. Gray Code is a binary numeral system where two successive values differ in only one bit.

Here are the steps:

1. Write the BCD numbers from 0 to 9.
2. Convert each BCD number to its corresponding Gray Code.

### Conversion Table

| Decimal | BCD  | Gray Code |
|---------|------|-----------|
| 0       | 0000 | 0000      |
| 1       | 0001 | 0001      |
| 2       | 0010 | 0011      |
| 3       | 0011 | 0010      |
| 4       | 0100 | 0110      |
| 5       | 0101 | 0111      |
| 6       | 0110 | 0101      |
| 7       | 0111 | 0100      |
| 8       | 1000 | 1100      |
| 9       | 1001 | 1101      |

### Boolean expression for each BCD bits can be written as

D3= m(8, 9)
D2= m(4, 5, 6, 7, 8, 9)
D1= m(2, 3, 4, 5)
D0= m(1, 2, 5, 6, 9)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/fa30f480-8121-46a5-8e58-8f87390306b8)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/9d2208f3-5c07-4717-a6aa-bb673fb42cfb)

## 2. Fundamental Properties of Boolean Algebra

The fundamental properties of Boolean algebra include:

- **Commutative Law**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/66790646-c097-4bb6-82c0-6af0abb49daa)

- **Associative Law**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/b00cd9d1-c475-4646-920a-8c9301be469d)

- **Distributive Law**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/c6a5134c-9b3a-45e9-b721-73b6b4924fe2)

- **Identity Law**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/4c8a2fe4-f415-4a9b-8645-7ed463fd475e)

- **Null Law**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/97be7bd3-e6e6-40fd-95b1-9d394dbc84a0)

- **Idempotent Law**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/07a5f82e-5d4d-4a1e-b4e3-1cb2dc961bb9)

- **Inverse Law**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/6a5e23ab-7957-4792-a200-694886e2973a)

- **Absorption Law**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/f60fcd52-ec78-4290-97c4-6beb413ac466)

- **De Morgan's Theorem**:

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/b58a573f-815a-414e-99a4-14d9d0a1dabe)

## 3. Isomorphic Boolean Algebra

Isomorphic Boolean algebras are Boolean algebras that have the same structure, meaning there exists a one-to-one correspondence (bijection) between the elements of the two algebras that preserves the operations of conjunction (AND), disjunction (OR), and negation (NOT). Essentially, two Boolean algebras are isomorphic if they are structurally identical.

## 4. Synchronizer

A synchronizer is a circuit used to mitigate metastability in digital systems when signals are transferred between different clock domains. It ensures that data transitions from one clock domain to another without causing unpredictable behavior. The simplest synchronizer consists of two flip-flops connected in series, clocked by the destination clock.

## 5. Design a Sequence Detector that Detects 1X1X? (Overlap)

To design a sequence detector that detects the pattern "1X1X" (where X can be 0 or 1) with overlapping, you can use a state machine.

### State Diagram

1. **State 0**: Initial state.
2. **State 1**: Detected '1'.
3. **State 2**: Detected '1X'.
4. **State 3**: Detected '1X1'.
5. **State 4**: Final state when '1X1X' is detected.

The state transitions depend on the input bits and the previous state. This can be implemented using D flip-flops and combinational logic.

## 6. 4-bit Linear Feedback Shift Register (LFSR)

A 4-bit LFSR is a shift register where the input bit is a linear function of its previous state. 

### Circuit Diagram

```plaintext
 +---+    +---+    +---+    +---+
 | D |--->| Q |--->| Q |--->| Q |--->| Q |
 +---+    +---+    +---+    +---+
     ^           ^      |      ^
     |___________|      |______|
```

- Tap positions are often chosen to ensure maximum length sequences. For a 4-bit LFSR, a common configuration is using taps at positions 4 and 3 (i.e., feedback from Q3 and Q4).

## 7. 4-bit Barrel Shifter using MUX

A barrel shifter is used for shifting or rotating the bits of a binary number. 

### Circuit Diagram

A 4-bit barrel shifter can be designed using four 4-to-1 multiplexers (MUX). Each MUX selects one of the four input bits based on the control signals to determine the shift amount.

## 8. Design a PISO Shift Register

A Parallel In Serial Out (PISO) shift register takes parallel data inputs and shifts them out serially.

### Circuit Diagram

- Load the parallel data into the shift register.
- Use a clock to shift out the data bit-by-bit serially.
- Use a control signal to switch between parallel load and serial shift mode.

```plaintext
Parallel Inputs:  D3, D2, D1, D0
Shift Register:   Q3, Q2, Q1, Q0
                 _______
Load/Shift ----->|   |   |
Clock ---------->|---|   |
                 |___|___|
                   |
                   |
                 Serial Out
```
