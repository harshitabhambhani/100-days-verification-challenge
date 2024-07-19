# 100 Days Verification Challenge - Day 34 - Basic Verilog Codes

## 1. Explain with example different methods to code a clock in Verilog.

In Verilog, you can code a clock using various methods depending on the design requirements and complexity. Here are a few methods with examples:

### Method 1: Using Always Block
```verilog
module clock_divider(
    input wire clk_in,      // Input clock
    output reg clk_out      // Output clock
);
    reg [31:0] counter = 0; // Counter for clock division

    always @(posedge clk_in) begin
        counter <= counter + 1;
        if (counter == 50000000) begin
            clk_out <= ~clk_out;
            counter <= 0;
        end
    end
endmodule
```

### Method 2: Using Assign Statement
```verilog
module clock_divider_assign(
    input wire clk_in,
    output wire clk_out
);
    reg [31:0] counter = 0;

    assign clk_out = (counter < 25000000) ? 1'b0 : 1'b1;

    always @(posedge clk_in) begin
        counter <= counter + 1;
        if (counter == 50000000) counter <= 0;
    end
endmodule
```

## 2. Write a Verilog code for:

### i. Synchronous Reset
```verilog
module sync_reset(
    input wire clk,
    input wire rst,
    output reg q
);
    always @(posedge clk) begin
        if (rst) begin
            q <= 1'b0;
        end else begin
            q <= 1'b1; // or some other logic
        end
    end
endmodule
```

### ii. Asynchronous Reset
```verilog
module async_reset(
    input wire clk,
    input wire rst,
    output reg q
);
    always @(posedge clk or posedge rst) begin
        if (rst) begin
            q <= 1'b0;
        end else begin
            q <= 1'b1; // or some other logic
        end
    end
endmodule
```

## 3. Write a Verilog code to swap contents of two registers:

### i. With a Temporary Register
```verilog
module swap_with_temp(
    input wire clk,
    input wire [7:0] reg1,
    input wire [7:0] reg2,
    output reg [7:0] reg1_out,
    output reg [7:0] reg2_out
);
    reg [7:0] temp;

    always @(posedge clk) begin
        temp <= reg1;
        reg1_out <= reg2;
        reg2_out <= temp;
    end
endmodule
```

### ii. Without a Temporary Register
```verilog
module swap_without_temp(
    input wire clk,
    input wire [7:0] reg1,
    input wire [7:0] reg2,
    output reg [7:0] reg1_out,
    output reg [7:0] reg2_out
);
    always @(posedge clk) begin
        reg1_out <= reg1 ^ reg2;
        reg2_out <= reg1_out ^ reg2;
        reg1_out <= reg1_out ^ reg2_out;
    end
endmodule
```

## 4. Design Using Verilog:

### i. XNOR Gate
```verilog
module xnor_gate(
    input wire a,
    input wire b,
    output wire y
);
    assign y = ~(a ^ b);
endmodule
```

### ii. D Flip-Flop
```verilog
module d_ff(
    input wire clk,
    input wire d,
    output reg q
);
    always @(posedge clk) begin
        q <= d;
    end
endmodule
```

### iii. 2:1 MUX
```verilog
module mux_2_to_1(
    input wire a,
    input wire b,
    input wire sel,
    output wire y
);
    assign y = (sel) ? b : a;
endmodule
```

### iv. 2-bit Full Adder
```verilog
module full_adder_2bit(
    input wire [1:0] a,
    input wire [1:0] b,
    input wire cin,
    output wire [1:0] sum,
    output wire cout
);
    wire carry1;

    assign {carry1, sum[0]} = a[0] + b[0] + cin;
    assign {cout, sum[1]} = a[1] + b[1] + carry1;
endmodule
```

## 5. Design a Verilog code to execute following truth table:

| Inputs | Outputs |
|--------|---------|
| a | b | x | y |
|---|---|---|---|
| 0 | 0 | 1 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 1 |

### Verilog Code
Here is the Verilog code that implements the given truth table:

```verilog
module truth_table(
    input wire a,
    input wire b,
    output wire x,
    output wire y
);
    // Implement the logic for x and y based on the truth table
    assign x = ~a & ~b | a & b;
    assign y = ~a & b;

endmodule
```

### Explanation

The logic for `x` and `y` is derived as follows:

#### For `x`:
- When `a = 0` and `b = 0`, `x = 1` (true for ~a & ~b).
- When `a = 0` and `b = 1`, `x = 1` (true for ~a & b).
- When `a = 1` and `b = 0`, `x = 0` (false for a & ~b).
- When `a = 1` and `b = 1`, `x = 0` (false for a & b).

#### For `y`:
- When `a = 0` and `b = 0`, `y = 0` (false for ~a & ~b).
- When `a = 0` and `b = 1`, `y = 1` (true for ~a & b).
- When `a = 1` and `b = 0`, `y = 0` (false for a & ~b).
- When `a = 1` and `b = 1`, `y = 1` (true for a & b).

In this code:
- The `assign` statements are used to define the logic for `x` and `y` based on the input values of `a` and `b`.
- The expressions `(~a & ~b) | (~a & b)` and `(~a & b) | (a & b)` ensure that the outputs match the truth table provided.
