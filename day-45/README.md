# 100 Days Verification Challenge - Day 45 - RTL Design

## 1. What do conditional assignments get inferred into?

Conditional assignments in Verilog (using the `?:` operator) get inferred into multiplexers. For example:

```verilog
assign out = (sel) ? in1 : in0;
```

This will be synthesized into a 2-to-1 multiplexer, where `sel` determines which input (`in1` or `in0`) is passed to the output (`out`).

## 2. What is the logic that gets synthesized when conditional operators in a single continuous assignment are nested? 

When conditional operators are nested within a single continuous assignment, the logic synthesized resembles a tree of multiplexers. For example:

```verilog
assign out = (sel1) ? ((sel2) ? in1 : in2) : in3;
```

This would be synthesized into a hierarchy of multiplexers, where the selection of inputs depends on the values of `sel1` and `sel2`.

## 3. Why should a nonblocking assignment be used for sequential logic, and what would happen if a blocking assignment were used? Compare it with the same code in a combinational block.

- **Nonblocking Assignments (`<=`):**
  - Used for sequential logic (e.g., in `always` blocks triggered by clock edges).
  - Ensures all assignments within a block are evaluated before any updates are made.
  - Prevents race conditions and ensures proper timing behavior.

- **Blocking Assignments (`=`):**
  - Used for combinational logic.
  - Evaluated and updated immediately, which can cause unintended behavior if used in sequential logic.

**Example:**

```verilog
always @(posedge clk) begin
  a <= b; // Nonblocking assignment (correct for sequential logic)
  b <= c;
  c <= d;
end
```

Using blocking assignments in the same block:

```verilog
always @(posedge clk) begin
  a = b; // Blocking assignment (incorrect for sequential logic)
  b = c;
  c = d;
end
```

In the combinational block:

```verilog
always @(*) begin
  a = b; // Blocking assignment (correct for combinational logic)
  b = c;
  c = d;
end
```

## 4. What does the logic in a function get synthesized into? What are the area and timing implications of calling functions in RTL?

The logic inside a Verilog function is synthesized into combinational logic. Functions are used to encapsulate common combinational logic operations. The area and timing implications depend on the complexity of the operations inside the function.

## 5. What does the logic in a task get synthesized into? Explain with an example.

Tasks can contain both combinational and sequential logic. When synthesized, tasks are converted into the corresponding logic circuits. For example:

```verilog
task my_task(input a, input b, output reg c);
  begin
    c = a & b;
  end
endtask
```

This task will be synthesized into the corresponding AND gate logic.

## 6. What are the differences between using a task, and defining a module for implementing reusable logic?

- **Tasks:**
  - Can contain both combinational and sequential logic.
  - Can have delays.
  - Used for procedural code and can be invoked multiple times within a module.

- **Modules:**
  - Represent reusable hardware blocks.
  - Have defined input and output ports.
  - Can be instantiated multiple times to create hierarchical designs.

## 7. Can tasks and functions be declared external to the scope of module-endmodule?

In Verilog, tasks and functions cannot be declared outside the scope of `module-endmodule`. They must be defined within the module.

## 8. Design a 4-bit up-down counter which has an input up_down. When up_down = 1, it acts as an up counter, when up_down = 0, it acts as a down counter.

```verilog
module up_down_counter (
  input wire clk,
  input wire reset,
  input wire up_down,
  output reg [3:0] count
);
  always @(posedge clk or posedge reset) begin
    if (reset)
      count <= 4'b0000;
    else if (up_down)
      count <= count + 1;
    else
      count <= count - 1;
  end
endmodule
```

## 9. Design a binary to Gray Code Converter in Verilog.

```verilog
module binary_to_gray (
  input wire [3:0] binary,
  output wire [3:0] gray
);
  assign gray[3] = binary[3];
  assign gray[2] = binary[3] ^ binary[2];
  assign gray[1] = binary[2] ^ binary[1];
  assign gray[0] = binary[1] ^ binary[0];
endmodule
```
