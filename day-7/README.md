# 100 Days Verification Challenge - Day 7

## 1. FSM for Serial Two's Complement Block Detection

The two's complement of a binary number involves flipping all the bits and adding 1 to the least significant bit. An FSM to detect a serial two's complement block could look like this:

The main logic behind this is, start from the least significant bit and retain the bits until and first 1-bit has occurred. Once a 1-bit is found, start complementing the bits if 1 makes it 0 and if 0 make it 1. Note retain the first 1-bit. (Don’t complement it, complement the bit which follows that first 1-bit).

### State Assignment:

Let us assume State ‘a’ represents that 1 has not occurred yet. and assume State ‘b’ the situation after the first one has occurred. State flow diagram:

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/bd583158-4446-4432-a954-70bf84e13802)

## 2. FSM for Detecting Sequence 10110 (Overlapping)

To detect the sequence `10110` with overlapping:

States:
- `S0`: Initial state.
- `S1`: Detected `1`.
- `S2`: Detected `10`.
- `S3`: Detected `101`.
- `S4`: Detected `1011`.
- `S5`: Detected `10110` (final/accepting state).

Transitions:
- `S0` → `S1` on input `1`.
- `S1` → `S2` on input `0`.
- `S2` → `S3` on input `1`.
- `S3` → `S4` on input `1`.
- `S4` → `S5` on input `0`.
- `S5` → `S1` on input `1` (for overlapping).
- `S5` → `S2` on input `0` (for overlapping).

## 3. FSM for Detecting Sequence 11001100 (Non-Overlapping)

To detect the sequence `11001100` without overlapping:

States:
- `S0`: Initial state.
- `S1`: Detected `1`.
- `S2`: Detected `11`.
- `S3`: Detected `110`.
- `S4`: Detected `1100`.
- `S5`: Detected `11001`.
- `S6`: Detected `110011`.
- `S7`: Detected `1100110`.
- `S8`: Detected `11001100` (final/accepting state).

Transitions:
- `S0` → `S1` on input `1`.
- `S1` → `S2` on input `1`.
- `S2` → `S3` on input `0`.
- `S3` → `S4` on input `0`.
- `S4` → `S5` on input `1`.
- `S5` → `S6` on input `1`.
- `S6` → `S7` on input `0`.
- `S7` → `S8` on input `0`.
- `S8` → `S0` on any input (reset for non-overlapping detection).

## 4. FSM for More Than One "1"s in Last 3 Samples

To detect more than one `1` in the last 3 samples:

States:
- `S0`: Initial state (no `1`s in the last 3 samples).
- `S1`: One `1` in the last 3 samples.
- `S2`: Two or more `1`s in the last 3 samples (accepting state).

Transitions:
- `S0` → `S1` on input `1`.
- `S1` → `S2` on input `1`.
- `S2` remains in `S2` on input `1`.
- On input `0`, transition logic depends on the previous two states to keep track of `1`s within the last three samples.

## 5. FSM for Detecting Consequent 4 "0"s (Overlapping)

To detect four consecutive `0`s with overlapping:

States:
- `S0`: Initial state.
- `S1`: Detected `0`.
- `S2`: Detected `00`.
- `S3`: Detected `000`.
- `S4`: Detected `0000` (final/accepting state).

Transitions:
- `S0` → `S1` on input `0`.
- `S1` → `S2` on input `0`.
- `S2` → `S3` on input `0`.
- `S3` → `S4` on input `0`.
- `S4` → `S1` on input `0` (for overlapping).
- On input `1`, reset to `S0` from any state.

