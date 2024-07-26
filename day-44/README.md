# 100 Days Verification Challenge - Day 44 - Verilog Ports

## 1. What are the different approaches of connecting ports in a hierarchical design? What are the pros and cons of each?

### Positional (Ordered) Port Connections
- **Pros:**
  - Simple and concise.
  - Less verbose, which can make the code more readable.
- **Cons:**
  - Order of the ports must be memorized or looked up.
  - Harder to maintain and debug, especially if the module has many ports.

### Named (Keyword) Port Connections
- **Pros:**
  - More readable and self-documenting.
  - Easier to manage and less error-prone, especially for modules with many ports.
  - Order of ports does not matter.
- **Cons:**
  - More verbose than positional connections.

### Mixed Port Connections
- **Pros:**
  - Can leverage both positional and named advantages.
- **Cons:**
  - Can be confusing if not used consistently.

## 2. Can there be full or partial no-connects to a multi-bit port of a module during its instantiation?

Yes, you can have full or partial no-connects to a multi-bit port during its instantiation. 
- For full no-connects, you can use the `.` notation with an empty connection.
- For partial no-connects, you can connect only the required bits and leave the rest unconnected.

## 3. What happens to the logic after synthesis, that is driving an unconnected output port that is left open (that is, no connect) during its module instantiation?

The logic driving an unconnected output port is typically optimized away during synthesis because it has no impact on the functionality of the design. Synthesis tools remove any logic that does not contribute to the output of the design.

## 4. What value is sampled by the logic from an input port that is left open (that is, no-connect) during its module instantiation?

If an input port is left open, the value sampled can be unpredictable. It might be 'x' (unknown) in simulation or might be optimized away in synthesis. Some tools may also default the value to zero.

## 5. How is the connectivity established in Verilog when connecting wires of different widths?

When connecting wires of different widths:
- If the source wire is wider than the destination, the higher-order bits are truncated.
- If the source wire is narrower than the destination, the higher-order bits of the destination are typically padded with zeros.

## 6. Can you use a Verilog function to define the width of a multi-bit port, wire, or reg type?

Yes, you can use a Verilog function to define the width of a multi-bit port, wire, or `reg` type. This allows you to parameterize your module and make it more flexible.

```verilog
function integer get_width;
  input integer value;
  begin
    get_width = $clog2(value + 1);
  end
endfunction
```

## 7. Create a bi-directional net with assignments influencing both source and destination.

Creating a bi-directional net requires the use of `inout` ports and proper tri-state buffer logic.

```verilog
module bidir(inout wire bus);
  reg data_out;
  wire data_in;

  assign bus = (/* condition */) ? data_out : 'bz;
  assign data_in = bus;

  // Other logic...
endmodule
```

## 8. What if multiple procedural assignments made to the same reg variable in an always block?

If multiple procedural assignments are made to the same `reg` variable within an `always` block, the last assignment in the block will override previous assignments. This can lead to unintended behavior and should be avoided.

## 9. What will be the result of this instantiation? 

```verilog
module adder;
  reg A, B, C_IN, SUM;
  wire C_OUT;

  1_bit_adder fal(SUM, C_OUT, A, B, C_IN); // Instantiate 1_bit_adder, call it fal

  // <stimulus>
endmodule
```
(Hint: o/p port SUM in fal is connected to reg variable SUM in module adder)

Here, the output port `SUM` of the instantiated `1_bit_adder` module is connected to the `SUM` `reg` in the `adder` module. This means any value assigned to `SUM` inside `1_bit_adder` will be reflected in the `SUM` `reg` of `adder`. The connection is valid and will work as expected if proper assignments are made within `1_bit_adder`.

