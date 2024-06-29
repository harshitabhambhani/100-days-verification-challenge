# 100 Days Verification Challenge - Day 8

## 1. What is a Buffer? What are its applications?

A buffer is a digital circuit that provides isolation and strength to a signal. It amplifies the input signal, allowing it to drive larger loads without degrading the signal integrity.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/1867ea9f-3015-4052-aa8d-dff595cf61fe)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/e4938e9f-8477-469c-be31-f359a4d762b4)

Applications of Buffers:
- Signal Amplification: Buffers can strengthen weak signals to ensure they can drive the next stage in a circuit.
- Isolation: Buffers provide electrical isolation between different stages of a circuit, preventing interactions that might cause signal degradation.
- Delay Elements: Buffers can be used to introduce delays in signal propagation.
- Driving Loads: Buffers can drive loads with higher current requirements than the originating circuit can provide.

## 2. What is a Tri-State Buffer?

A tri-state buffer is a type of buffer that can exist in three states:
- High (1)
- Low (0)
- High-Impedance (Z): In this state, the buffer effectively disconnects from the circuit, allowing multiple outputs to share the same connection point without interfering with each other.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/3d8a6aec-4c1e-43b1-9e4b-93a92790fe37)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/c0823714-2dd0-47e2-8974-5fbcd1601a97)

Tri-state buffers are commonly used in bus systems where multiple devices need to connect to a common data bus without interfering with each other.

## 3. What is the Difference Between NAND and Negative Input AND Gate?

A NAND gate is a digital logic gate that produces a low output (0) only when all its inputs are high (1); otherwise, it produces a high output (1).

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/87d0a38a-c859-4f1b-9e2e-2c208d689c2d)

A negative input AND gate (also known as a NAND gate with active-low inputs) is a gate where the inputs are inverted before being fed into a NAND gate. This means that a negative input AND gate will have the same truth table as a NAND gate but with inverted input logic.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/cf3ac211-4279-4ff5-befe-d9fe615c3ab4)

## 4. What is Pull-Up & Pull-Down Network?

- Pull-Up Network (PUN): This network is used to ensure that a signal line is pulled up to a high logic level (1) when no other active device is pulling it low. It typically involves a resistor connected between the signal line and the positive supply voltage.
- Pull-Down Network (PDN): This network ensures that a signal line is pulled down to a low logic level (0) when no other active device is pulling it high. It typically involves a resistor connected between the signal line and the ground.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/d1a77c9b-1a51-46f9-9a17-380366f7e9c7)

These networks are crucial in ensuring that a signal line does not float and remains at a defined logic level.

## 5. Design a Full Adder Using NAND Gates ONLY

### BLock diagram of Full Adder:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/1f76321d-5653-4e86-9a1f-153c301b854f)

### Full Adder Logic:
- Sum = A ⊕ B ⊕ Cin
- Carry = AB + Cin(A ⊕ B)

### Full Adder using NAND Gates:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/f7984a03-25a8-4e96-9920-a2c2a6a935da)

### Logical Expression for Full Adder using NAND Gate

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/339f3713-166c-412c-81b2-513ba86e100b)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/a448462d-8727-4635-94ee-7c0fac58298d)

## 6. Explain the Working of a Full Subtractor

A full subtractor is a combinational circuit that performs subtraction of three bits: the minuend (A), subtrahend (B), and borrow-in (Bin). It produces two outputs: the difference (D) and the borrow-out (Bout).

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/05a657b0-3df9-4b5a-84ac-560af129a05a)

### Truth Table:
| A | B | Bin | D | Bout |
|---|---|-----|---|------|
| 0 | 0 |  0  | 0 |  0   |
| 0 | 0 |  1  | 1 |  1   |
| 0 | 1 |  0  | 1 |  1   |
| 0 | 1 |  1  | 0 |  1   |
| 1 | 0 |  0  | 1 |  0   |
| 1 | 0 |  1  | 0 |  0   |
| 1 | 1 |  0  | 0 |  0   |
| 1 | 1 |  1  | 1 |  1   |

From above table we can draw the K-Map as shown for “difference” and “borrow”.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/6dfa3b90-ab71-4ca0-a7c6-02388254f218)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/9d1c665a-ca89-435e-84d1-6bbcf52df8d3)

Logic Equations:

- Difference (D) =

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/870a5bb0-91db-44ef-8d85-3a4f5faa459b)

- Borrow-out (Bout) =

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/623d3ed3-ff50-4228-b53f-01a14d6e7919)

### Logic Circuit for Full Subtractor

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/a563d095-b32b-4be1-848b-a532a737dcd0)

## 7. Difference Between Ripple Carry Adder and Carry Look Ahead Adder

Ripple Carry Adder (RCA):
- Each bit's carry-out depends on the carry-in from the previous bit.
- Simple and easy to design.
- Slower due to the ripple effect of carry propagation through each bit.

Carry Look Ahead Adder (CLA):
- Uses a more complex logic to calculate carry bits in advance.
- Faster since it reduces the delay caused by the carry propagation.
- More complex and requires more gates compared to RCA.

## 8. Explain Comparator with Truth Table

A comparator is a combinational circuit that compares two binary values and determines their relationship (greater than, less than, or equal to).

2-Bit Comparator Truth Table:
| A1 | A0 | B1 | B0 | A > B | A = B | A < B |
|----|----|----|----|-------|-------|-------|
|  0 |  0 |  0 |  0 |   0   |   1   |   0   |
|  0 |  0 |  0 |  1 |   0   |   0   |   1   |
|  0 |  0 |  1 |  0 |   0   |   0   |   1   |
|  0 |  0 |  1 |  1 |   0   |   0   |   1   |
|  0 |  1 |  0 |  0 |   1   |   0   |   0   |
|  0 |  1 |  0 |  1 |   0   |   1   |   0   |
|  0 |  1 |  1 |  0 |   0   |   0   |   1   |
|  0 |  1 |  1 |  1 |   0   |   0   |   1   |
|  1 |  0 |  0 |  0 |   1   |   0   |   0   |
|  1 |  0 |  0 |  1 |   1   |   0   |   0   |
|  1 |  0 |  1 |  0 |   0   |   1   |   0   |
|  1 |  0 |  1 |  1 |   0   |   0   |   1   |
|  1 |  1 |  0 |  0 |   1   |   0   |   0   |
|  1 |  1 |  0 |  1 |   1   |   0   |   0   |
|  1 |  1 |  1 |  0 |   1   |   0   |   0   |
|  1 |  1 |  1 |  1 |   0   |   1   |   0   |

## 9. Design "Frequency Multiplier by 2" Circuit

A frequency multiplier by 2 can be designed using a phase-locked loop (PLL) or a simple edge detector circuit:

1. Using PLL:
   - The PLL locks onto the input frequency and its voltage-controlled oscillator (VCO) runs at twice the input frequency.

2. Using Edge Detector:
   - Use a D flip-flop clocked by the input signal to detect rising edges.
   - Connect the output of the D flip-flop to a clock doubling circuit which generates pulses at twice the input frequency.

