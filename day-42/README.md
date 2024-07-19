# 100 Days Verification Challenge - Day 42 - Advanced Verilog Codes

## 1. Design the following in Verilog: 

### A circuit that can be used as an inverter/buffer depending on the input signal INV. If INV-1, the circuit acts as an inverter. If INV=0, the circuit acts as a Buffer.

The circuit acts as an inverter or buffer depending on the input signal `INV`. If `INV` is `1`, the circuit acts as an inverter. If `INV` is `0`, the circuit acts as a buffer.

```verilog
module inv_buf (
  input wire INV,
  input wire A,
  output wire Y
);
  assign Y = INV ? ~A : A;
endmodule
```

## 2. Design a module 4bit_adder_subtractor_dut which has a function 4b_add_sub which takes an input signal add. If add=1, the function performs addition of two 4-bit inputs 'A' & 'B', else it performs subtraction of 'A' & 'B'

This module contains a function `4b_add_sub` which performs addition or subtraction based on the input signal `add`.

```verilog
module adder_subtractor (
  input wire add,
  input wire [3:0] A,
  input wire [3:0] B,
  output wire [3:0] result,
  output wire carry_out
);
  wire [3:0] B_complement;
  wire carry_in;

  assign B_complement = add ? B : ~B;
  assign carry_in = add ? 1'b0 : 1'b1;

  assign {carry_out, result} = A + B_complement + carry_in;
endmodule
```

## 3. Design following using Verilog:

**i. 3-bit Johnson Counter**

A Johnson counter cycles through a sequence of states where each state is a bitwise shift of the previous state.

```verilog
module johnson_counter (
  input wire clk,
  input wire reset,
  output reg [2:0] q
);
  always @(posedge clk or posedge reset) begin
    if (reset)
      q <= 3'b000;
    else begin
      q <= {~q[0], q[2:1]};
    end
  end
endmodule
```

**ii. SR Latch**

An SR latch is a basic memory element with set (S) and reset (R) inputs.

```verilog
module sr_latch (
  input wire S,
  input wire R,
  output reg Q,
  output reg Qn
);
  always @(S or R) begin
    if (S && ~R) begin
      Q <= 1;
      Qn <= 0;
    end else if (~S && R) begin
      Q <= 0;
      Qn <= 1;
    end
  end
endmodule
```

## 4. Design an FSM in Verilog with below states:
### i. IDLE-This is the default state on reset. IDLE state can transition to 2 states GRNTO & GRNT1: GRNTO if req0-1 GRNT1 if req1-1
### ii. GRNT 0- This state is achieved from IDLE state when req0-1 If req0 remains '1', the state GRNTO state remains unchanged. If req00, then GRNTO transitions to IDLE state.
### iii. GRNT 1- This state is achieved from IDLE state when req1-1 If reql remains '1', the state GRNT1 state remains unchanged. If req10, then GRNT1 transitions to IDLE state.

This FSM has three states: IDLE, GRNT0, and GRNT1.

```verilog
module fsm (
  input wire clk,
  input wire reset,
  input wire req0,
  input wire req1,
  output reg [1:0] state
);
  // State encoding
  localparam IDLE  = 2'b00,
             GRNT0 = 2'b01,
             GRNT1 = 2'b10;

  always @(posedge clk or posedge reset) begin
    if (reset)
      state <= IDLE;
    else begin
      case (state)
        IDLE: begin
          if (req0)
            state <= GRNT0;
          else if (req1)
            state <= GRNT1;
        end

        GRNT0: begin
          if (!req0)
            state <= IDLE;
        end

        GRNT1: begin
          if (!req1)
            state <= IDLE;
        end

        default: state <= IDLE;
      endcase
    end
  end
endmodule
```
