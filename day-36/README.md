# 100 Days Verification Challenge - Day 36 - Operators

## 1. Describe following operators with an example:

### i. Arithmetic Operators: `*`, `+`, `%`

- **`*` (Multiplication)**: Multiplies two values.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd3;
  wire [7:0] product = a * b; // product = 15
  ```

- **`+` (Addition)**: Adds two values.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd3;
  wire [7:0] sum = a + b; // sum = 8
  ```

- **`%` (Modulo)**: Computes the remainder of division.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd3;
  wire [7:0] remainder = a % b; // remainder = 2
  ```

### ii. Logical Operators: `!`, `&&`

- **`!` (Logical NOT)**: Inverts the boolean value.
  ```verilog
  wire a = 1'b0;
  wire not_a = !a; // not_a = 1
  ```

- **`&&` (Logical AND)**: Returns true if both operands are true.
  ```verilog
  wire a = 1'b1;
  wire b = 1'b0;
  wire and_result = a && b; // and_result = 0
  ```

### iii. Relational Operators: `>`, `<`, `>=`

- **`>` (Greater Than)**: Checks if the left operand is greater than the right operand.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd3;
  wire greater_than = a > b; // greater_than = 1
  ```

- **`<` (Less Than)**: Checks if the left operand is less than the right operand.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd3;
  wire less_than = a < b; // less_than = 0
  ```

- **`>=` (Greater Than or Equal To)**: Checks if the left operand is greater than or equal to the right operand.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd5;
  wire greater_or_equal = a >= b; // greater_or_equal = 1
  ```

### iv. Equality Operators: `==`, `!=`

- **`==` (Equal To)**: Checks if two operands are equal.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd5;
  wire equal = (a == b); // equal = 1
  ```

- **`!=` (Not Equal To)**: Checks if two operands are not equal.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd3;
  wire not_equal = (a != b); // not_equal = 1
  ```

### v. Bitwise Operators: `&`, `|`, `^`

- **`&` (Bitwise AND)**: Performs a bitwise AND operation.
  ```verilog
  wire [7:0] a = 8'b1100_1100;
  wire [7:0] b = 8'b1010_1010;
  wire [7:0] and_result = a & b; // and_result = 8'b1000_1000
  ```

### vi. Reduction Operators: `&`, `~&`

- **`&` (Reduction AND)**: Computes the AND of all bits.
  ```verilog
  wire [3:0] a = 4'b1110;
  wire all_ones = &a; // all_ones = 0
  ```

- **`~&` (Reduction NAND)**: Computes the NAND of all bits.
  ```verilog
  wire [3:0] a = 4'b1110;
  wire not_all_ones = ~&a; // not_all_ones = 1
  ```

### vii. Shift Operators: `>>`, `<<`

- **`>>` (Right Shift)**: Shifts bits to the right.
  ```verilog
  wire [7:0] a = 8'b1100_1100;
  wire [7:0] shifted_right = a >> 2; // shifted_right = 8'b0011_0011
  ```

- **`<<` (Left Shift)**: Shifts bits to the left.
  ```verilog
  wire [7:0] a = 8'b1100_1100;
  wire [7:0] shifted_left = a << 2; // shifted_left = 8'b0011_0000
  ```

### viii. Concatenation: `{}`

- **Concatenation**: Combines multiple bits into a single vector.
  ```verilog
  wire [3:0] a = 4'b1100;
  wire [3:0] b = 4'b0011;
  wire [7:0] concat = {a, b}; // concat = 8'b1100_0011
  ```

### ix. Replication: `{}`

- **Replication**: Replicates a bit vector multiple times.
  ```verilog
  wire [3:0] a = 4'b1010;
  wire [15:0] replicate = {4{a}}; // replicate = 16'b1010_1010_1010_1010
  ```

### x. Conditional Operator: `? :`

- **Conditional**: Selects between two values based on a condition.
  ```verilog
  wire [7:0] a = 8'd5;
  wire [7:0] b = 8'd10;
  wire [7:0] max = (a > b) ? a : b; // max = 10
  ```

## 2. Explain Operator Precedence in Verilog:

Operators in Verilog have a specific precedence order that determines how expressions are evaluated. Here's a summary of common precedence levels (from highest to lowest):

1. **Unary Operators**: `!`, `~`, `+`, `-`
2. **Power Operator**: `**`
3. **Multiplication/Division/Modulo**: `*`, `/`, `%`
4. **Addition/Subtraction**: `+`, `-`
5. **Shift Operators**: `<<`, `>>`
6. **Relational Operators**: `<`, `<=`, `>`, `>=`
7. **Equality Operators**: `==`, `!=`
8. **Bitwise AND**: `&`
9. **Bitwise XOR**: `^`
10. **Bitwise OR**: `|`
11. **Logical AND**: `&&`
12. **Logical OR**: `||`
13. **Conditional Operator**: `? :`
14. **Assignment Operators**: `=`, `+=`, `-=`, `*=`, `/=`, etc.

## 3. Design following in Verilog

### a. 3-bit Ring Counter
```verilog
module ring_counter(
  output reg [2:0] count,
  input clk,
  input reset
);
  always @(posedge clk or posedge reset) begin
    if (reset)
      count <= 3'b001; // Initial value
    else
      count <= {count[1:0], count[2]}; // Rotate right
  end
endmodule
```

### b. Negative-edge Triggered D-FF with Clear
```verilog
module dff_neg_edge(
  output reg q,
  input d,
  input clk,
  input clear
);
  always @(negedge clk or posedge clear) begin
    if (clear)
      q <= 1'b0;
    else
      q <= d;
  end
endmodule
```

### c. 4-bit Asynchronous Counter
```verilog
module async_counter(
  output reg [3:0] count,
  input clk,
  input reset
);
  always @(posedge clk or posedge reset) begin
    if (reset)
      count <= 4'b0000;
    else
      count <= count + 1;
  end
endmodule
```

### d. 4-bit Comparator which compares two 4-bit no. & prints the largest number
```verilog
module comparator_4bit(
  output reg [3:0] largest,
  input [3:0] a,
  input [3:0] b
);
  always @* begin
    if (a > b)
      largest = a;
    else
      largest = b;
  end
endmodule
```

