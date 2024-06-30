# 100 Days Verification Challenge - Day 7 - Sequence detector

## 1. FSM for Serial Two's Complement Block Detection

The two's complement of a binary number involves flipping all the bits and adding 1 to the least significant bit. An FSM to detect a serial two's complement block could look like this:

The main logic behind this is, start from the least significant bit and retain the bits until and first 1-bit has occurred. Once a 1-bit is found, start complementing the bits if 1 makes it 0 and if 0 make it 1. Note retain the first 1-bit. (Don’t complement it, complement the bit which follows that first 1-bit).

### State Assignment:

Let us assume State ‘a’ represents that 1 has not occurred yet. and assume State ‘b’ the situation after the first one has occurred. State flow diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/bd583158-4446-4432-a954-70bf84e13802)

## 2. FSM for Detecting Sequence 10110 (Overlapping)

(using Mealy FSM)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/d2541488-ee7a-4764-a3d1-5a50bda60656)

(using Moore FSM)

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/a61b14ba-ff23-40fc-9af4-f68c588573b6)

## 3. FSM for More Than One "1"s in Last 3 Samples

The idea is we need to design a complex sequence generator which will detect the patterns 011, 101, 110, and 111. Let us assume four different states
a = no 1 detected state.
b = one 1 detected state or 01 or 1 detected state.
c = two or more than two 1’s detected state.
d = 001/010 detected state. The FSM diagram is

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/ad573916-635e-42b6-9b83-ed118c1251a7)
