class: middle

# CS2100 Midterm Cheat Sheet

---

class: middle

## Binary and Hex Table

| Binary | Hex | Binary | Hex | Binary | Hex | Binary | Hex |
| ------ | --- | ------ | --- | ------ | --- | ------ | --- |
| 0000   | 0   | 0100   | 4   | 1000   | 8   | 1100   | C   |
| 0001   | 1   | 0101   | 5   | 1001   | 9   | 1101   | D   |
| 0010   | 2   | 0110   | 6   | 1010   | A   | 1110   | E   |
| 0011   | 3   | 0111   | 7   | 1011   | B   | 1111   | F   |

---

class: middle

## Control Signal Outputs (1/2)

| Instruction | RegDst | ALUSrc | MemToReg | RegWrite |
| ----------- | ------ | ------ | -------- | -------- |
| `R-type`    | 1      | 0      | 0        | 1        |
| `lw`        | 0      | 1      | 1        | 1        |
| `sw`        | X      | 1      | X        | 0        |
| `beq`       | X      | 0      | X        | 0        |

---

class: middle

## Control Signal Outputs (2/2)

| Instruction | MemRead | MemWrite | Branch | ALUop1 | ALUOp2 |
| ----------- | ------- | -------- | ------ | ------ | ------ |
| `R-type`    | 0       | 0        | 0      | 1      | 0      |
| `lw`        | 1       | 0        | 0      | 0      | 0      |
| `sw`        | 0       | 1        | 0      | 0      | 0      |
| `beq`       | 0       | 0        | 1      | 0      | 1      |
