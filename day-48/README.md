# 100 Days Verification Challenge - Day 48 - RTL Design

## 1. What are some reusable coding practices for RTL Design?

1. **Modular Design**: Break down complex designs into smaller, reusable modules.
2. **Parameterization**: Use parameters to make modules configurable for different sizes and types.
3. **Consistent Naming Conventions**: Follow a consistent naming convention for signals, modules, and variables.
4. **Use of Constants**: Define constants for fixed values instead of hardcoding them.
5. **Code Documentation**: Add comments to describe the functionality of each module and critical sections of code.
6. **Design for Testability**: Incorporate test points and include features that make testing easier.
7. **Avoiding Latches**: Ensure all signals are properly registered to avoid unintended latches.
8. **Clock Domain Crossing**: Handle signals crossing clock domains carefully to avoid metastability.
9. **Reuse of Common Components**: Create libraries of common components like FIFO, ALU, etc., that can be reused across designs.

## 2. What are "snake" paths, and why should they be avoided?

"Snake" paths are long, winding routes in the layout of an integrated circuit, usually caused by poor floor planning or placement. They should be avoided because:
- **Increased Delay**: Longer paths increase the signal propagation delay.
- **Higher Power Consumption**: Longer interconnects can lead to higher power dissipation.
- **Signal Integrity Issues**: Increased path length can cause signal integrity issues such as crosstalk and noise.

## 3. What are a few considerations while partitioning large designs?

1. **Functional Partitioning**: Group related functionalities together.
2. **Clock Domain Partitioning**: Separate different clock domains to minimize clock domain crossing issues.
3. **Hierarchical Design**: Use a hierarchical approach to manage complexity.
4. **Resource Sharing**: Optimize resource sharing between partitions.
5. **Communication Overhead**: Minimize communication overhead between partitions.
6. **Scalability**: Design partitions to be scalable for future expansion.
7. **Testing and Debugging**: Ensure each partition can be tested and debugged independently.

## 4. How can I reliably convey control information across clock domains?

- **Use Synchronizers**: Use two or more flip-flops in series to synchronize control signals.
- **Gray Code**: Use Gray code for counters to ensure only one bit changes at a time.
- **Handshaking Protocols**: Implement handshaking protocols to ensure safe data transfer.
- **Dual-Port RAMs**: Use dual-port RAMs for shared memory access between clock domains.

## 5. What is a safe strategy to transfer data of different bus-widths and across different clock domains?

1. **Data Width Conversion**: Use serializers/deserializers to convert data between different bus widths.
2. **FIFO Buffers**: Use FIFO buffers to handle different data rates and clock domains.
3. **Handshaking**: Implement proper handshaking to ensure data integrity.
4. **Clock Domain Crossers**: Use specialized clock domain crossing circuits to handle asynchronous transfers.

## 6. What are a few considerations while using FIFOs for posted writes or prefetched reads that influence the speed of the design?

1. **Depth and Width**: Choose appropriate FIFO depth and width based on data throughput requirements.
2. **Latency**: Consider the latency introduced by FIFO in the data path.
3. **Flow Control**: Implement proper flow control to avoid overflow and underflow conditions.
4. **Clock Domain Crossing**: Ensure FIFOs are designed to handle different clock domains if required.
5. **Performance Impact**: Analyze the impact of FIFOs on the overall performance and timing of the design.

## 7. What will be synthesized from a module with only inputs and no outputs? 

A module with only inputs and no outputs will likely be optimized out during synthesis because it has no impact on the design. The synthesis tool will consider it redundant and remove it from the final netlist.

## 8. What are "combinatorial timing loops"? Why should they be avoided?

Combinatorial timing loops occur when the output of a combinatorial circuit feeds back into its input without any intervening sequential elements. They should be avoided because:
- **Unstable Outputs**: They can cause unstable or oscillating outputs.
- **Difficult to Analyze**: They make timing analysis and simulation difficult.
- **Unpredictable Behavior**: They lead to unpredictable circuit behavior, which can be hard to debug and fix.

## 9. How does the sensitivity list of a combinatorial always block affect pre- and post- synthesis simulation? Is this still an issue lately?

The sensitivity list in a combinatorial always block should include all the signals that the block depends on. If any signal is missed:
- **Pre-Synthesis Simulation**: The simulation might not reflect the true behavior, leading to incorrect results.
- **Post-Synthesis Simulation**: The synthesized hardware might behave differently from the simulation if the sensitivity list is incomplete. This issue has largely been mitigated by modern synthesis tools, but it’s still good practice to ensure the sensitivity list is accurate.

## 10. Design an 8-bit counter by using forever loop. The counter starts counting at count = 5 & finishes at count = 67. The count is incremented at positive edge of clock. The clock has a time period of 10. The counter counts through the loop only once & then is disabled. (Hint: Use the disable statement).

```verilog
module counter_8bit (
    input wire clk,
    input wire reset,
    output reg [7:0] count
);
    initial count = 5;

    always @(posedge clk or posedge reset) begin
        if (reset)
            count <= 5;
        else begin
            forever begin
                if (count == 67) disable counter;
                count <= count + 1;
            end
        end
    end
endmodule
```

Note: This example demonstrates the use of the `forever` loop and `disable` statement. In actual hardware design, you would typically use a more straightforward approach with a finite state machine (FSM) to achieve the same behavior.
