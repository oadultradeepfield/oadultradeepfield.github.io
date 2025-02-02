---
tags: LeetCode
---

# Some LeetCode Problems Part 1

> _"To Be Or Not To Be"_
>
> — _LeetCode #2704_

This is the first blog of this new LeetCode problems series. The series will explore the problems I solve at multiple stages of my journey. It will be the problem I did to prepare for CVWO technical assessments in this part. I was lazy recently, so I only have a week to prepare. I will continue to update this blog as I solve more problems and explain them intuitively to help me review when needed.

Note: I will try not to write the entire code but only write down the key idea or put some explanatory text instead, so it is not rote memorization.

## 206. Reverse Linked List

I know this is one of the most classic problems. However, I usually mess this up a bit after not thinking about something recursively for a while. The thing is that I just cannot solve the problem instantly and need to take some time, which is such a shame for an easy problem.

### Recursive Solution

I usually start the problem with a recursive solution since wishful thinking will help me navigate through everything more easily. So, if we have a list like:

```
1 -> 2 -> 3 -> 4 -> 5
```

We can come up with a subproblem that tries to merge the node `1` with the reverse of the `2 -> 3 -> 4 -> 5`, which is `5 -> 4 -> 3 -> 2` and that's the idea! The next question is how do we link the last node (`2`) back to the node we left (`1`). The idea is simple, recall that the node `1` points to `2`, so calling `head.next` will bring us to `2`, and now we can assign this node to point to `1` by setting the value of `head.next.next`. Now, the `head.next` should be `None` since the first element becomes the last:

```python
new_head = reverseList(head.next)
head.next.next = head
head.next = None
```

We just need to return `new_head` since we need to return the starting point of the list. The base cases for this problem are when there is no or only a single element in the list.

### Iterative Solution

After we have the fundamental ideas, we shall implement the iterative solution, which is more memory efficient. In this problem, we can use the previous base cases as edge cases. Apart from those cases, the lists with more than two elements could be reversed by moving the `next` pointer to the previous element. The first previous element should be just `None` as we have already seen before:

```python
prev = None
curr = head

while curr:
    temp = curr.next
    curr.next = prev # Key Idea
    prev = curr
    curr = temp
```

I flag the key line with a comment. The tricky thing is to realize that after you set the `next` pointer to the previous, you lose access to the upcoming element. This issue is fixed by storing that element in the `temp` variable. We move the `prev` to the `curr` pointer to continuously move on to the next element. The `temp` is now assigned to `curr` so we can access the disconnected nodes.

---

## 155. Min Stack

This is a medium problem, but it is simpler than we might have thought. The hard part is actually knowing the trick. At some point, we may realize that the problem title is the best hint. We must keep track of the minimum element we find in the stack. Below is how I did it:

```python
def push(self, val: int) -> None:
        currentMin = val if not self.stack else min(val, self.stack[-1][1])
        self.stack.append([val, currentMin])
```

Unlike an ordinary stack, we store a list of integers instead of an integer. If there is no element in the stack, the element we are adding is the minimum. But if there is, we find the minimum between the current smallest and the input value. Since we push the element on top of the stack in order, it is guaranteed that when popping the pair out, the second entry of each stack element is always the minimum found until that point. Eventually, we can accomplish the task in $O(1)$ time.

---

## 98. Validate Binary Search Tree

This problem is another one that requires wishful thinking. Starting from the condition for a binary tree to be a binary search tree. We may note that all elements in the left subtree need to be smaller than the node value, and those on the right need to be larger than the node value. Checking the value on the current node is not enough, as we need to go through all possible nodes. Therefore, we can keep track of the bound of the current subtree to check if it not exceeds:

```python
def dfs(root, lowerBound, upperBound):
    if not root:
        return True

    if not (lowerBound < root.val < upperBound):
        return False

    # Continue
```

From the second if block, we already ensure that the current node passes the condition, so we need to check for the left and right subtree if the remaining nodes meet the condition. Therefore, we will return this:

```python
    return (
            dfs(root.left, lowerBound, root.val) and
            dfs(root.right, root.val, upperBound)
        )
```

Notice how `dfs` is a helper function. We need to call this function in the main function by setting the lower and upper bound to the values like `float(-inf)` and `float(+inf)` in Python. These two will be continuously updated as we go through each subtree.

---

## 46. Permutations

To be updated.

---

## 39. Combination Sum

To be updated.

---

## 73. Set Matrix Zeroes

To be updated.

---

## 33. Search in Rotated Sorted Array

To be updated.

---

## 56. Merge Intervals

To be updated.

---

## 62. Unique Paths

To be updated.

---

## 198. House Robber

To be updated.
