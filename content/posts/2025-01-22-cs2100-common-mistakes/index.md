---
title: "CS2100 Common Mistakes"
date: "2025-01-22"
summary: "We learn from failure, not from success! (Quote by Bram Stoker)"
toc: true
readTime: true
autonumber: false
math: true
tags: ["NUS Courses"]
showTags: true
---

As you read this blog, you may realize that I am taking the CS 2K Trinity Modules, which are not commonly recommended. Therefore, I also need a system to manage the overwhelming content of these modules. While CS2030S is known for its heavy workload, CS2040S is known for its difficult concepts, and CS2100 is known for covering a broad range of topics but lacking depth. With this vast amount of knowledge, I am trying to note some of my misconceptions here so that I won't repeat them.

## Lecture 3: Data Representation and Number Systems

- When converting a binary number to an 8-bit 1's or 2's complement, such as `01001010`, the result is simply `01001010` for both. You only negate the bits or add one after negation (for the 2's complement) when you need to find the negative value `-(01001010)`, which, for example, is `10110110`.
- The IEEE-754 format can be more conveniently represented as 8 hexadecimal digits, but it is worth noting that you first need to convert the binary into a form like $1.XXXX \times 2^n$. The 32 bits of IEEE-754 consist of 1 sign bit (0 for positive and 1 for negative), 8 bits for the exponent in excess-127 notation, and the remaining 23 bits represent the fractional part, arranged from left to right.
- Below is a useful bit table to memorize or refer to, making binary-to-hexadecimal conversion faster:

  | Binary | Hexadecimal | Binary | Hexadecimal |
  | ------ | ----------- | ------ | ----------- |
  | 0000   | 0           | 1000   | 8           |
  | 0001   | 1           | 1001   | 9           |
  | 0010   | 2           | 1010   | A           |
  | 0011   | 3           | 1011   | B           |
  | 0100   | 4           | 1100   | C           |
  | 0101   | 5           | 1101   | D           |
  | 0110   | 6           | 1110   | E           |
  | 0111   | 7           | 1111   | F           |

---

## Lecture 4: Pointers and Functions

We can declare a variable `int *p`, which is a pointer `p` pointing to an integer value. Likewise, `int **q` is a double pointer. Here, `q` is a pointer that points to a pointer that points to an integer value. For example, we can assign `q = &p`. The tricky part is when we dereference the double pointer. `*q` will point to `p`, but `**q` will point to the value that `p` is pointing to.

---

## Lecture 5: Arrays, Strings, and Structures

- In C, the function passes a value instead of a reference like in many other languages, so any variables passed in are local within the function scope, except for pointers.
- The variable name of an array (for example, `a`) is a pointer to the first element of the array. Using this property, we can modify the structure in the first element of the array by passing the array name to the function.
- Strings are just arrays of characters that end with a null terminator `\0`. This terminator is not shown when printed, but it is worth noting that the behavior of strings is similar to that of arrays.

---

## Lecture 7: MIPS I (Introduction)

- Every line in assembly code corresponds one-to-one with a line in the binary code.
- Program variables are assigned to registers by compilers, not the programmers.
- Registers don't have data types like memory, and assembly could be considered a weakly typed language in this course.
- The MIPS processor has 32 registers, each 32 bits wide, while the immediate operand (constant) in the `addi` instruction is a 16-bit two's complement value (ranging from $-2^{15}$ to $2^{15} - 1$).
- Shifting $n$ bits left or right multiplies or divides bit values by $2^n$ (not to be confused with just $n$). If the results from bit shifting are zero, it could be due to the original bits being zeros or the shift size being at least the number of bits.
- Below are some useful instructions for performing operations that are not explicitly in the instruction set:
  - `sll` for multiplication
  - `srl` for division
  - `and` for masking
  - `or` for setting bits to 1
  - `nor`/`xor` for `not`
- A tip for adding a large constant (more than 16 bits for an immediate operand) is to use the `lui` instruction to set the first 16 bits (initializing the rest as zero), then use `ori` on that register to set the last 16 bits (while leaving the first 16 bits unchanged).

---

## Lecture 8: MIPS II (More Instructions)

- MIPS memory is 32 bits wide, allowing the processor to address $2^{32}$ locations, each holding 1 byte of data. Since words are 32 bits wide, each consecutive word occupies 4 addresses (4 bytes) and must be aligned.
- The `lw` (load word) instruction reads values from right to left, while the `sw` (store word) instruction writes values from left to right.
- The `slt` (set if less than) instruction sets the value to 1 if the condition is satisfied and to 0 otherwise.
- Labels are not instructions; they are pointers and do not consume memory.
- Be aware that the final loop iteration will also execute to check the condition, so the number of executed instructions is often off by one.

---

## Lecture 9: MIPS III (Instruction Formats and Encoding) and Lecture 10: Instruction Set Architecture

- Beware that the **Program Counter (PC)** stores the address of the next instruction to be executed, not the current one.
- To maximize the number of instructions in a fixed-length instruction set, consider maximizing the length of the longer instructions. This can be achieved by allowing the shorter instructions to occupy only one value (e.g., `0..000`) and using the remaining bit patterns for the longer instructions.
- To minimize the number of instructions, we maximize the shorter instructions. This typically results in the shorter instructions being one less than the longer ones, allowing us to distinguish between the two types.
- **Accumulator-based** and **stack-based architectures** use implicit operands, while **register-based architectures** like MIPS use explicit operands. **Memory-memory architectures** store everything in memory.

---

## Lecture 11: Processor: Datapath and Lecture 12: Processor: Control

- This visualization is very helpful for Lectures 11 and 12.

  ![Full Datapath Summary](/datapath.png)

- The stages of instruction execution are summarized as follows:

  1. **Fetch**: The instruction is fetched from memory using the program counter (PC) and placed into a register. The output is a 32-bit binary instruction.
  2. **Decode**: The opcode, registers, and related fields are extracted from the binary instruction. The data from the registers are also forwarded to the next step. The output consists of the operands for the ALU.
  3. **ALU**: This is where the execution takes place. The output is the result of the computation and a 1-bit `isZero` signal, which indicates whether the result is zero.
  4. **Memory**: The memory address calculated in the previous steps is used to read or write data (applicable only for **load/store** instructions). For other instructions, this stage is bypassed.
  5. **RegWrite**: The result is written back to the register (other unrelated registers remain unchanged). There is no additional output from this stage.

- The control signal for the multiplexer must handle all possible inputs. For example, 4 inputs require 2 bits to represent them (`00, 01, 10, 11`).
- The control signal `PCSrc` is `0` when `(PC + 4)` is selected and `1` when `(PC + 4) + (Immediate × 4)` is selected. This selection depends on the `isZero` signal from the ALU for branch instructions.
- The `ALUControl` signal specifies the operation the ALU needs to perform, while the `ALUSrc` signal determines the source of the second operand.
- `ALUSrc` is used to choose the second operand from either `RD2` or the sign-extended immediate, not from `RD1`.
- In `PCSrc`, the output `isZero` from the ALU is set to 1 when the ALU output is zero (not set to 0).
- The `ALUOp` is involved only in `ALUControl`, not in `ALUSrc`.
