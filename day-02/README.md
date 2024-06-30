# 100 Days Verification Challenge - Day 2 - Logic Gates

## 1. Which are basic logic gates? Explain working with truth table. 

### Types of Basic Logic Gates:
- AND Gate: In the AND gate, the output of an AND gate attains state 1 if and only if all the inputs are in state 1. The Boolean expression of AND gate is Y = A.B.
  
 ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/c265e776-880b-404f-a7b5-206261aa6a67)

  - Truth Table:
    
![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/12f4a3ac-e104-4588-b183-c7f88b168377)
    
- OR Gate: In an OR gate, the output of an OR gate attains state 1 if one or more inputs attain state 1. The Boolean expression of the OR gate is Y = A + B, read as Y equals A ‘OR’ B.
  
  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/3d7d719c-ef5b-474a-8c51-a6f0b22599b4)

  - Truth Table:
    
![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/1dedf028-bbe2-416e-8c67-65b108b1e84d)

- NOT Gate: In a NOT gate, the output of a NOT gate attains state 1 if and only if the input does not attain state 1. The Boolean expression is

  ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/5764d153-f093-4b65-9467-a9ec60c9943e)

  It is read as Y equals NOT A.

 ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/62f7d8ba-5670-45f3-abe0-f71fa97782a3)

  - Truth Table:

 ![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/37511c50-4fb6-4b59-8051-f283ad266324)


## 2. Why are NAND & NOR called the Universal Gates? What are advantages of universal gates.

### Universal Gates:
- NAND Gate: Can be used to construct any other logic gate, including AND, OR, and NOT gates.
- NOR Gate: Similarly, can be used to construct any other logic gate.

### Advantages of Universal Gates:
- Simplifies circuit design by reducing the number of different gate types needed.
- Can lead to more efficient and cost-effective implementations in digital circuits.

## 3. Design 4:1 MUX Using Universal Gates

- Truth Table:
  
![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/28722cc5-303b-4abc-8096-ee4d458cf4fb)
  
### a. Using NAND Gates:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/b9bd7d05-99eb-4dd4-b7e7-6df0c7f83e44)

### b. Using NOR Gates:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/bda7becf-a094-4519-9b3a-1df3470d302b)

## 4. What are the applications of NAND & NOR Gates?

### a. NAND Gate Applications:
- Used in memory circuits.
- Implementing arithmetic functions.

### b. NOR Gate Applications:
- Used in digital clocks.
- Building control circuits.

## 5. Design OR, AND, XOR, NOT Using Universal Gates

### a. Using NAND Gates:

#### AND Gate Using NAND

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/753fe160-c507-44e4-9fcb-a4ef7055a30e)

#### OR Gate Using NAND

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/53ac0da0-d3c3-46b5-a7c7-a1d2bb60204e)

#### XOR Gate Using NAND

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/4c2c3046-829d-4a11-b5ad-e2c4e97b52e3)

#### NOT Gate Using NAND

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/a6e95f1d-8622-4549-98b1-4255cff6a265)

### b. Using NOR Gates:

#### AND Gate Using NOR

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/cf62fe0d-2df9-4fc5-8635-74ef0f46e4fa)

#### OR Gate Using NOR

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/0fd5378d-6aa1-445d-b183-5037a43b9b78)

#### XOR Gate Using NOR

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/3d87d38f-20a4-4a46-aa6f-4b43443722d7)

#### NOT Gate Using NOR

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/4229701c-b69e-4d35-bf8a-26126d128f64)

## 6. Design below logic using logic gates:

### a. Inverter:
The inverter, often referred to as a NOT gate, is a logic device that has an output opposite of the input. It is sometimes called a negator. It may be used alone or in combination with other logic devices to fulfill equipment requirements. If we apply signal A to the input of the inverter as shown in the figure below, then the output f will be the opposite of the input. At times t0 through t2, A is LOW. Consequently, the output is HIGH. At t2, A goes HIGH and as a result f goes LOW. f remains LOW as long as A is HIGH and vice versa. The output of an inverter will be the complement of the input. The Boolean expression for the output of this gate is f = A.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/fcfaaf6a-7411-45aa-b603-3f51be512e84)

### b. Full Adder:
Full Adder is the adder that adds three inputs and produces two outputs. The first two inputs are A and B and the third input is an input carry as C-IN. The output carry is designated as C-OUT and the normal output is designated as S which is SUM. The C-OUT is also known as the majority 1’s detector, whose output goes high when more than one input is high. A full adder logic is designed in such a manner that can take eight inputs together to create a byte-wide adder and cascade the carry bit from one adder to another. we use a full adder because when a carry-in bit is available, another 1-bit adder must be used since a 1-bit half-adder does not take a carry-in bit. A 1-bit full adder adds three operands and generates 2-bit results.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/a857622b-05ee-4075-80f9-075569c8381e)

Full Adder Truth Table:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/29ba737d-1282-4d3e-94d9-d5d7683f7c6b)

Logical Expression for SUM: = A’ B’ C-IN + A’ B C-IN’ + A B’ C-IN’ + A B C-IN = C-IN (A’ B’ + A B) + C-IN’ (A’ B + A B’) = C-IN XOR (A XOR B) = (1,2,4,7) 

Logical Expression for C-OUT: = A’ B C-IN + A B’ C-IN + A B C-IN’ + A B C-IN = A B + B C-IN + A C-IN = (3,5,6,7) 

Another form in which C-OUT can be implemented: = A B + A C-IN + B C-IN (A + A’) = A B C-IN + A B + A C-IN + A’ B C-IN = A B (1 +C-IN) + A C-IN + A’ B C-IN = A B + A C-IN + A’ B C-IN = A B + A C-IN (B + B’) + A’ B C-IN = A B C-IN + A B + A B’ C-IN + A’ B C-IN = A B (C-IN + 1) + A B’ C-IN + A’ B C-IN = A B + A B’ C-IN + A’ B C-IN = AB + C-IN (A’ B + A B’) 

Therefore COUT = AB + C-IN (A EX – OR B) 

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/fc83f08e-e37c-4aaa-ab0d-67cfce6a51b7)

Implementation of Full Adder using NAND gates:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/6eea2807-3cad-481f-a304-83f1edd11ac8)

Implementation of Full Adder using NOR gates: 

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/48b3a014-f1df-4bb7-a707-2506380c4b9c)

## 7. What happens if more than one input is applied to a logic gate?

Adding more input terminals to a logic gate increases the number of input state possibilities. With a single-input gate such as the inverter or buffer, there can only be two possible input states: either the input is “high” (1) or it is “low” (0).

