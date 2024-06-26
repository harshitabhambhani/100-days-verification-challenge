# 100 Days Verification Challenge - Day 6

## 1. What is a Finite State Machine (FSM)?

A Finite State Machine (FSM) is a computational model used to design systems with a finite number of states. It consists of:

- A finite set of states.
- A finite set of inputs.
- A finite set of outputs.
- A transition function that determines the next state based on the current state and input.
- An initial state.
- (Optional) A set of final or accepting states.

## 2. Different Types of FSMs

FSMs can be classified into two main types:

- Deterministic Finite Automaton (DFA): For each state and input, there is exactly one transition to a new state.
- Non-Deterministic Finite Automaton (NFA): For each state and input, there can be multiple possible transitions to new states, including transitions without any input (ε-transitions).

## 3. Difference Between Moore & Mealy Machine

### Moore Machine:
  - Outputs depend only on the current state.
  - The output is associated with the state itself.
  - Easier to design and understand.
  - Generally requires more states than Mealy machines for the same problem.

### Mealy Machine:
  - Outputs depend on both the current state and the current input.
  - The output is associated with transitions.
  - Can produce quicker responses to inputs as the output can change in the middle of a transition.

## 4. Applications & Limitations of FSM

### Applications:
- Control systems in embedded systems.
- Parsing and lexical analysis in compilers.
- Network protocols and communication systems.
- User interface management.
- Game development (AI behavior).

### Limitations:
- FSMs are not suitable for problems requiring memory of past inputs beyond a fixed length.
- Can become complex and hard to manage with a large number of states.
- Limited by the fixed number of states.

## 5. Handling Exceptions or Error States in FSM

Exceptions or error states can be handled in FSMs by defining specific error states and transitions. When an unexpected input or error condition occurs, the FSM transitions to an error state where it can perform necessary error handling actions (e.g., logging, cleanup, retries) before either halting or transitioning back to a safe state.

## 6. Concepts in FSM

i. Trigger:
   - An event or condition that causes a transition from one state to another.

ii. Transition:
   - The movement from one state to another, triggered by an input or event.

iii. State Diagram:
   - A graphical representation of an FSM, showing states, transitions, inputs, and outputs.

iv. Super State:
   - A state that encompasses one or more substates, allowing for hierarchical state modeling.

v. Guard Conditions:
   - Conditions that must be true for a transition to occur. They act as additional constraints on transitions.

vi. Deadlock:
   - A situation in FSM where no further transitions are possible, often due to an inappropriate handling of states and transitions.

vii. Determinism:
   - A property of FSMs where every state and input combination leads to exactly one defined transition.

viii. Epsilon (ε) Transitions:
   - Transitions that occur without any input (i.e., they can move from one state to another spontaneously).
