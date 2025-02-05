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

Permutations and combinations are the classic problems that I even learned in CS1101S. I think the recursion idea is not complicated. The tricky part is writing the code to implement while handling language-specific paradigms. But the general idea is that if you have to permute `[1,2,3]`, you can separate the problem into trying to insert `1` to all possible permutations of `[2,3]`, which is

```
[1, 2, 3], [2, 1, 3], [2, 3, 1]
```

If you realize that the `[2,3]` can be permuted to `[3,2]`, we now get another list to insert, resulting in

```
[1, 3, 2], [3, 1, 2], [3, 2, 1]
```

If we combine the two lists, we have found all possible permutations of the 1, 2, and 3. The base case is the empty permutation, which we will return `[[]]`. In Python, we can write what we have previously discussed like this:

```python
top = nums[-1]
wish = self.permute(nums[:-1])
res = []

for p in wish:
    for i in range(len(p) + 1):
        res.append(p[:i] + [top] + p[i:]) # Key Idea
```

I usually make a mistake on my first try, forgetting that the output is an array of an array of integers, not just one layer nesting. You need to add each element correspondingly, resulting in the correct permutation. This problem further depicts the beauty of recursion. You don't need to think about the underlying process. Treat it like an already correct returned value.

---

## 39. Combination Sum

Although LeetCode tagged the previous task as backtracking, I feel that the current problem is a better introduction to the algorithms. Essentially, backtracking is used in a specific scenario, where we must decide on various possible choices and validate the choice if it leads to a solution. After that, we return to the starting path and explore other solutions.

In this problem, we want to explore all possible combinations of elements in an array that sum up to the `target` value, and we may choose a single value as many times as we wish. Thus, the modified template for a helper function for backtracking looks something like this:

```python
def backtrack(index, path):
    if sum(path) == target:
        res.append(path.copy())
        return

    if sum(path) > target or index >= len(candidates):
        return

    for i in range(index, len(candidates)):
        path.append(candidates[i])
        backtrack(i, path) # Key Idea
        path.pop()
```

The condition for leaving the current path leads to a solution where we append the result or otherwise where we would leave the path. In the loop, you are basically appending a value to the path and backtracking it to see if it leads to a solution. After that, we pop it from the path to explore other solutions. Another wishfully thought example of recursion! The key idea line may be a bit tricky to understand. In some problems, we may want to use `i + 1` as the duplicates are not allowed. But it is allowed for this problem, so we want to explore itself as well.

However, there is a possible optimization to this problem. The current solution runs in $O(n^m)$ time where $n$ is the length of candidates and $m$ is the recursion depth. Additionally, we need to sum an array at each step, which takes another $O(k)$ time where $k$ is the length of the current path. One possible way is to instead keep track of the remaining to the sum, like below:

```python
def optimizedBacktrack(index, path, remaining):
    if remaining == 0:
        res.append(path.copy())
        return

    for i in range(index, len(candidates)):
        if candidates[i] > remaining:
            break
        path.append(candidates[i])
        optimizedBacktrack(i, path, remaining - candidates[i])
        path.pop()
```

This still has a similar order of growth but potentially with less constant factors. The extra works that need to be done is to sort the array first using `candidates.sort()`, which is a relatively small cost compared to the exponential growth. This approach allows us to just skip the elements that are too large, knowing that they won't make up the target (or remaining) anyway.

---

## 73. Set Matrix Zeroes

I believe this problem will be straightforward for most people. However, the difficulty is the constraint of using only $O(1)$ space complexity. This restriction forces you to use some trick to put some flags inside the matrix that will let you know which rows or columns to set as zeroes when you revisit the matrix again.

The idea is to flag the first entry of the row or column that needs to be replaced with zeroes in the first pass. But wait, how can we ensure that as we fill zeroes in the second iteration, it doesn't interfere with the flag? One solution is to only replace those from index 1 onwards, excluding the first row and column, and we may need to check initially if the first rows and columns have zero or not:

```python
# Key Idea
first_row_has_zero = any(matrix[0][c] == 0 for c in range(n))
first_col_has_zero = any(matrix[r][0] == 0 for r in range(m))

for r in range(1, m):
    for c in range(1, n):
        if matrix[r][c] == 0:
            matrix[r][0] = 0
            matrix[0][c] = 0
```

After replacing the corresponding entries with zeroes, we then replace the first rows and columns if applicable:

```python
if first_row_has_zero:
    for c in range(n):
        matrix[0][c] = 0

if first_col_has_zero:
    for r in range(m):
        matrix[r][0] = 0
```

This approach allows us to complete the problem with a time complexity of $O(mn)$ without using any extra spaces. The naive solution of using a hash set to store the rows and columns to be replaced may take at least $O(mn)$ space.

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
