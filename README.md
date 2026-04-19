# Machine Learning Simulator - CPU Architecture Emulator

## Overview
A C++ implementation of a simplified machine architecture simulator that emulates basic CPU operations including register management, memory access, and instruction execution. Despite the repository name, this project functions as an educational machine language interpreter that processes hexadecimal instructions to demonstrate fundamental computer organization concepts such as fetch-decode-execute cycles, register-memory interaction, and conditional branching.

## Features
- Simulates a von Neumann architecture with 256 memory cells and 16 general-purpose registers
- Supports a custom hexadecimal instruction set with 7 operation codes:
  - `1RMA`: Load register R with value from memory address MA
  - `2RXY`: Load register R with immediate hexadecimal value XY
  - `3RAM`: Store register R value to memory address AM
  - `4RBS`: Move value from register B to register S
  - `5RST`: Add registers S and T, store result in register R
  - `BRXY`: Conditional branch to address XY if register R equals register 0
  - `C000`: Halt program execution
- Hexadecimal/decimal conversion utilities for instruction parsing
- Encapsulated Memory and Register classes with getter/setter methods
- File-based input parsing for instruction loading from text files
- Console output displaying final memory and register states for debugging and verification

## Technologies Used
- Language: C++ (100%)
- Standard Libraries: iostream, fstream, string, vector, sstream
- Data Representation: Hexadecimal instruction encoding, string-based value storage
- Compiler: Compatible with GCC, Clang, MSVC, or any C++11+ compliant compiler

## Setup and Usage
1. Clone the repository:
```bash
git clone https://github.com/z00xINe/Machine-Learning-Simulator.git
cd Machine-Learning-Simulator
```
2. Prepare an input file (e.g., `Test.txt`) with instructions in hexadecimal format:
```
0x2 0x0 0x03
0x2 0x1 0x01
0x5 0x2 0x21
0xB 0x2 0x48
0xC 0x0 0x00
```
  - Format: Each line represents one 4-digit hexadecimal instruction (opcode + operands).
3. Compile the source code:
```
g++ MachineLearningSimulator.cpp -o MachineSim
```
4. Run the simulator:
```
./MachineSim
```
5. Review console output showing final memory contents and register values.

## Instruction Set Reference

| Opcode | Format | Operation  | Description                |
|--------|--------|------------|----------------------------|
| 1      | 1RMA   | LOAD       | R ← Memory[MA]             |
| 2      | 2RXY   | LOAD_IMM   | R ← XY                     |
| 3      | 3RAM   | STORE      | Memory[AM] ← R             |
| 4      | 4RBS   | MOVE       | R ← S                      |
| 5      | 5RST   | ADD        | R ← S + T                  |
| B      | BRXY   | JUMP_IF_EQ | if R == R0: PC ← XY        |
| C      | C000   | HALT       | Terminate execution        |

## Output Format

- After execution, the simulator prints:
  - All 256 memory cells with addresses and stored values
  - Separator line for readability
  - All 16 registers with addresses and current values
- Example:
```
Memory[00] = 20
Memory[01] = 03
...
Register[00] = 00
Register[01] = 03
...
```

## Educational Value

- This project reinforces core computer architecture concepts:
  - Instruction encoding and decoding
  - Register-file and memory hierarchy interaction
  - Program counter management and control flow
  - Hexadecimal representation of machine instructions
  - Sequential execution model and branching logic

## Notes

- Input files must contain valid 4-digit hexadecimal instructions; malformed input may cause undefined behavior
- Register and memory values are stored as strings representing hexadecimal digits
- The simulator does not implement overflow detection or signed arithmetic
- Extendable to support additional instructions, interrupt handling, or I/O operations
