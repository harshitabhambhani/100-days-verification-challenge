# 100 Days Verification Challenge - Day 53 - Messaging, BFMs

## 1. Write a code to generate constrained random numbers in Verilog.

```verilog
module constrained_random;
    reg [3:0] random_num;
    integer seed = 1;

    initial begin
        // Generating constrained random numbers between 4 and 12
        repeat (10) begin
            random_num = $random(seed) % 9 + 4;
            $display("Random Number: %0d", random_num);
        end
    end
endmodule
```

## 2. How can you be sure that the constrained random stimulus has covered all the values in the range without repetition in a cyclic random fashion? Explain with an example.

To ensure all values are covered without repetition, you can use a cyclic random generation approach.

Example:

```verilog
module cyclic_random;
    reg [3:0] random_num;
    reg [3:0] values [0:8];
    integer i, j, temp;
    integer seed = 1;

    initial begin
        // Initialize the values array with numbers from 4 to 12
        for (i = 0; i < 9; i = i + 1) begin
            values[i] = i + 4;
        end
        
        // Shuffle the array using Fisher-Yates algorithm
        for (i = 8; i > 0; i = i - 1) begin
            j = $random(seed) % (i + 1);
            temp = values[i];
            values[i] = values[j];
            values[j] = temp;
        end
        
        // Display the values in random order without repetition
        for (i = 0; i < 9; i = i + 1) begin
            $display("Random Number: %0d", values[i]);
        end
    end
endmodule
```

## 3. Write a code to change the sequence of constrained random stimulus.

```verilog
module random_sequence_change;
    reg [3:0] random_num;
    integer seed = 1;

    initial begin
        // Generate random numbers
        repeat (10) begin
            random_num = $random(seed) % 9 + 4;
            $display("Original Random Number: %0d", random_num);
        end
        
        // Change the sequence
        seed = seed + 1; // Change the seed
        
        repeat (10) begin
            random_num = $random(seed) % 9 + 4;
            $display("Changed Random Number: %0d", random_num);
        end
    end
endmodule
```

## 4. What is weighted random stimulus? Explain with an example.

Weighted random stimulus involves assigning different probabilities to different values.

Example:

```verilog
module weighted_random;
    reg [3:0] random_num;
    integer seed = 1;
    integer weight;

    initial begin
        repeat (10) begin
            weight = $random(seed) % 100;
            if (weight < 50)
                random_num = 4; // 50% probability
            else if (weight < 80)
                random_num = 8; // 30% probability
            else
                random_num = 12; // 20% probability

            $display("Weighted Random Number: %0d", random_num);
        end
    end
endmodule
```

## 5. What metrics help in defining the completeness of the random simulations?

1. **Code Coverage**: Measures the extent to which the code is exercised.
2. **Functional Coverage**: Ensures all specified functional scenarios are tested.
3. **Assertion Coverage**: Tracks how many assertions are triggered.
4. **Toggle Coverage**: Ensures all signals have toggled.
5. **Path Coverage**: Ensures all possible paths in the code are exercised.

## 6. What are some stimulus generation techniques when the stimulus is not reproducible using BFMs? Explain using Verilog examples.

1. **Directed Tests**: Manually create test cases for specific scenarios.
2. **Constrained Random Testing**: Use constraints to generate specific random scenarios.
3. **Scenario-Based Testing**: Define and simulate real-world scenarios.

Example:

```verilog
module stimulus_gen;
    reg clk;
    reg reset;
    reg [3:0] data_in;

    initial begin
        clk = 0;
        forever #5 clk = ~clk;
    end

    initial begin
        reset = 1;
        #15 reset = 0;
        
        // Directed stimulus
        data_in = 4'b1010; #10;
        data_in = 4'b0101; #10;
        
        // Constrained random stimulus
        repeat (10) begin
            data_in = $random % 16;
            #10;
        end
    end
endmodule
```

## 7. What is SDF back-annotation, and how is it implemented in Verilog testbench?

Standard Delay Format (SDF) back-annotation involves annotating delays into the Verilog simulation to reflect actual timing.

Implementation in Verilog testbench:

```verilog
// Include SDF file in the testbench
initial begin
    $sdf_annotate("design.sdf", uut);
end
```

## 8. What is the difference between unit delay and full timing simulations?

- **Unit Delay Simulation**: Assumes all delays are unit (1-time unit) for faster simulation.
- **Full Timing Simulation**: Uses actual delays from SDF files for accurate timing analysis.

## 9. My gate simulation is not passing, and some tests hang. What are the key points to look for?

1. **Clock Issues**: Check clock stability and correctness.
2. **Reset Issues**: Ensure proper reset behavior.
3. **Timing Violations**: Check for setup and hold time violations.
4. **Initialization**: Ensure all signals are properly initialized.
5. **X-States**: Look for undriven signals resulting in unknown states (X).

## 10. Using a synchronous FSM approach, design a circuit that takes a single bit stream as an input at the pin `in`. An output pin `match` is asserted high each time the pattern 10101 is detected. A `reset` pin initializes the circuit synchronously. Input pin `clk` is used to clock the circuit. Apply constrained randomized stimulus to this design for verification.

FSM Design:

```verilog
module pattern_detector (
    input wire clk,
    input wire reset,
    input wire in,
    output reg match
);
    reg [2:0] state, next_state;
    
    // State encoding
    localparam S0 = 3'b000,
               S1 = 3'b001,
               S2 = 3'b010,
               S3 = 3'b011,
               S4 = 3'b100;
    
    // State transition
    always @(posedge clk or posedge reset) begin
        if (reset)
            state <= S0;
        else
            state <= next_state;
    end
    
    // Next state logic
    always @(*) begin
        case (state)
            S0: next_state = (in == 1) ? S1 : S0;
            S1: next_state = (in == 0) ? S2 : S1;
            S2: next_state = (in == 1) ? S3 : S0;
            S3: next_state = (in == 0) ? S4 : S1;
            S4: next_state = (in == 1) ? S1 : S0;
            default: next_state = S0;
        endcase
    end
    
    // Output logic
    always @(posedge clk or posedge reset) begin
        if (reset)
            match <= 0;
        else if (state == S4 && in == 1)
            match <= 1;
        else
            match <= 0;
    end
endmodule
```

Testbench with Constrained Random Stimulus:

```verilog
module pattern_detector_tb;
    reg clk, reset, in;
    wire match;
    integer seed = 1;

    pattern_detector uut (
        .clk(clk),
        .reset(reset),
        .in(in),
        .match(match)
    );

    initial begin
        clk = 0;
        forever #5 clk = ~clk;
    end

    initial begin
        reset = 1;
        #15 reset = 0;
        
        // Apply constrained random stimulus
        repeat (50) begin
            in = $random(seed) % 2;
            #10;
        end

        $finish;
    end
endmodule
```

This testbench generates a constrained random sequence of inputs to verify the functionality of the pattern detector FSM. The `match` output is asserted high whenever the pattern `10101` is detected in the input stream.
