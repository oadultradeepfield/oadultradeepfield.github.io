---
tags: NUS-Courses
---

# CS2040S Probem Sets Part 1

> If you need your software to run twice as fast, hire better programmers. But if you need your software to run more than twice as fast, use a better algorithm.
>
> — _Software Lead at Microsoft (Cited from the Lecture)_

I am taking CS2040S in AY2024/25 Semester 2 and plan to compile useful tricks and mistakes I made during the problem sets, which I corrected after researching before submission, of course. I aim to update this blog weekly or whenever I discover something new, if possible. While the title focuses on problem sets, I may also include lecture reviews or optional problems from the week if I find them interesting.

**Note**: Part 1 refers to the content covered before the midterm (first recess week), which primarily focuses on data structures, while Part 2 will cover algorithms.

## PS1: Getting Started

This problem involved implementing a linear-feedback shift register, with the tricky part being how to shift the array of bits (represented as `int` in Java) to the right by one position while replacing the leftmost element with a value derived from the previous state. In this example, the leftmost element is computed as the XOR of the rightmost element with a specified element.

Here is my final code:

```java
public class ShiftRegister {
    private int[] seed; // Array of bits
    private final int size; // Size of the array
    private final int tap; // Index of the element used to compute XOR

    ShiftRegister(int size, int tap) {
        this.size = size;
        this.tap = tap;
    }

    // Implementation hidden
    // ...

    public int shift() {
        int mostSignificantBit = this.seed[size - 1];
        int feedback = this.seed[this.tap] ^ mostSignificantBit;

        for (int i = size - 1; i > 0; i--) {
            this.seed[i] = this.seed[i - 1];
        }

        this.seed[0] = feedback;
        return feedback;
    }

    // Implementation hidden
    // ...
}
```

This code can handle the edge case when `size = 1`, as the loop will not be executed. The mistake I initially made was iterating through the array from `i = 0` to `i = size - 1` inclusively. This approach is more complicated because it requires caching some value beforehand; otherwise, updating the current element in a forward iteration causes a chain effect, replacing subsequent elements with the same value.

By iterating in reverse, the previous values at `i - 1` remain unchanged during the iteration, which solves the problem effectively.

For comparison, here is an example of the forward iteration approach:

```java
// Example for direct (forward) iteration
int prev = this.seed[0];

for (int i = 1; i < size; i++) {
    int temp = this.seed[i];
    this.seed[i] = prev;
    prev = temp;
}
```

Additionally, the optional part of this problem set involved a form of bit manipulation.

---

## PS2: Load Balancing

To be updated.

---

## PS3: The Sorting Detectives

To be updated.
