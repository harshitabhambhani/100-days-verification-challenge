# 100 Days Verification Challenge - Day 32 - Verilog Data Types

## 1. Explain the difference between 'reg' & 'wire' with an example.

In Verilog, `reg` and `wire` are used to declare different types of variables, each with distinct characteristics and usage.

- **`wire`**: Represents a physical wire in the circuit and is used to connect different modules or elements. It can only be driven by continuous assignments (using the `assign` statement) or by output ports of modules.

- **`reg`**: Represents a variable that can store a value. It is used in procedural blocks like `always` or `initial` blocks. It does not imply a physical register but rather a variable that can hold values.

### Example:

```verilog
module example;
  wire a, b; // 'wire' declaration
  reg c;     // 'reg' declaration

  // Continuous assignment to wire
  assign a = b;

  // Procedural assignment to reg
  always @(a or b) begin
    c = a & b;
  end
endmodule
```

In this example:
- `a` and `b` are declared as `wire` and are used for continuous assignment.
- `c` is declared as `reg` and is used inside an `always` block.

## 2. Explain ternary operator (?) with an example.

The ternary operator in Verilog is similar to the ternary operator in other programming languages. It is used to choose between two values based on a condition.

Syntax:
```verilog
condition ? true_value : false_value
```

### Example:
```verilog
module ternary_example;
  reg [3:0] a, b, c;
  initial begin
    a = 4'b1010;
    b = 4'b0101;
    c = (a > b) ? a : b; // If a > b, then c = a, otherwise c = b
  end
endmodule
```

In this example, `c` will be assigned the value of `a` if `a` is greater than `b`, otherwise, it will be assigned the value of `b`.

## 3. Identify the base formats of nos. in following declarations:

- **12345**: Decimal (default format when no base is specified).

- **`025**: Octal (specified by the leading `0`).

- **`h9**: Hexadecimal (specified by the leading `h`).

- **'b1**: Binary (specified by the leading 'b').

## 4. Find the value of following declarations:

- **1'bz**: High impedance (Z).

- **32'h1x792**: The value has 'x' which represents unknown. So, the possible range of values would be:
  - `0000_0001_x111_1001_0010` (x can be 0 or 1)

- **16'o4z**: The value has 'z' which represents high impedance. The possible range of values would be:
  - `0000_0100_z` (z is high impedance, so only 12 bits are valid from octal)

- **16'h2xz**: The value has 'x' and 'z'. The possible range of values would be:
  - `0010_xxxx_z` (x can be 0 or 1, z is high impedance)

## 5. Explain how negative nos. can be declared & stored in Verilog.

Negative numbers in Verilog are declared using the two's complement representation. You can use the signed keyword to specify a signed value.

### Example:
```verilog
module negative_example;
  reg signed [7:0] neg_num;

  initial begin
    neg_num = -8'd10; // -10 in decimal
  end
endmodule
```

In this example, `neg_num` is an 8-bit signed register that stores the value -10. Verilog will handle the two's complement representation internally.

## 6. Explain the following keywords in Verilog with an example:

### i. `time`

The `time` keyword is used to declare variables that hold simulation time values. It is a special data type for storing time.

### Example:
```verilog
module time_example;
  time current_time;

  initial begin
    #5 current_time = $time; // Capture the current simulation time
  end
endmodule
```

### ii. `integer`

The `integer` keyword is used to declare integer variables. They are typically 32-bit signed integers.

### Example:
```verilog
module integer_example;
  integer count;

  initial begin
    count = 0;
    count = count + 1;
  end
endmodule
```

### iii. `parameter`

The `parameter` keyword is used to define constants in Verilog. Parameters can be used to create configurable modules.

### Example:
```verilog
module parameter_example;
  parameter WIDTH = 8;
  reg [WIDTH-1:0] data;

  initial begin
    data = 8'b10101010;
  end
endmodule
```

### iv. `defparam`

The `defparam` keyword is used to override parameters after module instantiation. It allows you to change parameter values from outside the module.

### Example:
```verilog
module defparam_example;
  parameter WIDTH = 8;
  reg [WIDTH-1:0] data;

  initial begin
    data = 8'b10101010;
  end
endmodule

module top;
  defparam defparam_example.WIDTH = 16; // Override parameter
  defparam_example example_inst();
endmodule
```

In this example, the `WIDTH` parameter of `defparam_example` is overridden to 16 in the `top` module.
