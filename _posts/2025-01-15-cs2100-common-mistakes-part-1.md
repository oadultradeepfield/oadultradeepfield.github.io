---
tags: NUS-Courses
---

# CS2100 Common Mistakes Part 1

> We learn from failure, not from success!
>
> — _Bram Stoker_

As you read this blog, you may realize that I am taking the CS 2K Trinity Modules, which are not commonly recommended. Therefore, I also need a system to manage the overwhelming content of these modules. While CS2030S is known for its heavy workload, CS2040S is known for its difficult concepts, and CS2100 is known for covering a broad range of topics but lacking depth. With this vast amount of knowledge, I am trying to note some of my misconceptions here so that I won't repeat them.

**Note**: Part 1 covers the first half of the semester (before the midterm and recess week). I followed this convention in a previous post on CS2040S, but I think there isn't an obvious separation for this course.

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

## Lecture 4: Pointers and Functions

We can declare a variable `int *p`, which is a pointer `p` pointing to an integer value. Likewise, `int **q` is a double pointer. Here, `q` is a pointer that points to a pointer that points to an integer value. For example, we can assign `q = &p`. The tricky part is when we dereference the double pointer. `*q` will point to `p`, but `**q` will point to the value that `p` is pointing to.

---

## Lecture 5: Arrays, Strings, and Structures

- In C, the function passes a value instead of a reference like in many other languages, so any variables passed in are local within the function scope, except for pointers.
- The variable name of an array (for example, `a`) is a pointer to the first element of the array. Using this property, we can modify the structure in the first element of the array by passing the array name to the function.
- Strings are just arrays of characters that end with a null terminator `\0`. This terminator is not shown when printed, but it is worth noting that the behavior of strings is similar to that of arrays.

---

## Lecture 7: MIPS I (Introduction)

To be updated.

---

## Lecture 8: MIPS II (More Instructions)

To be updated.

---

## Lecture 9: MIPS III (Instruction Formats and Encoding)

To be updated.

---

## Lecture 10: Instruction Set Architecture

To be updated.

---

## Lecture 11: Processor: Datapath

To be updated.

---

## Lecture 12: Processor: Control

To be updated.
