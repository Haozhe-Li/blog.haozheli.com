## Processor Hardware

### 1. Electricity Primer

- **Electrical Current**: Flow of electrons across a conductor.
- **Electrical Voltage**: Force gradient causing electrons to move.
- **Electrical Resistance**: Impedes current flow.
- **Electrical Power**: Product of current and voltage.
- **Resistance and Heat**: Resistance converts power into heat, affecting temperature.

### 2. Transistors

- **Function**: Act as electrical valves.
- **Structure**: Connected to three wires, altering connectivity based on voltage.
- **Types**: Some allow current unless there's voltage; others allow current only if there's voltage.

### 3. Gates

- **Definition**: Arrangements of transistors with specific properties.
- **Common Gates**: NAND gate, AND gate, OR gate, XOR gate, etc.
- **Functionality**: Mimic any 1-, 2-, or 3-input truth table.

### 4. Building with Gates

- **Logic Construction**: Connect gates' outputs to inputs of other gates to build complex operations.
- **Arithmetic**: Binary arithmetic constructed using Boolean expressions and logic gates.
- **Multiplexer**: Works like an array indexing operation, selecting data inputs based on a selection input.
- **Register**: Important for storing information, made from interconnected gates forming feedback loops.
- **Memory**: Implemented using registers and multiplexers, with cheaper and slower designs for larger memories.

### 5. Processor Design

#### 5.1 Conceptual Design

- **Instructions and Memory**: Instructions stored in memory; fetched one after another using a program counter (PC).
- **Operation on Program Registers**: Instructions perform operations on local variables (program registers).
- **Control Constructs**: if statements, loops, function calls, etc., change the next executed code.

#### 5.2 Modern Design

- **Fancy Instruction Encoding**: Uses deprecated and late-add instructions to maintain compatibility.
- **Pipelining**: Breaks instructions into multiple steps, allowing parallel execution.
- **Speculation**: Predicts outcomes of operations to avoid idle processor cycles.
- **Out-of-Order Execution**: Reorders instructions for optimal execution, increases speculation value.

### Conclusion

- **Analogy**: Processor complexity likened to a multi-employee company, with various optimizations improving efficiency.
