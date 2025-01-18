---
tag: NUS-Courses
---

# MA1522 Common Mistakes

> _"Life is a linear equation in which you can't cross multiply! If you think you can do it, you can do it. If you think you can't do it, you can't do it."_
>
> — _Israelmore Ayivor_

Like other series of courses I take in this semester, I note some of the mistakes I made i.e. misconception or some tricky terms here to help me revise faster during the exam period. Note that I know some basics of this course already since I took related courses during high school so the early part of the courses may not be written as detailed as the later.

## Chapter 1: Linear Systems

- A standard equation is written in the form $a_1x_1 + a_2x_2 + \dots + a_nx_n = b$ (with variables on one side and the constant on the other).
- A linear system is **inconsistent** if there is no solution and **consistent** if it has at least one solution.
- For 3D linear systems, there are no solutions if at least two of the planes are parallel, or if all three planes intersect but do not form a single line. A unique solution occurs when two of the planes intersect as lines, and those lines intersect at a single point.
- Based on the above, the system has infinitely many solutions (a general solution) with one parameter if the three planes intersect along a line, and with two parameters if the planes coincide.
- When analyzing augmented matrices, we consider the leading entries, including those on the right-hand side (RHS). So, if the last column (RHS) is a pivot column, there is no solution (generally be $0\ 0\ 0 \ldots\ 0\ \lvert\ b$).
- Reduced Row Echelon Form (RREF) differs from Row Echelon Form (REF) in that its leading entries are all 1's. Additionally, a pivot column in RREF contains a 1 in the leading row and 0's elsewhere. Both forms have infinitely many solutions if there are non-pivot columns, which become parameters.

---

## Chapter 2: Matrix Algebra

- In this course, a zero matrix can be categorized as a triangular matrix, diagonal matrix, and scalar matrix, as the definitions of these types do not require the diagonal or triangular elements to be nonzero.
- A symmetric matrix $\mathbf{A}$ satisfies the property $\mathbf{A} = \mathbf{A}^T$, and $\mathbf{A}^n$ is also symmetric (but not necessarily true for the converse).
- If $\mathbf{v}$ is a solution to $\mathbf{A}\mathbf{x} = \mathbf{B}$ and $\mathbf{u}$ is one of the solutions to $\mathbf{A}\mathbf{x} = \mathbf{0}$, then $\mathbf{u} + \mathbf{v}$ is also a solution to $\mathbf{A}\mathbf{x} = \mathbf{B}$. Similarly, if $\mathbf{v}_1$ and $\mathbf{v}_2$ are solutions to $\mathbf{A}\mathbf{x} = \mathbf{B}$, then $\mathbf{v}_1 - \mathbf{v}_2$ is a solution to $\mathbf{A}\mathbf{x} = \mathbf{0}$.
- Every elementary matrix is invertible, and its inverse corresponds to reversing the row operation performed on $\mathbf{I}_n$ to obtain the elementary matrix.
- To get the product $\mathbf{E}\mathbf{A}$, note that the size of $\mathbf{E}$ should be $m \times m$ if $\mathbf{A}$ is $m \times n$.
- If $\mathbf{A} \xrightarrow{r_1} \xrightarrow{r_2} \dots \xrightarrow{r_k} \mathbf{B}$, then $\mathbf{B} = \mathbf{E}_k \dots \mathbf{E}_2 \mathbf{E}_1 \mathbf{A}$, which implies $\mathbf{A} = \mathbf{E}_1^{-1} \mathbf{E}_2^{-1} \dots \mathbf{E}_k^{-1} \mathbf{B}$, or equivalently, $\mathbf{B} \xrightarrow{r_k'} \dots \xrightarrow{r_2'} \xrightarrow{r_1'} \mathbf{A}$.
- To quickly obtain $\mathbf{L}$ after reducing $\mathbf{A}$ to $\mathbf{U}$, we can perform only the row operation $R_i + cR_j$ for $i > j$. We can then replace the $(i,j)$ entry of $\mathbf{L}$ with the value of $-c$.
- $\mathbf{A}\mathbf{x} = \mathbf{b}$ has a unique solution when $\mathbf{U}\mathbf{x} = \mathbf{y}$ has a unique solution, which occurs when $\mathbf{U}$ is invertible, since $\mathbf{L}$ is always invertible.
- The determinant of a triangular matrix is equal to the product of the entries along its diagonal.
- If a square matrix has two identical rows/columns or if one row/column is a scalar multiple of another, the determinant is zero.
- **Equivalent Statements of Invertibility**: For a **square matrix** $\mathbf{A}$ of order $n$, the following statements are equivalent, meaning each one implies the others:
  1. $\mathbf{A}$ is invertible.
  2. $\mathbf{A}^T$ is invertible.
  3. $\mathbf{A}$ has a left-inverse.
  4. $\mathbf{A}$ has a right-inverse.
  5. The RREF of $\mathbf{A}$ is the identity matrix.
  6. $\mathbf{A}$ can be expressed as the product of elementary matrices.
  7. $\mathbf{A}\mathbf{x} = \mathbf{0}$ has only the trivial solution.
  8. $\mathbf{A}\mathbf{x} = \mathbf{b}$ has a unique solution (and thus consistent).
  9. $\det(\mathbf{A})\neq 0$.

---

## Chapter 3: Euclidean Vector Spaces

To be updated.

---

## Chapter 4: Subspaces Associated to a Matrix

To be updated.

---

## Chapter 5: Orthogonality and Least Square Solution

To be updated.

---

## Chapter 6: Eigenanalysis

To be updated.

---

## Chapter 7: Linear Transformation

To be updated.
