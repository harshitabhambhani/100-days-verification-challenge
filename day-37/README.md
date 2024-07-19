# 100 Days Verification Challenge - Day 37 - Case Statements and Delays

## 1. Describe following delays with example:

### i. Regular Assignment Delay

In Verilog, a regular assignment delay uses the `#` symbol to specify the delay before the assignment takes effect. This delay is used in procedural blocks (`always`, `initial`) to model timing behavior.

Example:
```verilog
module example;
  reg a, b;
  
  initial begin
    a = 0;
    #10 a = 1; // 'a' is set to 1 after 10 time units
  end
  
  always #5 b = a; // 'b' will follow 'a' with a delay of 5 time units
endmodule
```

### ii. Implicit Continuous Assignment Delay

Implicit continuous assignments (made with the `assign` statement) do not have an explicit delay. They update immediately whenever their input values change.

Example:
```verilog
module example;
  reg a, b;
  wire c;
  
  assign c = a & b; // Continuous assignment, no explicit delay
  
  initial begin
    a = 0;
    b = 0;
    #10 a = 1; // Change in 'a' will immediately reflect in 'c'
    #5  b = 1; // 'c' updates immediately to 1
  end
endmodule
```

### iii. Net Declaration Delay

Net declaration delays are used to specify delays for nets, often in `assign` statements. However, specifying delays in this manner is rare and generally discouraged for hardware description because it can lead to unclear timing behavior.

Example:
```verilog
module example;
  reg a, b;
  wire c;
  
  assign #5 c = a & b; // Implicit delay of 5 time units
endmodule
```

## 2. What is delta simulation time?

Delta simulation time is a concept in digital simulation used to model events that occur at the same time but in different simulation cycles or "delta cycles." In Verilog simulation, operations in the same simulation time step are ordered in terms of delta cycles to ensure correct timing and ordering of events.

## 3. Transport Delay vs. Inertial Delay:

- **Transport Delay**: Delays the signal exactly by the specified amount of time, irrespective of the signal's transition. It’s used in `#` delays and `transport` delay models.
  ```verilog
  assign #10 out = in; // Transport delay of 10 time units
  ```

- **Inertial Delay**: Delays the signal but only propagates changes if the input signal remains stable for the entire delay period. It filters out glitches.
  ```verilog
  assign (delay 5, latch 5) out = in; // Inertial delay of 5 time units
  ```

## 4. What is meant by inferring latches & how to avoid it?

Inferring latches occurs when the synthesis tool interprets incomplete `always` blocks as latch-based designs. This often happens if not all input conditions are covered or if there’s no `else` clause, leading to a situation where the previous value of the variable is held.

Example:
```verilog
module latch_example(
  output reg q,
  input d,
  input clk
);
  always @(posedge clk) begin
    q <= d; // If not handled properly, this could infer a latch if 'q' is not assigned a value in all branches
  end
endmodule
```

## 5. Explain the repeat loop.

The `repeat` loop in Verilog is used to execute a block of code a specific number of times.

Example:
```verilog
module example;
  integer i;
  
  initial begin
    repeat (10) begin
      #5; // Wait 5 time units
      $display("This is repeat loop iteration %0d", i);
      i = i + 1;
    end
  end
endmodule
```

## 6. Why is it necessary to list all inputs in the sensitivity list of a combinational circuit?

In combinational circuits, it’s necessary to list all inputs in the sensitivity list to ensure that the output is updated whenever any of the inputs change. This guarantees that the combinational logic is correctly modeled and reacts to all input changes.

Example:
```verilog
module comb_logic(
  output reg out,
  input a,
  input b
);
  always @(a or b) begin
    out = a & b;
  end
endmodule
```

## 7. Explain following statements in Verilog:

### i. `casex`

The `casex` statement is used for case statements with "don't care" conditions. It treats `x` and `z` as wildcards.

Example:
```verilog
module example(
  output reg [1:0] out,
  input [3:0] in
);
  always @* begin
    case (in)
      4'b1xxx: out = 2'b00;
      4'b01xx: out = 2'b01;
      4'b001x: out = 2'b10;
      4'b0001: out = 2'b11;
      default: out = 2'bxx;
    endcase
  end
endmodule
```

### ii. `casez`

The `casez` statement is similar to `casex`, but `z` is treated as a wildcard and `x` is not.

Example:
```verilog
module example(
  output reg [1:0] out,
  input [3:0] in
);
  always @* begin
    casez (in)
      4'b1zzz: out = 2'b00;
      4'b01zz: out = 2'b01;
      4'b001z: out = 2'b10;
      4'b0001: out = 2'b11;
      default: out = 2'bxx;
    endcase
  end
endmodule
```

## 8. What is Verilog parallel case and full case statements?

- **Parallel Case**: Ensures that the case statement's branches are evaluated in parallel, but it doesn’t guarantee that all possible values are covered. Warnings can be generated if not all possible values are handled.

- **Full Case**: Explicitly informs the synthesis tool that all possible values of the case expression are covered. This helps in optimizing the design but requires that all cases be handled.

Example:
```verilog
module example(
  output reg [1:0] out,
  input [1:0] in
);
  always @* begin
    case (in)
      2'b00: out = 2'b00;
      2'b01: out = 2'b01;
      2'b10: out = 2'b10;
      2'b11: out = 2'b11;
      default: out = 2'bxx; // Full case
    endcase
  end
endmodule
```

## 9. Design 4-bit Ripple Carry Adder

```verilog
module ripple_carry_adder(
  output [3:0] sum,
  output carry_out,
  input [3:0] a,
  input [3:0] b,
  input carry_in
);
  wire c1, c2, c3;

  // 1st bit addition
  full_adder fa0 (
    .sum(sum[0]),
    .carry_out(c1),
    .a(a[0]),
    .b(b[0]),
    .carry_in(carry_in)
  );

  // 2nd bit addition
  full_adder fa1 (
    .sum(sum[1]),
    .carry_out(c2),
    .a(a[1]),
    .b(b[1]),
    .carry_in(c1)
  );

  // 3rd bit addition
  full_adder fa2 (
    .sum(sum[2]),
    .carry_out(c3),
    .a(a[2]),
    .b(b[2]),
    .carry_in(c2)
  );

  // 4th bit addition
  full_adder fa3 (
    .sum(sum[3]),
    .carry_out(carry_out),
    .a(a[3]),
    .b(b[3]),
    .carry_in(c3)
  );

endmodule

module full_adder(
  output sum,
  output carry_out,
  input a,
  input b,
  input carry_in
);
  assign {carry_out, sum} = a + b + carry_in;
endmodule
```

