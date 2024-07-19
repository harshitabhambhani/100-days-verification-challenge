# 100 Days Verification Challenge - Day 39 - Tasks & Functions

## 1. Are tasks and functions re-entrant, and how are they different task and function calls?

- **Tasks**: Not re-entrant. A task can have delays and can call other tasks or functions. When a task is called, it blocks the calling code until it completes, and re-entry could cause conflicts if multiple threads or processes access shared resources.

- **Functions**: Re-entrant. Functions are intended to be used in expressions, and they cannot have delays or call tasks. They return a value immediately and are designed to be used in a non-blocking manner.

## 2. Can a 'task' be called within a 'function'?

In Verilog, a `task` cannot be called from within a `function`. Functions are intended to be used in expressions and cannot have delays or blocking statements, which tasks often include.

## 3. What are the restrictions of using automatic tasks? How can I override variables in an automatic task?

- **Automatic Tasks**: Automatic tasks are created with the `automatic` keyword and are local to the task call. They are typically used for re-entrant tasks, where each call to the task has its own local variables. The key restriction is that you cannot use delays or blocking statements in an automatic task.

- **Overriding Variables**: To override variables in an automatic task, you can declare the variable as `input` or `output` in the task definition. These variables can be passed from the calling code and used within the task.

## 4. When to Use a Task Instead of a Function?

- **Use a Task**:
  - When you need to include delays or blocking statements.
  - When you need to perform multiple steps or complex operations that involve changing states.
  - When you want to call other tasks or functions.

- **Use a Function**:
  - When you need a quick computation without delays.
  - When you want to use the result directly in expressions.
  - When you require a re-entrant code block.

## 5. How can I call a function like a task, that is, not have a return value assigned to a variable.
To call a function without assigning its return value to a variable, you can use a function in an expression context where the result is not used. For example:

```verilog
my_function(arg1, arg2);
```

In this case, `my_function` is called, but its return value is not assigned to any variable or used.

## 6. Define a `function` to design 8-function ALU that takes two 4-bit inputs `a` & `b` & computes a 5-bit output `out` based on 3-bit input `sel` as below:

<table>
  <thead>
    <tr>
      <th>sel</th>
      <th>out</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3'b000</td>
      <td>a</td>
    </tr>
    <tr>
      <td>3'b001</td>
      <td>a + b</td>
    </tr>
    <tr>
      <td>3'b010</td>
      <td>a - b</td>
    </tr>
    <tr>
      <td>3'b011</td>
      <td>a * b</td> <!-- Note: Ensure that this operation fits within the bit width if needed -->
    </tr>
    <tr>
      <td>3'b100</td>
      <td>a % b</td>
    </tr>
    <tr>
      <td>3'b101</td>
      <td>a << 1</td>
    </tr>
    <tr>
      <td>3'b110</td>
      <td>a >> 1</td>
    </tr>
    <tr>
      <td>3'b111</td>
      <td>a > b</td>
    </tr>
  </tbody>
</table>

```verilog
function [4:0] alu_function;
    input [3:0] a, b;
    input [2:0] sel;
    begin
        case (sel)
            3'b000: alu_function = a;
            3'b001: alu_function = a + b;
            3'b010: alu_function = a - b;
            3'b011: alu_function = a * b; // You might need to ensure this fits in 5 bits
            3'b100: alu_function = a % b; // Same here
            3'b101: alu_function = a << 1;
            3'b110: alu_function = a >> 1;
            3'b111: alu_function = (a > b) ? 1 : 0;
            default: alu_function = 5'bx;
        endcase
    end
endfunction
```

## 7. Task to Compute Factorial

Here is a Verilog task to compute the factorial of a 4-bit number with a delay:

```verilog
task compute_factorial;
    input [3:0] n;
    output [31:0] result;
    reg [31:0] temp;
    integer i;
    begin
        temp = 1;
        for (i = 1; i <= n; i = i + 1)
            temp = temp * i;
        #11 result = temp; // Delay of 11 time units
    end
endtask
```

