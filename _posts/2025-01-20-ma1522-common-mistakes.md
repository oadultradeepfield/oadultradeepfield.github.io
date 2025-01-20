---
tag: NUS-Courses
---

# MA1522 Common Mistakes

> _"Life is a linear equation in which you can't cross multiply! If you think you can do it, you can do it. If you think you can't do it, you can't do it."_
>
> — _Israelmore Ayivor_

Like other series of courses I take in this semester, I note some of the mistakes I made i.e. misconception or some tricky terms here to help me revise faster during the exam period. Note that I know some basics of this course already since I took related courses during high school so the early part of the courses may not be written as detailed as the later.

## Equivalent Statements of Invertibility

These are the most important concepts I've noticed so far. They link many topics together, and the list continues to grow as new terms are introduced, so I place it at the top of my notes.

For a **square matrix** $\mathbf{A}$ of order $n$, the following statements are equivalent, meaning each one implies the others:

1. $\mathbf{A}$ is invertible.
2. $\mathbf{A}^T$ is invertible.
3. $\mathbf{A}$ has a left-inverse.
4. $\mathbf{A}$ has a right-inverse.
5. The RREF of $\mathbf{A}$ is the identity matrix.
6. $\mathbf{A}$ can be expressed as the product of elementary matrices.
7. $\mathbf{A}\mathbf{x} = \mathbf{0}$ has only the trivial solution.
8. $\mathbf{A}\mathbf{x} = \mathbf{b}$ has a unique solution (and thus consistent).
9. $\det(\mathbf{A})\neq 0$.
10. The columns/rows of $\mathbf{A}$ are linearly independent, form a basis, and, therefore, span $\mathbb{R}^n$.
11. $\mathbf{A}$ is full rank, that is $\text{rank}(\textbf{A})=n$.
12. $\text{nullity}(A)=0$.

---

## Chapter 1: Linear Systems

- A standard equation is written in the form $a_1x_1 + a_2x_2 + \dots + a_nx_n = b$ (with variables on one side and the constant on the other).
- A linear system is **inconsistent** if there is no solution and **consistent** if it has at least one solution.
- For 3D linear systems, there are no solutions if at least two of the planes are parallel, or if all three planes intersect but do not form a single line. A unique solution occurs when two of the planes intersect as lines, and those lines intersect at a single point.
- Based on the above, the system has infinitely many solutions (a general solution) with one parameter if the three planes intersect along a line, and with two parameters if the planes coincide.
- When analyzing augmented matrices, we consider the leading entries, including those on the right-hand side (RHS). So, if the last column (RHS) is a pivot column, there is no solution (generally be $0\ 0\ 0 \ldots\ 0\ \lvert\ b$).
- Reduced Row Echelon Form (RREF) differs from Row Echelon Form (REF) in that its leading entries are all 1's. Additionally, a pivot column in RREF contains a 1 in the leading row and 0's elsewhere.

---

## Chapter 2: Matrix Algebra

- In this course, a zero matrix can be categorized as a triangular matrix, diagonal matrix, and scalar matrix, as the definitions of these types do not require the diagonal or triangular elements to be nonzero.
- A symmetric matrix $\mathbf{A}$ satisfies the property $\mathbf{A} = \mathbf{A}^T$, and $\mathbf{A}^n$ is also symmetric (but not necessarily true for the converse).
- Every elementary matrix is invertible, and its inverse corresponds to reversing the row operation performed on $\mathbf{I}_n$ to obtain the elementary matrix.
- To get the product $\mathbf{E}\mathbf{A}$, note that the size of $\mathbf{E}$ should be $m \times m$ if $\mathbf{A}$ is $m \times n$.
- If $\mathbf{A} \xrightarrow{r_1} \xrightarrow{r_2} \dots \xrightarrow{r_k} \mathbf{B}$, then $\mathbf{B} = \mathbf{E}_k \dots \mathbf{E}_2 \mathbf{E}_1 \mathbf{A}$, which implies $\mathbf{A} = \mathbf{E}_1^{-1} \mathbf{E}_2^{-1} \dots \mathbf{E}_k^{-1} \mathbf{B}$, or equivalently, $\mathbf{B} \xrightarrow{r_k'} \dots \xrightarrow{r_2'} \xrightarrow{r_1'} \mathbf{A}$.
- To quickly obtain $\mathbf{L}$ after reducing $\mathbf{A}$ to $\mathbf{U}$, we can perform only the row operation $R_i + cR_j$ for $i > j$. We can then replace the $(i,j)$ entry of $\mathbf{L}$ with the value of $-c$.
- $\mathbf{A}\mathbf{x} = \mathbf{b}$ has a unique solution when $\mathbf{U}\mathbf{x} = \mathbf{y}$ has a unique solution, which occurs when $\mathbf{U}$ is invertible, since $\mathbf{L}$ is always invertible.
- The determinant of a triangular matrix is equal to the product of the entries along its diagonal.
- If a square matrix has two identical rows/columns or if one row/column is a scalar multiple of another, the determinant is zero.

---

## Chapter 3: Euclidean Vector Spaces

- The dot product between vectors $\mathbf{u}$ and $\mathbf{v}$ is defined as $\mathbf{u}^T\mathbf{v}$ because vectors in this course are column vectors. Consequently, $(\mathbf{u}^T\mathbf{v})^T = \mathbf{v}^T\mathbf{u} = \mathbf{v} \cdot \mathbf{u}$ is also valid, as the dot product is commutative.
- $\text{span}(S) = \mathbb{R}^n \iff$ the RREF of the matrix formed by the column vectors in $S$ has no zero rows. To span $\mathbb{R}^n$, we need at least $n$ linearly independent vectors.
- To check if $\mathbf{v}$ is a linear combination of the vectors in the set $S$, verify that the equation $\mathbf{A}\mathbf{x} = \mathbf{v}$ has a solution. To determine if the span of one set is a subset of another, check if all vectors in the first set can be expressed as a linear combination of the vectors in the second set.
- The solution set of $\mathbf{A}\mathbf{x} = \mathbf{b}$ is given by $\mathbf{u} + V$, where $\mathbf{u}$ is a particular solution of the system, and $V$ is the solution set of the homogeneous system $\mathbf{A}\mathbf{x} = \mathbf{0}$.
- All subspaces contain infinitely many vectors due to their recursive definition. However, the zero subspace is the only exception, containing exactly one element: $\mathbf{0}$.
- A set of vectors is linearly independent if and only if the homogeneous system, with the vectors as the columns of the coefficient matrix, has only the trivial solution.
- **Some Special Cases**: The empty set is linearly independent, and a set containing a single vector $\mathbf{v}$ is linearly independent if and only if $\mathbf{v} \neq \mathbf{0}$. The span of all zero vectors is the only case where the span forms a single point (the zero vector).
- Linear dependency is defined on the vector set as a whole (when there are more than two vectors) because if one vector can be expressed as a linear combination of the others, arithmetic operations on the vectors can yield similar results.
- The dimension of a subspace is determined by the minimum number of vectors needed to form a basis. Note that $\mathbb{R}^2$ is not a subspace of $\mathbb{R}^3$ since it lacks a third coordinate, but we can have a 2D plane that is a two-dimensional subspace of $\mathbb{R}^3$ by setting the third coordinate to $0$.
- When expressing coordinates relative to a basis, we always include only as many coordinates as the dimension of the subspace. However, the basis itself should have the same number of entries as the dimension of the superspace.
- Both REF and RREF have infinitely many solutions if there are non-pivot columns, as these columns correspond to free variables (parameters), which also determine the dimension of the solution space.
- Conditions to check if $S$ is a basis of subspace $V$ (both requires $\lvert S \rvert = \text{dim}(V)$):
  1. If $\text{span}(S) = V$ is not known: $S \subseteq V$ and $S$ is linearly independent.
  2. If $S$ being linearly independent is not known: $V \subseteq \text{span}(S)$.
- $U \subseteq V \iff \text{dim}(U) \leq \text{dim}(V)$, with equality if and only if $U = V$.
- To convert the basis back from the transition matrix, find the inverse of the transition matrix. Note that the transition matrix should be a square matrix with $n$ equal to the dimension.

---

## Chapter 4: Subspaces Associated to a Matrix

- Although an $m \times n$ matrix has $m$ rows and $n$ columns, the row space is a subspace of $\mathbb{R}^n$ (with $n$ coordinates), while the column space is a subspace of $\mathbb{R}^m$ (with $m$ coordinates).
- The non-zero rows of the RREF of $\mathbf{A}$ form a basis for $\text{Row}(\mathbf{A})$. However, the corresponding pivot columns of the RREF of $\mathbf{A}$ (denoted as $\mathbf{R}$) form a basis for $\text{Col}(\mathbf{A})$ (it is not preserved under row operations).
- The nullspace of $\mathbf{A}$ is the solution space of $\mathbf{A}\mathbf{x} = \mathbf{0}$. The nullity of $\mathbf{A}$ is the dimension of its nullspace, which is essentially the same as number of non-pivot columns its in RREF.
- $\text{rank}(\mathbf{A})=\text{dim}(\text{Col}(\mathbf{A}))=\text{dim}(\text{Row}(\mathbf{A}))$ and is preserved under transpose.
- $\text{Col}(\mathbf{AB})\subseteq \text{Col}(\mathbf{A})$, $\text{Rank}(\mathbf{AB})\leq \text{min}(\text{rank}(\textbf{A}), \text{rank}(\textbf{B}))$, and $\text{rank}(A)+\text{nullity}(\mathbf{A})=n$ for $m\times n$ matrix.
- For an $m \times n$ matrix $\mathbf{A}$, the following are equivalent:
  1. $\mathbf{A}$ is full rank: $\text{rank}(\mathbf{A}) = n$.
  2. The rows of $\mathbf{A}$ span $\mathbb{R}^n$: $\text{Row}(\mathbf{A}) = \mathbb{R}^n$.
  3. The columns of $\mathbf{A}$ are linearly independent.
  4. The homogeneous system $\mathbf{Ax = 0}$ has only the trivial solution: $\text{Null}(\mathbf{A}) = \{\mathbf{0}\}$.
  5. $\mathbf{A}^T \mathbf{A}$ is an invertible matrix of order $n$.
  6. $\mathbf{A}$ has a left inverse.
- For an $m \times n$ matrix $\mathbf{A}$, the following are equivalent:
  1. $\mathbf{A}$ is full rank: $\text{rank}(\mathbf{A}) = m$.
  2. The columns of $\mathbf{A}$ span $\mathbb{R}^m$: $\text{Col}(A) = \mathbb{R}^m$.
  3. The rows of $\mathbf{A}$ are linearly independent.
  4. The system $\mathbf{Ax = b}$ is consistent for all $\mathbf{b} \in \mathbb{R}^m$.
  5. $\mathbf{A} \mathbf{A}^T$ is an invertible matrix of order $m$.
  6. $\mathbf{A}$ has a right inverse.

---

## Chapter 5: Orthogonality and Least Square Solution

To be updated.

---

## Chapter 6: Eigenanalysis

To be updated.

---

## Chapter 7: Linear Transformation

To be updated.
