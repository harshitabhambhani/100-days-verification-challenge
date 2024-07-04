# 100 Days Verification Challenge - Day 14 - Pipelining hazards

## 1. Explain the different types pipelining hazards with examples (Structural, Control, Data hazards)

Pipelining hazards are conditions that prevent the next instruction in the instruction stream from executing during its designated clock cycle. There are three main types of hazards:

### a. Structural Hazards

Structural hazards occur when hardware resources are not available to execute an instruction. This happens when two or more instructions require the same resource at the same time.

**Example:**
If a processor has only one memory unit and both an instruction fetch and a memory read/write operation are needed simultaneously, a structural hazard occurs.

### b. Control Hazards (Branch Hazards)

Control hazards occur due to branch instructions. When the pipeline makes decisions based on branch outcomes, it may fetch incorrect instructions.

**Example:**
If a branch instruction is taken, the instructions that were fetched in the pipeline after the branch instruction may need to be discarded or replaced.

### c. Data Hazards

Data hazards occur when instructions that exhibit data dependency modify data in different stages of a pipeline.

**Sub-categories of Data Hazards:**
1. **RAW (Read After Write):** Occurs when an instruction needs to read a location that a previous instruction writes to before it writes.
2. **WAR (Write After Read):** Occurs when an instruction writes to a location before a previous instruction reads from it.
3. **WAW (Write After Write):** Occurs when two instructions write to the same location out of order.

**Example:**
For instructions:
- `ADD R1, R2, R3`
- `SUB R4, R1, R3`

A RAW hazard occurs because `SUB` reads `R1` before `ADD` writes to it.

## 2. What are ways to resolve different pipeline hazards? What are pros & cons of these resolution techniques?

### a. Structural Hazards

**Resolution:**
- **Resource duplication:** Duplicate the resource so that it can handle multiple simultaneous requests.
- **Pipeline stalling:** Introduce a stall or delay to wait until the resource becomes available.

**Pros and Cons:**
- **Pros:** Simple and effective in avoiding conflicts.
- **Cons:** Duplication increases hardware costs, and stalling reduces pipeline efficiency.

### b. Control Hazards

**Resolution:**
- **Branch prediction:** Predict the outcome of a branch to keep the pipeline full.
- **Delayed branching:** Delay the execution of a branch instruction to allow time for the branch decision to be made.
- **Branch target buffer:** Cache the target address of branches to quickly resolve branch instructions.

**Pros and Cons:**
- **Pros:** Effective in reducing the number of stalls.
- **Cons:** Incorrect predictions lead to pipeline flushes and performance penalties.

### c. Data Hazards

**Resolution:**
- **Pipeline forwarding (bypassing):** Use intermediate results directly from pipeline stages.
- **Pipeline stalling:** Introduce a delay until the hazard is resolved.
- **Instruction reordering:** Reorder instructions to avoid hazards.

**Pros and Cons:**
- **Pros:** Forwarding reduces the number of stalls; reordering can improve efficiency.
- **Cons:** Forwarding increases hardware complexity; stalling reduces performance.

## 3. Identify the pipelining hazards (also tell the sub-category e.g., Data hazard - WAW) in below sequence of instructions. Explain why these instructions are resulting in pipelining hazard.

### a. Sequence: `SUB R1, R4, R3` and `ADD R1, R2, R3`

**Hazard:** Data Hazard - RAW
**Explanation:**
- `ADD` reads `R1` which is written by `SUB`.
- `ADD` needs the result of `SUB` before it can proceed.

### b. Sequence: `ADD R1, R2, R3` and `SUB R4, R1, R3`

**Hazard:** Data Hazard - RAW
**Explanation:**
- `SUB` reads `R1` which is written by `ADD`.
- `SUB` needs the result of `ADD` before it can proceed.

### c. Sequence: `SUB R4, R1, R3` and `ADD R1, R2, R3`

**Hazard:** Data Hazard - WAW
**Explanation:**
- Both `SUB` and `ADD` write to `R1`.
- If `ADD` completes before `SUB`, the write to `R1` by `SUB` will overwrite the result of `ADD`.
