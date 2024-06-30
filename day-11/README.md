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

To design a sequence detector that detects the sequence 1X1X, where X can be either 0 or 1, you can use a Moore machine. A Moore machine is a finite state machine that produces an output based on the current state of the machine, rather than on the input and the current state, as in a Mealy machine.

Here is an example of a Moore machine that detects the sequence 1X1X:

| Current State | Input | Next State | Output |
|---------------|-------|------------|--------|
| S0            | 0     | S0         | 0      |
| S0            | 1     | S1         | 0      |
| S1            | 0     | S2         | 0      |
| S1            | 1     | S3         | 0      |
| S2            | 0     | S2         | 0      |
| S2            | 1     | S3         | 0      |
| S3            | 0     | S0         | 1      |
| S3            | 1     | S1         | 1      |

In this Moore machine, there are four states: S0, S1, S2, and S3. The sequence 1X1X is detected when the machine is in state S3 and the input is either 0 or 1. The output is produced when the sequence is detected.

The Moore machine has the advantage of being easier to design and implement, since the output is produced based on the current state only. However, it may be slower than a Mealy machine, since the output is produced after the input has been processed and the next state has been determined.

## 6. 4-bit Linear Feedback Shift Register (LFSR)

A linear feedback shift register (LFSR) is a digital circuit that can be used to generate a sequence of binary numbers. It is called a linear feedback shift register because it uses a linear feedback function to determine the next number in the sequence.

A 4-bit LFSR is a shift register that consists of 4 flip-flops and a feedback function. The output of each flip-flop is fed back to the input of the first flip-flop, and the feedback function determines which flip-flop outputs are combined to form the input of the first flip-flop.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/efe5be59-44b7-4d7f-9139-741c22377e29)

To design a 4-bit LFSR, we can use D flip-flops and logic gates. Here is one way to do it:

- Use four D flip-flops to create the 4-bit shift register. These flip-flops will be connected in a chain, with the output of each flip-flop connected to the input of the next flip-flop.

- Connect the clock input of the first flip-flop to the clock input of the other flip-flops. This will ensure that all of the flip-flops are clocked at the same time.

- Use an XOR gate to create the feedback function. The XOR gate will have two inputs, one connected to the output of the first flip-flop and the other connected to the output of the third flip-flop. The output of the XOR gate will be connected to the input of the first flip-flop.

- Connect the reset input of each flip-flop to a reset line. This will allow you to reset the LFSR to a known state when necessary.

The output of the flip-flops will form the 4-bit output of the LFSR, and the clock input will control the shifting. When the clock input is high, the flip-flops will shift the data one bit to the right and the feedback function will determine the new value of the first flip-flop. When the reset input is high, all of the flip-flops will be reset to zero.

### LFSR Verilog Code

'''
module LFSR(input clk, rst, output reg [3:0] op);
  always@(posedge clk) begin
    if(rst) op <= 4'hf;
    else op = {op[2:0],(op[3]^op[2])};
  end
endmodule
'''

### Testbench Code

'''
module TB;
  reg clk, rst;
  wire [3:0]op;
  
  LFSR lfsr1(clk, rst, op);
  
  initial begin
    $monitor("op=%b",op);
    clk = 0; rst = 1;
    #5 rst = 0;
    #50; $finish;
  end
  
  always #2 clk=~clk;
  
  initial begin 
    $dumpfile("dump.vcd"); $dumpvars;
  end
endmodule
'''

### Output will look something like this:

'''
op=xxxx
op=1111
op=1110
op=1100
op=1000
op=0001
op=0010
op=0100
op=1001
op=0011
op=0110
op=1101
op=1010
op=0101
op=1011
'''

## 7. 4-bit Barrel Shifter using MUX

A barrel shifter is a digital circuit that can shift the bits of a binary word by a specified number of positions in a single clock cycle. It is often used in microprocessors to perform bit shifting and rotation operations efficiently.

A 4-bit barrel shifter uses multiplexers (MUXes) to select which bits of the input word should be shifted and placed in the output word. The number of MUXes used will depend on the size of the input and output words. For a 4-bit barrel shifter, four MUXes would be used, one for each bit position.

Here's an example of how a 4-bit barrel shifter using MUXes might work:

- The input to the barrel shifter is a 4-bit binary word, and the desired shift amount is specified as an input as well.

- The first MUX selects which bit should be placed in the first output bit position. If the shift amount is 0, the first MUX will select the first input bit. If the shift amount is 1, the first MUX will select the second input bit, and so on.

- The second MUX selects which bit should be placed in the second output bit position. If the shift amount is 0, the second MUX will select the second input bit. If the shift amount is 1, the second MUX will select the third input bit, and so on.

- The third and fourth MUXes work in a similar manner to select the bits for the third and fourth output bit positions.

The shift amount can be any value from 0 to 3, so the MUXes will select different input bits depending on the shift amount. For example, if the input word is "1001" and the shift amount is 2, the output word would be "0010" because the first and second MUXes would select the third and fourth input bits, respectively.

### Circuit diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/abf67702-42aa-43e9-82b2-2c16cea95ec0)

### Truth Table

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/feda52d9-ccc9-4ded-9d55-d8c75468b7d1)

## 8. Design a PISO Shift Register

A PISO (Parallel In, Serial Out) shift register is a digital circuit that can be used to convert parallel data to serial data. It is called a PISO shift register because it accepts parallel data on its input and shifts it out serially on its output.

### Circuit diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/77d1d379-e603-47d5-b69c-e5afc2ebe8ee)

To design a PISO shift register, we can use flip-flops and logic gates. Here is one way to do it:

- Use N D flip-flops to create the shift register. These flip-flops will be connected in a chain, with the output of each flip-flop connected to the input of the next flip-flop. The number of flip-flops will determine the size of the shift register (i.e. the number of bits it can store).

- Connect the clock input of the first flip-flop to the clock input of the other flip-flops. This will ensure that all of the flip-flops are clocked at the same time.

- Use an AND gate to create the load signal. The AND gate will have one input for each flip-flop, and the output of the AND gate will be connected to the load input of each flip-flop.

- Connect the data inputs of the flip-flops to the parallel data inputs of the shift register. These inputs will be used to load data into the shift register.

- Connect the serial output of the shift register to the output of the last flip-flop. This output will shift out the data stored in the shift register one bit at a time.

The output of the flip-flops will form the serial output of the shift register, and the clock input will control the shifting. When the clock input is high and the load input is low, the flip-flops will shift the data one bit to the right. When the load input is high, the data inputs will be loaded into the flip-flops.
