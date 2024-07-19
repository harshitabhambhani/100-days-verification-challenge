# 100 Days Verification Challenge - Day 38 - Behavioral Modelling

## 1. Explain difference between case, casex & casez.

- **`case`**: This is a basic case statement that compares the expression exactly with each case item. It performs a strict comparison, meaning no don’t-care conditions are used.

  ```verilog
  case (expression)
    2'b00: // action;
    2'b01: // action;
    2'b10: // action;
    2'b11: // action;
  endcase
  ```

- **`casex`**: This case statement treats `x` and `z` as don't-care conditions. This means that the specific value of `x` or `z` will not affect the case selection.

  ```verilog
  casex (expression)
    2'b1x: // action;
    2'bx0: // action;
  endcase
  ```

- **`casez`**: This case statement treats `z` as a don't-care condition but will not ignore `x`. It’s useful when you want to match against certain bits that may be unknown.

  ```verilog
  casez (expression)
    2'b1z: // action;
    2'bz0: // action;
  endcase
  ```

## 2. Explain sequential & parallel blocks with an example.

- **Sequential Block**: Executes statements in the order they appear, one after the other. It is used with `initial` and `always` blocks.

  ```verilog
  initial begin
    a = 0;
    #10 b = 1;
    #5 c = 2;
  end
  ```

- **Parallel Block**: Executes all statements simultaneously. It is often used for non-blocking assignments within `always` blocks.

  ```verilog
  always @(*) begin
    a = b;
    c = d;
    e = f;
  end
  ```

## 3. Explain following event-based timing control mechanisms:

- **i. Regular Event Control**: Triggered by changes in signals. The block executes when there is a change in any of the signals listed.

  ```verilog
  always @(a or b or c) begin
    // actions
  end
  ```

- **ii. Named Event Control**: Uses named events to control execution. Events are defined and triggered explicitly.

  ```verilog
  event my_event;
  
  always @ (my_event) begin
    // actions
  end
  
  initial begin
    -> my_event; // triggers the event
  end
  ```

## 4. Explain the conditional statement if and else with an example.

- **`if` and `else`**: Used for conditional branching in Verilog. Actions are executed based on the condition being true or false.

  ```verilog
  always @ (posedge clk) begin
    if (reset) begin
      q <= 0;
    end else begin
      q <= d;
    end
  end
  ```

  Example:

  ```verilog
  initial begin
    if (a == 1) begin
      b = 1;
    end else if (a == 2) begin
      b = 2;
    end else begin
      b = 0;
    end
  end
  ```

## 5. Explain following looping statements: 

- **`while`**: Executes statements repeatedly as long as the condition is true.

  ```verilog
  integer i;
  
  initial begin
    i = 0;
    while (i < 10) begin
      i = i + 1;
    end
  end
  ```

- **`for`**: Executes statements for a specific number of iterations.

  ```verilog
  integer i;
  
  initial begin
    for (i = 0; i < 10; i = i + 1) begin
      // actions
    end
  end
  ```

## 6. How can we disable naming of blocks?

To disable naming of blocks, use anonymous blocks by simply not providing a name:

```verilog
begin
  // actions
end
```

## 7. What is the output?

Here’s the code provided with an explanation of its output:

```verilog
initial begin
  m = 1'b0;
end

initial begin
  #5 a = 1'b1;
  #25 b = 1'b0;
end

initial begin
  #10 x = 1'b0; 
  #25 y = 1'b1; 
end

initial begin
  #50 $finish;   
end
```

The code will execute as follows:

- At time `0`: `m` is set to `0` (from the first `initial` block).
- At time `5`: `a` is set to `1` (from the second `initial` block).
- At time `10`: `x` is set to `0` (from the third `initial` block).
- At time `25`: `b` is set to `0` (from the second `initial` block) and `y` is set to `1` (from the third `initial` block).
- At time `50`: Simulation ends with `$finish` (from the fourth `initial` block).

So, at simulation end, the values will be:

- `m = 0`
- `a = 1`
- `b = 0`
- `x = 0`
- `y = 1`
