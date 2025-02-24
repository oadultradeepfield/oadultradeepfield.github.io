---
title: "Useful Stuffs from MA1522"
date: "2025-01-24"
summary: "Life is a linear equation in which you can't cross multiply! If you think you can do it, you can do it. If you think you can't do it, you can't do it (Quote by Israelmore Ayivor)"
toc: true
readTime: true
autonumber: false
math: true
tags: ["Course Notes"]
showTags: true
---

Like other series of courses I take in this semester, I note some of the mistakes I made i.e. misconception or some tricky terms here to help me revise faster during the exam period.

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
11. $\mathbf{A}$ is full rank, that is $\text{rank}(\mathbf{A})=n$.
12. $\text{nullity}(A)=0$.
13. 0 is not an eigenvalue of $\mathbf{A}$.
14. The linear transformation $T$ defined by $T\_{\mathbf{A}}(\mathbf{v})=\mathbf{Av}$ is both injective and surjective.

---

## Chapter 1: Linear Systems

- A standard equation is written in the form $a\_1x\_1 + a\_2x\_2 + \dots + a\_nx\_n = b$ (with variables on one side and the constant on the other).
- A linear system is **inconsistent** if there is no solution and **consistent** if it has at least one solution.
- For 3D linear systems, there are no solutions if at least two of the planes are parallel, or if all three planes intersect but do not form a single line. A unique solution occurs when two of the planes intersect as lines, and those lines intersect at a single point.
- Based on the above, the system has infinitely many solutions (a general solution) with one parameter if the three planes intersect along a line, and with two parameters if the planes coincide.
- When analyzing augmented matrices, we consider the leading entries, including those on the right-hand side (RHS). So, if the last column (RHS) is a pivot column, there is no solution (generally be $0\ 0\ 0 \ldots\ 0\ \lvert\ b$).
- Reduced Row Echelon Form (RREF) differs from Row Echelon Form (REF) in that its leading entries are all 1's. Additionally, a pivot column in RREF contains a 1 in the leading row and 0's elsewhere.

---

## Chapter 2: Matrix Algebra

- In this course, a zero matrix can be categorized as a triangular matrix, diagonal matrix, and scalar matrix, as the definitions of these types do not require the diagonal or triangular elements to be nonzero.
- A symmetric matrix $\mathbf{A}$ satisfies the property $\mathbf{A} = \mathbf{A}^T$, and $\mathbf{A}^n$ is also symmetric (but not necessarily true for the converse).
- Every elementary matrix is invertible, and its inverse corresponds to reversing the row operation performed on $\mathbf{I}\_n$ to obtain the elementary matrix.
- To get the product $\mathbf{E}\mathbf{A}$, note that the size of $\mathbf{E}$ should be $m \times m$ if $\mathbf{A}$ is $m \times n$.
- If $\mathbf{A} \xrightarrow{r\_1} \xrightarrow{r\_2} \dots \xrightarrow{r\_k} \mathbf{B}$, then $\mathbf{B} = \mathbf{E}\_k \dots \mathbf{E}\_2 \mathbf{E}\_1 \mathbf{A}$, which implies $\mathbf{A} = \mathbf{E}\_1^{-1} \mathbf{E}\_2^{-1} \dots \mathbf{E}\_k^{-1} \mathbf{B}$, or equivalently, $\mathbf{B} \xrightarrow{r\_k'} \dots \xrightarrow{r\_2'} \xrightarrow{r\_1'} \mathbf{A}$.
- To quickly obtain $\mathbf{L}$ after reducing $\mathbf{A}$ to $\mathbf{U}$, we can perform only the row operation $R\_i + cR\_j$ for $i > j$. We can then replace the $(i,j)$ entry of $\mathbf{L}$ with the value of $-c$.
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
- $\text{Col}(\mathbf{AB})\subseteq \text{Col}(\mathbf{A})$, $\text{Rank}(\mathbf{AB})\leq \text{min}(\text{rank}(\mathbf{A}), \text{rank}(\mathbf{B}))$, and $\text{rank}(A)+\text{nullity}(\mathbf{A})=n$ for $m\times n$ matrix.
- For an $m \times n$ matrix $\mathbf{A}$, the following are equivalent:
  1. $\mathbf{A}$ is full rank: $\text{rank}(\mathbf{A}) = n$.
  2. The rows of $\mathbf{A}$ span $\mathbb{R}^n$: $\text{Row}(\mathbf{A}) = \mathbb{R}^n$.
  3. The columns of $\mathbf{A}$ are linearly independent.
  4. The homogeneous system $\mathbf{Ax = 0}$ has only the trivial solution: $\text{Null}(\mathbf{A}) = \text{set}(\mathbf{0})$.
  5. $\mathbf{A}^T \mathbf{A}$ is an invertible matrix of order $n$.
  6. $\mathbf{A}$ has a left inverse.
  7. [The linear transformation with $\mathbf{A}$ as the standard matrix is injective.](#chapter-7-linear-transformation)
- For an $m \times n$ matrix $\mathbf{A}$, the following are equivalent:
  1. $\mathbf{A}$ is full rank: $\text{rank}(\mathbf{A}) = m$.
  2. The columns of $\mathbf{A}$ span $\mathbb{R}^m$: $\text{Col}(A) = \mathbb{R}^m$.
  3. The rows of $\mathbf{A}$ are linearly independent.
  4. The system $\mathbf{Ax = b}$ is consistent for all $\mathbf{b} \in \mathbb{R}^m$.
  5. $\mathbf{A} \mathbf{A}^T$ is an invertible matrix of order $m$.
  6. $\mathbf{A}$ has a right inverse.
  7. [The linear transformation with $\mathbf{A}$ as the standard matrix is surjective.](#chapter-7-linear-transformation)

---

## Chapter 5: Orthogonality and Least Square Solution

- A set of vectors is **orthogonal** if they are pairwise orthogonal (i.e., their dot product is zero). They are **orthonormal** if they are orthogonal and all vectors in the set are unit vectors.
- If a subspace $V$ is defined by a linear equation, the vector orthogonal to $V$ consists of those that are multiples of the coefficients of the equation.
- Any orthogonal set of nonzero vectors is linearly independent (but not vice versa).
- A matrix $\mathbf{A}$ is orthogonal if $\mathbf{A}^T = \mathbf{A}^{-1}$. Equivalently, $\mathbf{A}^T \mathbf{A} = \mathbf{I} = \mathbf{A} \mathbf{A}^T$, meaning the columns and rows of $\mathbf{A}$ form an **orthonormal** basis for $\mathbb{R}^n$.
- If we can express $\mathbf{v} = c\_1 \mathbf{u}\_1 + c\_2 \mathbf{u}\_2 + \dots + c\_k \mathbf{u}\_k$, where the set of vectors $\mathbf{u}\_i$ is an orthogonal basis, remember that each component $c\_i$ is $\frac{\mathbf{v} \cdot \mathbf{u}\_i}{\Vert\mathbf{u}\_i\Vert^2}.$ In this case, we also call $\mathbf{v}$ the orthogonal projection of some vector $\mathbf{w}$, where $\mathbf{w} = \mathbf{v} + \mathbf{w}\_n$ and $\mathbf{w}\_n$ is orthogonal to the subspace that $\mathbf{v}$ is in. It is also true that $\mathbf{v}$ is the vector in the subspace that is closest to $\mathbf{w}$.
- **Gram-Schmidt Orthogonalization**: Let $\mathbf{u} \_i$ be an element in the linearly independent set. We can create an orthonormal set of $\mathbf{v} \_i$ by using $\mathbf{v} \_k = \mathbf{u} \_k-\sum \_{i=1}^{k-1}\frac{\mathbf{v} \_i\cdot\mathbf{u} \_k}{\Vert\mathbf{v} \_i\Vert^2} \mathbf{v} \_i$, where $\mathbf{v} \_1 = \mathbf{u} \_1$. There can be a trick question where $\mathbf{v} \_k$ is $\mathbf{0}$ but $\mathbf{v} \_{k-1}$ is not. In this case, it indicates that $\mathbf{u} \_k$ is not part of a linearly independent set, since we can form $\mathbf{u} \_k$ as a linear combination of the previous elements.
- If a matrix $\mathbf{A}$ has a linearly independent columns, it can be factorized into $\mathbf{QR}$ where $\mathbf{Q}$ is a **orthonormal** columns and $\mathbf{R}=\mathbf{Q}^T\mathbf{A}$ is an upper triangular matrix with positive diagonal entries. Note that each column in $\mathbf{A}$ is also a multiple of the same column in $\mathbf{Q}$.
- A vector $\mathbf{u}$ is a least square solution to $\mathbf{Ax}=\mathbf{b}\iff \mathbf{u}$ is a solution to $\mathbf{A}^T\mathbf{Ax}=\mathbf{A}^T\mathbf{b}$, which is not guaranteed to be unique, but the projection $\mathbf{Au}=\mathbf{A}(\mathbf{A}^T\mathbf{A})^{-1}\mathbf{A}^T\mathbf{b}$ (to $\text{Col}(\mathbf{A})$) is unique.

---

## Chapter 6: Eigenanalysis

- The characteristic polynomial of $\mathbf{A}$, denoted as $\text{char}(\mathbf{A}) = \det(x\mathbf{I} - \mathbf{A})$, is used to determine the eigenvalues. An eigenvalue $\lambda$ is a root of this polynomial, implying that $(\lambda \mathbf{I} - \mathbf{A})\mathbf{x} = \mathbf{0}$ has nontrivial solutions.
- The algebraic multiplicity of $\lambda$ is the largest integer $r\_\lambda$ such that $\det(x\mathbf{I} - \mathbf{A}) = (x - \lambda)^{r_\lambda}p(x)$ for some polynomial $p(x)$, where $\lambda$ is not a root of $p(x)$.
- If $\text{char}(\mathbf{A})$ can be factored into linear terms, the roots of the polynomial are the eigenvalues.
- The eigenvalues of a triangular matrix are its diagonal entries. The algebraic multiplicity of each eigenvalue is the number of times it appears on the diagonal.
- The geometric multiplicity $\dim(E\_\lambda)$ of an eigenvalue $\lambda$ is the dimension of its associated eigenspace. Each eigenspace is linearly independent, and $1 \leq \dim(E\_\lambda) \leq r\_\lambda$.
- A square matrix $\mathbf{A}$ is diagonalizable, $\mathbf{A} = \mathbf{PDP}^{-1}$, if it has $n$ linearly independent eigenvectors. $\mathbf{D}$ is a diagonal matrix with the eigenvalues as its diagonal entries, and $\mathbf{P}$ contains the corresponding eigenvectors as its columns.
- If $\mathbf{A}$ is diagonalizable, then the geometric multiplicity equals the algebraic multiplicity for each eigenvalue.
- **Spectral Theorem**: $\mathbf{A}$ is orthogonally diagonalizable ($\mathbf{A} = \mathbf{PDP}^T$) **if and only if** $\mathbf{A}$ is symmetric. The eigenspaces of $\mathbf{A}$ are orthogonal.
- **Power of a Diagonalizable Matrix**: $\mathbf{A}^m = \mathbf{PD}^m\mathbf{P}^{-1}$, where $\mathbf{D}^m$ is obtained by raising each diagonal entry of $\mathbf{D}$ to the power of $m$. This applies to $m = -1$ (inverse) as well.
- A steady-state (equilibrium) vector for a stochastic matrix $\mathbf{P}$ is a probability vector that is an eigenvector associated with eigenvalue 1. If a Markov chain converges, it converges to this vector.
- To compute the equilibrium vector, find the eigenvector $\mathbf{u}$ associated with eigenvalue 1, then normalize it: $\mathbf{v} = \frac{\mathbf{u}}{\sum_{k=1}^n u\_k}$.
- The eigenvalues $\mu\_i$ of $\mathbf{A}^T\mathbf{A}$ are nonnegative. The singular values of $\mathbf{A}$ are $\sigma\_i = \sqrt{\mu\_i}$. When ordered in decreasing order, these are the diagonal entries of $\mathbf{\Sigma}$.
- **Singular Value Decomposition (SVD)**: $\mathbf{A} = \mathbf{U\Sigma V}^T$.
  1. Compute the eigenvalues of $\mathbf{A}^T\mathbf{A}$. For eigenvalues with algebraic multiplicity greater than one, repeat them on the diagonal of $\mathbf{\Sigma}$.
  2. $\mathbf{V}$ consists of orthonormal eigenvectors of $\mathbf{A}^T\mathbf{A}$.
  3. Compute $\mathbf{u}\_i = \mathbf{A}\mathbf{v}\_i / \sigma\_i$.
  4. If the set of $\mathbf{u}_i$ does not form an orthonormal basis ($r \neq m$), extend it to complete the basis.

---

## Chapter 7: Linear Transformation

- A mapping $T:\mathbb{R}^n\to\mathbb{R}^m$ is a linear transformation $\iff T(\alpha \mathbf{u} + \beta \mathbf{v}) = \alpha T(\mathbf{u}) + \beta T(\mathbf{v})$. We call $\mathbb{R}^n$ the domain and $\mathbb{R}^m$ the codomain. In general, this can be extended to a set of vectors.
- There are many properties of linearity; an easy way to test it is to check whether it maps $\mathbf{0}\_n$ to $\mathbf{0}\_m$. Specifically, if $T(\mathbf{0}\_n) \neq \mathbf{0}\_m$, then the transformation is not linear.
- A linear transformation exists if we can express $T(\mathbf{u}) = \mathbf{A}\mathbf{u}$. The columns of $\mathbf{A}$ correspond to the images of the standard basis vectors for $\mathbb{R}^n$. The matrix $\mathbf{A}$ is referred to as the standard matrix or the matrix representation of $T$.
- If the standard basis is not used, the image can still be constructed using the relationship $T(\mathbf{v}) = [T]\_S [\mathbf{v}]\_S$. If $\mathbf{P}$ is the transition matrix from the standard basis to $S$, then $\mathbf{A} = [T]\_S \mathbf{P}$.
- The range of $T$ is the column space of its associated standard matrix $\mathbf{A}$: $\text{Col}(\mathbf{A})$. The rank of $T$ is the dimension of its range, which is equal to $\text{rank}(\mathbf{A})$.
- The kernel of $T$ is the set of all vectors whose images under $T$ are $\mathbf{0}$. This is the same as the nullspace of $\mathbf{A}$: $\text{Null}(\mathbf{A})$. The dimension of the kernel is referred to as the nullity.
- A linear transformation is injective if $\text{ker}(T) = \text{set}(\mathbf{0})$, meaning that the equation $\mathbf{Ax} = \mathbf{0}$ has only the trivial solution.
- A linear transformation is surjective if its range is equal to its codomain. The transformation that maps the larger to smaller spaces is always surjective.
