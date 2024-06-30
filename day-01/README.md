# 100 Days Verification Challenge - Day 1 - Flip flops and Latches

## 1. Explain Functioning of JK & SR Flip-Flop

### SR Flip-Flop
The SR (Set-Reset) flip-flop is a type of sequential logic circuit. It has two inputs, S (set) and R (reset), and two outputs, Q and Q'. The functioning is as follows:
- When S=1 and R=0, Q is set to 1.
- When S=0 and R=1, Q is reset to 0.
- When S=0 and R=0, Q retains its previous state.
- When S=1 and R=1, the output is undefined.

### JK Flip-Flop
The JK flip-flop is an improvement over the SR flip-flop that eliminates the undefined state. It has inputs J, K, and clock (CLK):
- When J=1 and K=0, Q is set to 1.
- When J=0 and K=1, Q is reset to 0.
- When J=0 and K=0, Q retains its previous state.
- When J=1 and K=1, Q toggles its state.

## 2. Difference Between Flip-Flop & Latch

- Latch: A latch is a level-sensitive device that changes state as long as the control signal (enable) is active. It continuously responds to its inputs as long as the enable signal is present.
- Flip-Flop: A flip-flop is an edge-sensitive device that changes state only at the edge (rising or falling) of the control signal (clock). It only responds to its inputs at the moment of a clock transition.

## 3. Why Are Latches Faster than Flip-Flops?

Latches are faster than flip-flops because they are level-sensitive and do not wait for a clock edge to change their state. This allows them to respond immediately to input changes as long as the enable signal is active.

## 4. Explain the Use of Flip-Flops and Latches

### Flip-Flop
Flip-flops are used in applications where precise timing control is essential. They are commonly found in:
- Registers
- Counters
- Memory devices
- Synchronous circuits

### Latch
Latches are used in applications where immediate response to input changes is required. They are commonly found in:
- Asynchronous circuits
- Temporary storage within digital circuits
- Data synchronization

## 5. Why is the Gated SR Flip-Flop Called Asynchronous Latch?

The Gated SR Flip-Flop includes an enable input that controls when the flip-flop can change state. It is called an asynchronous latch because it operates based on the enable signal, making it independent of the clock signal, and thus asynchronous with the system clock.

## 6. Implement D Flip-Flop Using NAND Gates

A D Flip-Flop can be implemented using NAND logic gates by performing the following steps:

1.	Connect two NAND gates in a cross-coupled arrangement, with the output of each gate connected to the input of the other gate.
2.	Connect the D input to one of the NAND gates' inputs.
3.	Connect a clock input to both NAND gates' inputs, with the clock signal flipped by an inverter to one of the inputs.
4.	Connect an enable input to both NAND gates' inputs, with the enable signal flipped by an inverter to one of the inputs.

Circuit Diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/bda778bb-8527-4a6d-83ca-0f7be0b55c24)

The resulting circuit will be a D FLip-Flop made up of NAND gates, and the output states will be as follows:

1. When Enable=0, the output of each NAND gate will be 1, and the flip-flop will retain its previous state.
2. When Enable=1 and Clock transitions from low to high, the input D is latched at the output Q of the flip-flop.
3. When Enable=1 and Clock transitions from high to low, the output Q of the flip-flop remains at the last latched D input.

## 7. Design D Flip-Flop Using 2:1 MUX

Truth Table of D FLip-Flop:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/757182a3-a890-4544-830f-e48067885409)

Circuit Diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/d41b298d-7286-46e7-9745-affd9dba4cad)

1. Multiplexer Connections:
   - Use two 2:1 multiplexers for the design.
   - Connect the D input to input 0 of both multiplexers.
   - Connect the output of the first multiplexer to input 1 of the second multiplexer, creating a feedback loop.

2. Clock Signal:
   - Connect the clock input to the select input of both multiplexers. This ensures that the clock signal controls the selection of inputs in the multiplexers.

3. Output:
   - The outputs of the multiplexers form the Q output of the flip-flop. This output represents the stored value of the D input.

4. Operation:
   - When the clock input is high (1), the multiplexers select the D input as their output, meaning the output follows the value of the D input.
   - When the clock input is low (0), the multiplexers select their own outputs as the output of the flip-flop, meaning the stored value is maintained.
