---
tags: NUS-Courses
---

# CS2040S Common Mistakes

> _"An algorithm must be seen to be believed."_
> 
> — _Donald Knuth_

Initially, I thought noting only DSA techniques and tricks would be adequate for this course. Not so long ago that I realize midterm and final exams are MCQs which are mostly the same style as the lecture review quizzes. I note all my mistakes here to make sure I am not doing it again.

## Time Complexity

- We say that $O(f(n)) = O(g(n))$ only if $f(n)$ can be written as a constant times $g(n)$. As a result, we can say that $O(\log\_2(n)) = O(\log\_{10}(n))$ since logarithms with different bases can be converted using a constant factor. However, $O(2^n) \neq O(2^{2n})$ because $2^{2n}$ grows exponentially faster than $2^n$.

---

## Binary Search and Peak Finding

- The **precondition** is that the input array is sorted; this is required for the function to work correctly.  
- The **postcondition** is that if the element is in the array, it will be found. In general, postconditions describe what ensures the algorithm achieves its intended purpose.  
- The **loop invariant** (the condition that is true at the beginning and end of the loop) is that `A[begin] <= key <= A[end]`.  
- A **peak** in this course can be equal to its surroundings, while a strict peak is called a **steep peak**.

