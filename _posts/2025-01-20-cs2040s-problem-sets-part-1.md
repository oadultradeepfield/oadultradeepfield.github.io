---
tags: NUS-Courses
---

# CS2040S Probem Sets Part 1

> _"If you need your software to run twice as fast, hire better programmers. But if you need your software to run more than twice as fast, use a better algorithm."_
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

This week's problems simplify the NP-hard load-balancing problem by introducing certain assumptions. The key takeaways I want to highlight as reusable programming tricks are array partitioning and the binary search template provided below.

The primary focus this week is binary search, so let's start with the template:

```java
public static int searchArray(int[] dataArray) {
    int n = dataArray.length;

    // Implementation hidden
    // ...

    int left = 0, right = n - 1;
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (condition) { // Replace this with the specific condition
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return dataArray[left];
}
```

Binary search is simple but can be tricky to implement correctly every time. Using a consistent template can help avoid common pitfalls. Here's how it works:

1. **Initialization**: Start by initializing the `left` and `right` pointers correctly based on the context of the problem.
2. **Middle Pointer**: Create the middle pointer using `int mid = left + (right - left) / 2`. This avoids potential overflow issues when working with large numbers.
3. **Pointer Adjustment**: Use specific conditions to move the pointers and halve the search space in each iteration.
4. **Final Step**: At the end, carefully handle the result. In many problems, the `left` pointer will indicate the first element (or index) that satisfies the condition.

The follow-up technique is partitioning an array based on certain conditions. In this context, the goal is to partition the jobs such that when a processor’s load is exceeded, the next processor is used instead. Here is the example:

```java
public static boolean isFeasibleLoad(int[] jobSizes, int queryLoad, int p) {
    int n = jobSizes.length;

    if (n == 0 || queryLoad <= 0 || p <= 0) {
        return false;
    }

    int currentProcessorSum = 0;
    int processorsUsed = 1;

    for (int jobSize : jobSizes) {
        if (jobSize > queryLoad) {
            return false;
        }

        if (currentProcessorSum + jobSize > queryLoad) {
            processorsUsed++;
            currentProcessorSum = jobSize;
        } else {
            currentProcessorSum += jobSize;
        }

        if (processorsUsed > p) {
            return false;
        }
    }

    return true;
}
```

The first `if` block is used to handle invalid input and is not directly related to the main logic. The key idea is to initialize the number of used processors to be at least 1, since we will always use a processor after handling the case where `p=0`. We then iterate through the job sizes and check if each job can be assigned to the current processor. The base condition is that each job should not exceed the maximum allowed load. If the sum of jobs for the current processor exceeds the query load, we move the job to the next processor. The final condition checks if the number of processors used ever exceeds the total number of available processors.

---

## PS3: The Sorting Detectives

To be updated.

---

## Contest 1: Treasure Island

To be updated.

---

## PS4: Scapegoat Trees

To be updated.

---

## PS5: Autocomplete

To be updated.

---

## PS6: Automatic Writing

To be updated.
