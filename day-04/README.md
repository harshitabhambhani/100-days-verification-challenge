# 100 Days Verification Challenge - Day 4 - Timers and Counters

## 1. Design & Explanation

### a. 4-bit Ring Counter

A 4-bit ring counter is a type of shift register counter where the output of the last flip-flop is fed back to the input of the first flip-flop. This creates a circular shifting of bits.

#### Working:
1. Components: Four D flip-flops connected in series.
2. Initial State: Typically, only one flip-flop is set to 1, and the rest are set to 0 (e.g., 1000).

#### Operation:
- On each clock pulse, the bit pattern shifts right by one position.
- The output of the last flip-flop is fed back to the input of the first flip-flop, creating a ring of bits.

#### State Diagram:
```
1000 -> 0100 -> 0010 -> 0001 -> 1000
```

### b. 4-bit Johnson Counter

A 4-bit Johnson counter, also known as a twisted ring counter, is a type of shift register counter where the complement of the output of the last flip-flop is fed back to the input of the first flip-flop.

#### Working:
1. Components: Four D flip-flops connected in series.
2. Initial State: All flip-flops are reset to 0 (0000).

#### Operation:
- On each clock pulse, the bit pattern shifts right by one position.
- The complement of the last flip-flop’s output is fed back to the input of the first flip-flop.

#### State Diagram:
```
0000 -> 1000 -> 1100 -> 1110 -> 1111 -> 0111 -> 0011 -> 0001 -> 0000
```

### c. 3-bit Ripple Counter

A 3-bit ripple counter is a type of asynchronous counter where each flip-flop is triggered by the output of the previous flip-flop.

#### Working:
1. Components: Three T (toggle) flip-flops connected in series.
2. Initial State: All flip-flops are reset to 0 (000).

#### Operation:
- The first flip-flop toggles on each clock pulse.
- Each subsequent flip-flop toggles when the preceding flip-flop changes from high to low (falling edge).

#### State Diagram:
```
000 -> 001 -> 010 -> 011 -> 100 -> 101 -> 110 -> 111 -> 000
```

### d. Decade Counter

A decade counter is a type of counter that counts from 0 to 9 (10 states) and then resets to 0.

#### Working:
1. Components: Four flip-flops connected in series.
2. Operation: Counts in binary from 0000 to 1001 (0 to 9) and then resets to 0000 on the next clock pulse.

#### State Diagram:
```
0000 -> 0001 -> 0010 -> 0011 -> 0100 -> 0101 -> 0110 -> 0111 -> 1000 -> 1001 -> 0000
```

## 2. Differences

### a. Timers vs. Counters

#### Timers:
- Measure time intervals.
- Often used in generating delays or measuring the duration of an event.
- Operate based on the clock frequency.

#### Counters:
- Count events, occurrences, or pulses.
- Used for counting the number of times an event occurs.
- Can be synchronous (all flip-flops clocked simultaneously) or asynchronous (flip-flops clocked sequentially).

### b. Synchronous vs. Asynchronous Counters

#### Synchronous Counters:
- All flip-flops are driven by a common clock signal.
- Changes in output occur simultaneously with the clock.
- Faster and more reliable due to synchronized operation.
- Less prone to propagation delays.

#### Asynchronous Counters:
- Flip-flops are not clocked simultaneously; each flip-flop is triggered by the output of the previous flip-flop.
- Changes in output occur at different times, creating ripple effect.
- Slower due to propagation delays between flip-flops.
- Simpler design but less reliable for high-speed applications.

## 3. Working of 555 Timer IC

The 555 timer IC is a versatile integrated circuit used for generating precise time delays or oscillations. It can operate in three modes: astable, monostable, and bistable.

### Astable Mode (Oscillator)

#### Operation:
- No stable state; continuously oscillates between high and low states.
- Generates a square wave output.

#### Circuit Configuration:
- Two resistors (R1 and R2) and a capacitor (C) are connected externally.
- Capacitor charges through R1 and R2, and discharges through R2.

#### Waveform:
- Frequency (f) and duty cycle (D) depend on R1, R2, and C values.

### Monostable Mode (One-shot Pulse Generator)

#### Operation:
- Generates a single pulse of a specified duration in response to an external trigger.
- Has one stable state (output low) and one unstable state (output high).

#### Circuit Configuration:
- A resistor (R) and a capacitor (C) are connected externally.
- Duration of the pulse (T) is determined by R and C values: \(T = 1.1 \times R \times C\).

### Bistable Mode (Flip-Flop)

#### Operation:
- Has two stable states: set (output high) and reset (output low).
- Changes state in response to external trigger signals.

#### Circuit Configuration:
- No external timing components required.
- Uses external trigger inputs to toggle between states.
