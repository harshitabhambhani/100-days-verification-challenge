# 100 Days Verification Challenge - Day 33 - System Tasks

## 1. Explain the difference between Sdisplay, Smonitor & Sstrobe with an example

- **$display**: Displays the values of variables at the time the statement is executed.
  - **Example**:
    ```verilog
    initial begin
      $display("Time=%0t a=%b b=%b", $time, a, b);
    end
    ```

- **$monitor**: Continuously monitors the variables and displays their values whenever any of them changes.
  - **Example**:
    ```verilog
    initial begin
      $monitor("Time=%0t a=%b b=%b", $time, a, b);
    end
    ```

- **$strobe**: Displays the values of variables at the end of the current simulation time step.
  - **Example**:
    ```verilog
    initial begin
      $strobe("Time=%0t a=%b b=%b", $time, a, b);
    end
    ```

## 2. Which system tasks are used to switch monitoring on & off? Explain with example.

- **Turning on monitoring**: Use `$monitor`.
  - **Example**:
    ```verilog
    initial begin
      $monitor("Time=%0t a=%b b=%b", $time, a, b);
    end
    ```

- **Turning off monitoring**: Use `$monitoroff`.
  - **Example**:
    ```verilog
    initial begin
      $monitor("Time=%0t a=%b b=%b", $time, a, b);
      #10 $monitoroff;
    end
    ```

## 3. Explain the following System tasks with an example:

- **$stop**: Halts the simulation and puts it into an interactive mode.
  - **Example**:
    ```verilog
    initial begin
      $display("Simulation stopped at time=%0t", $time);
      $stop;
    end
    ```

- **$finish**: Ends the simulation and exits.
  - **Example**:
    ```verilog
    initial begin
      $display("Simulation finished at time=%0t", $time);
      $finish;
    end
    ```

## 4. Explain following compiler directives with an example:

- **`define**: Defines a macro.
  - **Example**:
    ```verilog
    `define WIDTH 8
    reg [`WIDTH-1:0] data;
    ```

- **`include**: Includes another file.
  - **Example**:
    ```verilog
    `include "definitions.v"
    ```

## 5. Explain the difference between == & === with an example.

- **Equality operator (`==`)**: Compares two values for equality, treating `x` and `z` as unknowns.
  - **Example**:
    ```verilog
    initial begin
      if (a == b) begin
        $display("a is equal to b");
      end else begin
        $display("a is not equal to b");
      end
    end
    ```

- **Case equality operator (`===`)**: Compares two values for equality, including `x` and `z` values. It returns true only if both operands are exactly the same, including any unknown (`x`) or high-impedance (`z`) bits.
  - **Example**:
    ```verilog
    initial begin
      if (a === b) begin
        $display("a is exactly equal to b, including unknowns");
      end else begin
        $display("a is not exactly equal to b, including unknowns");
      end
    end
    ```

### Examples in detail:

- **Equality operator (`==`)**:
  ```verilog
  reg [3:0] a = 4'b010x;
  reg [3:0] b = 4'b0100;
  initial begin
    if (a == b) begin
      $display("a is equal to b"); // This will not be displayed because of 'x'
    end else begin
      $display("a is not equal to b"); // This will be displayed
    end
  end
  ```

- **Case equality operator (`===`)**:
  ```verilog
  reg [3:0] a = 4'b010x;
  reg [3:0] b = 4'b0100;
  initial begin
    if (a === b) begin
      $display("a is exactly equal to b, including unknowns"); // This will not be displayed because of 'x'
    end else begin
      $display("a is not exactly equal to b, including unknowns"); // This will be displayed
    end
  end
  ```

## 6. What is a sensitivity list?

- A sensitivity list in a procedural block (always block) defines the events that trigger the execution of that block.
  - **Example**:
    ```verilog
    always @ (posedge clk or negedge reset) begin
      if (!reset)
        q <= 0;
      else
        q <= d;
    end
    ```

## 7. Explain deposit and force commands.

- **Deposit (`$deposit`)**: Assigns a value to a variable.
  - **Example**:
    ```verilog
    initial begin
      $deposit(a, 1'b1);
    end
    ```

- **Force (`$force`)**: Temporarily overrides the value of a variable.
  - **Example**:
    ```verilog
    initial begin
      $force a = 1'b1;
    end
    ```

## 8. Explain freeze & drive with an example. 

- **Freeze**: Prevents further assignments to a variable.
  - **Example**:
    ```verilog
    initial begin
      $freeze(a);
    end
    ```

- **Drive**: Replaces continuous assignments with a new value.
  - **Example**:
    ```verilog
    initial begin
      $drive(a, 1'b1);
    end
    ```

## 9. What does timescale 1 Ns/1 Ps mean?

- **Timescale 1 ns/1 ps**: Sets the time unit to 1 nanosecond and the precision to 1 picosecond.
  - **Example**:
    ```verilog
    `timescale 1ns/1ps
    ```

## 10. Between variable and signal, which will be updated first & why?

- **Variables** (in procedural blocks): Updated first because they are evaluated immediately within the block.
- **Signals** (e.g., in continuous assignments): Updated after the block execution, based on event-driven updates.

  - **Example**:
    ```verilog
    reg a;
    wire b;
    
    always @ (posedge clk) begin
      a = b; // variable updated first
    end
    
    assign b = a; // signal updated next
    ```
