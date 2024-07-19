# 100 Days Verification Challenge - Day 35 - Procedural Blocks

## 1. What is the purpose of 'initial' & 'always' block in Verilog?

- **`initial` Block**: Executes once at the beginning of the simulation. It’s typically used to set initial values or perform initialization tasks. For example:
  ```verilog
  initial begin
    a = 0;
    b = 1;
  end
  ```

- **`always` Block**: Executes continuously whenever any of the variables in its sensitivity list change. It’s used to model combinational and sequential logic. For example:
  ```verilog
  always @(posedge clk) begin
    q <= d;
  end
  ```

## 2. Do `initial` & `always` blocks synthesize in Verilog?

- **`initial` Block**: Typically, `initial` blocks are not synthesized into hardware but are used for simulation purposes. They are not intended to describe hardware behavior but rather to set up the simulation environment.

- **`always` Block**: These blocks are synthesized into hardware. They describe the behavior of sequential or combinational logic and are used in hardware modeling.

## 3. Explain `final` block with an example:

The `final` block is used in Verilog to execute code when the simulation ends. It’s primarily for cleanup or final checks.

Example:
```verilog
module example;
  initial begin
    // Initialization code
  end

  final begin
    $display("Simulation finished.");
  end
endmodule
```

## 4. How can a `forever` loop be stopped in Verilog?

A `forever` loop will run indefinitely. To stop it, you typically need to use a `disable` statement or an external condition to control its execution. For example:

```verilog
always begin
  // Loop runs forever
  #10;
  if (stop_condition) begin
    disable my_loop;
  end
end

// The following is to define a loop to be disabled
task my_loop;
  forever begin
    // Task code
  end
endtask
```

## 5. Can `initial` & `always` blocks be used inside a `task`?

- **`initial` Block**: Cannot be used inside a `task`.
- **`always` Block**: Can be used inside a `task` as long as it’s used within procedural blocks. However, in most cases, `always` blocks are used outside tasks to describe hardware behavior.

## 6. What happens if there is no sensitivity list?

- **For Combinational Logic**: If there is no sensitivity list, the behavior can be unpredictable or lead to simulation mismatches. For combinational logic, it’s essential to specify a sensitivity list or use `always @*` to infer sensitivity automatically.

- **For Sequential Logic**: If no sensitivity list is provided in a clocked `always` block (like `always @(posedge clk)`), it will not execute correctly, leading to errors or undefined behavior.

## 7. What are Blocking and non-blocking in Verilog?

- **Blocking Assignment (`=`)**: Executes sequentially. The next statement waits until the current statement completes.
  ```verilog
  a = b; // Blocking
  c = a; // Executes after 'a = b' is complete
  ```

- **Non-Blocking Assignment (`<=`)**: Executes concurrently. The next statement does not wait for the current statement to complete.
  ```verilog
  a <= b; // Non-blocking
  c <= a; // Executes simultaneously
  ```

## 8. Explain continuous assignment with an example:

Continuous assignment is used for modeling combinational logic. It’s performed using the `assign` statement.

Example:
```verilog
module comb_logic(output wire y, input wire a, b);
  assign y = a & b; // Continuous assignment
endmodule
```

## 9. Design & execute following in Verilog:

i. **8:3 Priority Encoder Using `case` Statement**:
```verilog
module priority_encoder_8to3(output reg [2:0] y, input [7:0] in);
  always @* begin
    casez (in)
      8'b1???????: y = 3'd7;
      8'b01??????: y = 3'd6;
      8'b001?????: y = 3'd5;
      8'b0001????: y = 3'd4;
      8'b00001???: y = 3'd3;
      8'b000001??: y = 3'd2;
      8'b0000001?: y = 3'd1;
      8'b00000001: y = 3'd0;
      default: y = 3'dx; // Invalid input
    endcase
  end
endmodule
```

ii. **D Latch**:
```verilog
module d_latch(output reg q, input d, input clk);
  always @(d or clk) begin
    if (clk)
      q <= d;
  end
endmodule
```

iii. **Decade Counter**:
```verilog
module decade_counter(output reg [3:0] count, input clk, input reset);
  always @(posedge clk or posedge reset) begin
    if (reset)
      count <= 4'd0;
    else if (count == 4'd9)
      count <= 4'd0;
    else
      count <= count + 1;
  end
endmodule
```


