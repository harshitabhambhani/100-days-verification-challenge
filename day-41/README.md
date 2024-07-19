# 100 Days Verification Challenge - Day 41 - Advanced Verilog Concepts

## 1. Differentiate between Task and Function.

Tasks and functions in Verilog are used for code reuse, but they have some key differences:

- **Task**:
  - Can contain timing control statements (`#`, `@`, `wait`).
  - Can call other tasks and functions.
  - Can have zero or more input, output, or inout arguments.
  - Can return multiple values through output arguments.
  - Syntax:
    ```verilog
    task task_name;
      input arg1;
      output arg2;
      // Task body
    endtask
    ```

- **Function**:
  - Cannot contain timing control statements.
  - Can only call other functions.
  - Must execute in one simulation time unit.
  - Can have zero or more input arguments but no output or inout arguments.
  - Returns a single value.
  - Syntax:
    ```verilog
    function [return_type] function_name;
      input arg1;
      // Function body
    endfunction
    ```

## 2. What is PLI? What are its applications?

PLI (Programming Language Interface) is a mechanism in Verilog that allows interaction between Verilog code and C/C++ code. It provides a way to extend the capabilities of Verilog simulators.

- **Applications**:
  - Custom system tasks and functions.
  - Interfacing with hardware models written in C/C++.
  - Extending simulation features (e.g., adding custom verification utilities).
  - Enhancing debugging capabilities.

## 3. What is Virtual and Pure Virtual Function in Verilog?

Verilog does not directly support object-oriented programming (OOP) concepts like virtual functions. However, in SystemVerilog (an extension of Verilog), these concepts are available.

- **Virtual Function**:
  - A function that can be overridden in derived classes.
  - Allows dynamic dispatch (polymorphism).
  - Syntax:
    ```systemverilog
    class Base;
      virtual function void display();
        // Base class implementation
      endfunction
    endclass

    class Derived extends Base;
      virtual function void display();
        // Derived class implementation
      endfunction
    endclass
    ```

- **Pure Virtual Function**:
  - A virtual function with no implementation in the base class, forcing derived classes to provide an implementation.
  - Syntax:
    ```systemverilog
    class Base;
      pure virtual function void display();
    endclass
    ```

## 4. What is DPI? What are its Applications?

DPI (Direct Programming Interface) is a feature of SystemVerilog that allows seamless integration between SystemVerilog and foreign programming languages like C/C++.

- **Applications**:
  - Interfacing with external C/C++ models.
  - Creating custom verification components.
  - Extending simulator capabilities with custom functionality.
  - Efficiently handling complex data structures and algorithms not easily expressed in SystemVerilog.

## 5. Explain Following System Tasks in Verilog:

- **i. `$srandom`**: Seeds the random number generator.
  ```verilog
  $srandom(seed_value);
  ```

- **ii. `$readmemb`**: Reads memory contents from a binary file into a memory array.
  ```verilog
  $readmemb("file_name", memory_array);
  ```

- **iii. `$readmemh`**: Reads memory contents from a hexadecimal file into a memory array.
  ```verilog
  $readmemh("file_name", memory_array);
  ```

## 6. Explain Following File Support Operations in Verilog:

- **i. `$fopen`**: Opens a file and returns a file descriptor.
  ```verilog
  integer file;
  file = $fopen("file_name", "mode");
  ```

- **ii. `$fscanf`**: Reads formatted data from a file.
  ```verilog
  $fscanf(file, "format_string", variables);
  ```

- **iii. `$fdisplay`**: Writes formatted data to a file.
  ```verilog
  $fdisplay(file, "format_string", variables);
  ```

- **iv. `$fwrite`**: Writes data to a file without a newline.
  ```verilog
  $fwrite(file, "format_string", variables);
  ```

- **v. `$fclose`**: Closes a file.
  ```verilog
  $fclose(file);
  ```

## 7. Design & execute he following Verilog Codes:

- **i. T Flip Flop Design in Verilog:**

```verilog
module t_flip_flop (
    input wire clk,
    input wire reset,
    input wire t,
    output reg q
);

always @(posedge clk or posedge reset) begin
    if (reset)
        q <= 0;
    else if (t)
        q <= ~q;
end

endmodule
```

- **ii. 4-bit Shift Register:**

```verilog
module shift_register (
  input wire clk,
  input wire reset,
  input wire shift_in,
  output reg [3:0] q
);
  always @(posedge clk or posedge reset) begin
    if (reset)
      q <= 4'b0000;
    else
      q <= {q[2:0], shift_in};
  end
endmodule
```

- **iii. FSM to Detect Overlapping Sequence `01010`:**

```verilog
module fsm_sequence_detector (
    input wire clk,
    input wire reset,
    input wire in,
    output reg out
);

typedef enum reg [2:0] {
    IDLE,
    S0,
    S01,
    S010,
    S0101
} state_t;

state_t current_state, next_state;

// State transition logic
always @(posedge clk or posedge reset) begin
    if (reset)
        current_state <= IDLE;
    else
        current_state <= next_state;
end

// Next state logic
always @(*) begin
    case (current_state)
        IDLE:   next_state = in ? IDLE : S0;
        S0:     next_state = in ? S01 : S0;
        S01:    next_state = in ? IDLE : S010;
        S010:   next_state = in ? S0101 : S0;
        S0101:  next_state = in ? S01 : S010;
        default: next_state = IDLE;
    endcase
end

// Output logic
always @(posedge clk or posedge reset) begin
    if (reset)
        out <= 0;
    else
        out <= (current_state == S0101) && !in;
end

endmodule
```
