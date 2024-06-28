### 1. What is a Buffer? What are its applications?

A buffer is a digital circuit that provides isolation and strength to a signal. It amplifies the input signal, allowing it to drive larger loads without degrading the signal integrity.

Applications of Buffers:
- Signal Amplification: Buffers can strengthen weak signals to ensure they can drive the next stage in a circuit.
- Isolation: Buffers provide electrical isolation between different stages of a circuit, preventing interactions that might cause signal degradation.
- Delay Elements: Buffers can be used to introduce delays in signal propagation.
- Driving Loads: Buffers can drive loads with higher current requirements than the originating circuit can provide.

### 2. What is a Tri-State Buffer?

A tri-state buffer is a type of buffer that can exist in three states:
- High (1)
- Low (0)
- High-Impedance (Z): In this state, the buffer effectively disconnects from the circuit, allowing multiple outputs to share the same connection point without interfering with each other.

Tri-state buffers are commonly used in bus systems where multiple devices need to connect to a common data bus without interfering with each other.

### 3. What is the Difference Between NAND and Negative Input AND Gate?

A NAND gate is a digital logic gate that produces a low output (0) only when all its inputs are high (1); otherwise, it produces a high output (1).

A negative input AND gate (also known as a NAND gate with active-low inputs) is a gate where the inputs are inverted before being fed into a NAND gate. This means that a negative input AND gate will have the same truth table as a NAND gate but with inverted input logic.

### 4. What is Pull-Up & Pull-Down Network?

- Pull-Up Network (PUN): This network is used to ensure that a signal line is pulled up to a high logic level (1) when no other active device is pulling it low. It typically involves a resistor connected between the signal line and the positive supply voltage.
- Pull-Down Network (PDN): This network ensures that a signal line is pulled down to a low logic level (0) when no other active device is pulling it high. It typically involves a resistor connected between the signal line and the ground.

These networks are crucial in ensuring that a signal line does not float and remains at a defined logic level.

### 5. Design a Full Adder Using NAND Gates ONLY

A full adder can be designed using NAND gates by breaking down the full adder logic into simpler NAND gate implementations:

Full Adder Logic:
- Sum = A ⊕ B ⊕ Cin
- Carry = AB + Cin(A ⊕ B)

Using only NAND gates, we can construct XOR and AND gates:

- XOR using NAND:
