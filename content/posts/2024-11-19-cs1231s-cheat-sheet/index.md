---
title: "CS1231S Discrete Structures"
date: "2024-11-19"
summary: "These are things I found pretty helpful as an average student. They might not cover everything, but I refer to them whenever I need some intuition."
toc: true
readTime: true
autonumber: false
math: true
tags: ["Course Notes"]
showTags: true
---

**Note**: Taken in AY2024/25 Semester 1

## Real Numbers

- **T11 - Zero Product Property**: $ab = 0 \implies a = 0 \lor b = 0$
- **T21:** $a \neq 0 \implies a^2>0$.
- **T25**: If the product of two numbers is positive, then both numbers are either positive or both are negative
- **T27**: $\forall a, b, c \in \mathbb{R}$ $((0 < a < c \land 0 < b < d) \implies 0 < ab < cd)$.
- **Ord1**: If $a$ and $b$ are positive,
  so are $a+b$ and $ab$.

---

## Tutorial 1 - 2 (Logic and Proofs)

- The statement "$q$ if $p$" or "$p$ only if $q$" means $p\implies q$. Here, $p$ is a sufficient condition for $q$, and $q$ is a necessary condition for $p$.
- To prove statements aren't equivalent, we can plug in truth values and show that some rows in their truth tables don’t match.
- The contrapositive of $p\implies q$ is $\neg q \implies \neg p$, which are equivalent. The inverse, $\neg p \implies \neg q$, is equivalent to the converse, $q \implies p$.
- **Valid Argument**: If all premises are true (critical rows), the conclusion must also be true. An argument is invalid if the conclusion can be false, even when the premises are true.
- **Transitive Rule of Inference**: $((p\implies q) \land (q\implies r))\implies (p\implies r)$.
- **Implication Law**: $p \implies q \equiv \neg p \lor q$.
- **Negation of a Conditional Statement**: $\neg (p\implies q)\equiv p\land \neg q$
- **De Morgan's Laws**: $\neg(p \land q) \equiv \neg p \lor \neg q$ and $\neg(p \lor q) \equiv \neg p \land \neg q$.
- **Absorption Law**: $p \lor (p \land q) \equiv p$ and $p \land (p \lor q) \equiv p$.
- **Double Negative Law**: $\neg(\neg p) \equiv p$.
- **Commutative Law**: $p \lor q \equiv q \lor p$ and $p \land q \equiv q \land p$.
- **Distributive Law**: $p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$ and $p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$.
- **Negation Law**: $p \lor \neg p \equiv \text{True}$ and $p \land \neg p \equiv \text{False}$.
- **Identity Law**: $p \lor \text{False} \equiv p$ and $p \land \text{True} \equiv p$.
- It’s good practice to write statements inside brackets **after a quantifier**, like $\forall x\in A(P(x))$ or $\forall x \in A$ such that $P(x)$, to clearly show that $x$ is bounded. Otherwise, $x$ could be a **free variable**.

---

## Tutorial 3 (Sets)

- **Proving subset $A\subseteq B$**: Select an arbitrary element $x \in A$ and show that $x \in B$
- **Proving set equality**: $A = B \iff (A \subseteq B \land B \subseteq A)$, alternatively use set identities below.
- **Theorem 6.2.1**: $A \subseteq B \land B \subseteq C \implies A \subseteq C$.
- **De Morgan's Law**: $\overline{A \cap B} = \overline{A} \cup \overline{B}$ and $\overline{A \cup B} = \overline{A} \cap \overline{B}$.
- **Set Difference Law**: $A \setminus B = A \cap \overline{B}$
- **Double Complement Law**: $\overline{\overline{A}} = A$
- **Commutative Law**: $A \cup B = B \cup A$ and $A \cap B = B \cap A$
- **Distributive Law**: $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
- **Complement Law**: $A \cup \overline{A} = U$ (where $U$ is the universal set)
- **Identity Law**: $A \cap U = A$ (where $U$ is the universal set)

---

## Tutorial 4 - 5 (Relations)

- A **symmetric relation** also implies $R=R^{-1}$.
- A **composite relation** $S\circ R$ means we apply $R$ first and then $S$. Additionally, the composition of more than two relations is associative, i.e., $(T\circ S)\circ R=T\circ(S\circ R)$.
- The **equivalence class** of **an element $a$** under an equivalence relation $\sim$, denoted as $[a]$, is the set of all elements that are equivalent to $a$.
- For a partial order $\preceq$ on a set $A$, two elements $a,b\in A$ **are compatible** $\iff$ there exists an element $c$ such that $a\preceq c \land b\preceq c$.
- **Equivalence Relations and Composition**: (a) $R^{-1} \circ R = R \circ R^{-1}$, (b) $R = R \circ R$, and (c) $R \circ R^{-1} = R$.
- **Lemma Rel.1 - Equivalence Classes**: For all $x, y \in A$ with equivalence relation $\sim$, the following are equivalent: (i) $x \sim y$, (ii) $[x] = [y]$, (iii) $[x] \cap [y] \neq \emptyset$
- A **linear extension** of a partial order is a total order where all elements are comparable. To count the number of possible linearizations, we can use **recursion** to add **minimal elements**, accordingly.
- A **chain** in a partial order is a subset where every pair of elements is comparable, forming a total order. Its length is **one less than** the number of elements. A **maximal chain** is a chain $M$ that cannot be extended by adding more elements.

---

## Tutorial 6 (Functions)

- A function takes an **input from the domain** and gives **a single output in the codomain**. No input can have more than one output and each input needs to have an output.
- **(Theorem 7.2.3)** The **composition** of two or more injective functions is also **injective**, and **(Theorem 7.2.4)** the **composition** of two or more surjective functions is also **surjective**.
- A function is **injective ($\forall x_1,x_2 (f(x_1)=f(x_2)\implies x_1=x_2$))** $\iff$ it has a **left inverse**, and is **surjective ($\forall y,\exists x,f(x)=y$)** $\iff$ it has a **right inverse**.

---

## Tutorial 7 (Mathematical Induction)

- **Mathematical Induction (MI)**: Define $P(n)$, prove base case, assume $P(k)$ true, prove $P(k) \implies P(k+1)$, conclude $P(n)$ true for all $n \geq$ base case.
- **Strong Mathematical Induction (Strong MI)**: Define $P(n)$, prove base case, assume $P(i), P(i+1), \dots, P(k)$ true, prove $P(i) \land P(i+1) \land \dots \land P(k) \implies P(k+1)$, conclude $P(n)$ true for all $n \geq$ base case.

---

## Tutorial 8 (Cardinality)

- **Proposition 9.1**: An infinite set $B$ is countable $\iff$ there is a sequence $b_0, b_1, b_2, \ldots$ in which every element of $B$ appears **exactly once**.
- **Lemma 9.2**: An infinite set $B$ is countable $\iff$ there is a sequence $b_0, b_1, b_2, \ldots$ in which every element of $B$ appears.
- **Proposition 9.3**: Every infinite set has a countably infinite subset.
- **Lemma 9.4**: Let $A$ and $B$ be countably infinite sets. Then $A \cup B$ is countable. This also generalizes to the countability of $\bigcup\limits_{i=1}^{\infty} A_{i}$.
- **Pigeonhole Principle (PHP)**: Let $A$ and $B$ be finite sets. If there is an injection $f: A\to B$, then the cardinality of $A$ is $\leq$ that of $B$.
- **$\mathbb{Z}^+ \times \mathbb{Z}^+$ is countable**: Used in the proof that the union of countably infinite sets indexed by $\mathbb{Z}^+$ is countable.

---

## Tutorial 9 - 10 (Counting and Probability)

- **Inclusion-Exclusion Principle**: $P(A\cup B\cup C)=P(A)+P(B)+P(C)-P(A\cap B)-P(A\cap C)-P(B\cap C)+P(A\cap B\cap C)$.
- **Number of Circular Permutations**: $(n-1)!$ (fix one object and permute the rest).
- **Generalized PHP**: If $n$ objects are placed into $k$ boxes, then there is **at least one box** containing **at least** $\lceil n/k \rceil$ **objects**.
- **Stars and Bars**: For placing $n$ indistinguishable objects into $k$ boxes, the number of ways depends on the **constraint of minimum objects per box**: $\displaystyle\binom{n+k-1}{k-1}$ when boxes can be empty, $\displaystyle\binom{n-1}{k-1}$ with **at least one** object per box ($n+k-1-k=n-1$).
- **Binomial Theorem**: $\displaystyle(x+y)^n=\sum_{k=0}^n\binom{n}{k}x^{n-k}y^k$.
- **Linearity of Expected Value**: $E(X_1+X_2+\cdots+X_n)=E(X_1)+E(X_2)+\cdots+E(X_n)$.

---

## Tutorial 10 - 11 (Graphs and Trees)

- **Theorem 10.1.1**: The total degree of a graph is $2$ times the number of edges (which is even).
- **Proposition 10.1.3**: In any graph, there are an even number of edges with odd degree.
- **Lemma 10.2.1**: Let $G$ be a graph. (a) If $G$ is connected, then any two distinct vertices of $G$ can be connected by a path. (b) If vertices $v$ and $w$ are part of a circuit in $G$ and one edge is removed from the circuit, then there still exists a trail from $v$ to $w$ in $G$. (c) If $G$ is connected and $G$ contains a circuit, then an edge of the circuit can be removed without disconnecting $G$.
- **Theorem 10.2.4**: A graph $G$ has an Euler circuit $\iff$ $G$ is connected and every vertex of $G$ has positive even degree.
- **Corollary 10.2.5**: Let $G$ be a graph, and let $v$ and $w$ be two distinct vertices of $G$. There is an Euler trail from $v$ to $w$ $\iff G$ is connected, $v$ and $w$ have odd degree, and all other vertices of G have positive even degree.
- **Proposition 10.2.6**: If a graph $G$ has a Hamiltonian circuit, then $G$ has a subgraph $H$ with the following properties:

  1. $H$ contains every vertex of $G$.
  2. $H$ is connected.
  3. $H$ has the same number of edges as vertices.
  4. Every vertex of $H$ has degree 2.

- If $A$ is the adjacency matrix of a graph $G$, then $A_{ij}=A_{ji}$ if $G$ is undirected (symmetric). Additionally, $A^n_{ij}$ gives the numbers of walks of length $n$ (have $n$ edges in the walks) from vertex $i$ to vertex $j$.
- For a graph $G$ with $n$ vertices, if $G$ is $K_n$ **(complete graph)**, then it has $n(n-1)/2$ edges, and if $G$ is $K_{m,n}$ **(complete bipartite graph)**, then it has $mn$ edges.
- A **self-complementary** graph is **isomorphic** with its complement.
- **Theorem 10.4.1**: Let $S$ be a set of graphs and let $\cong$ be the relation of graph isomorphism on $S$. Then $\cong$ is an equivalence relation on $S$.
- A **dominating Set ($D$)** in a graph $G$ is a subset of vertices such that every vertex not in $D$ is adjacent to some vertex in $D$. The **minimal dominating set** is a set such that **none of its proper subsets** are dominating.
- **Euler's Formula**: For a planar graph $G$ with $e$ edges, $v$ vertices, and $f$ faces: $f=e-v+2$.
  - If $G$ is a simple planar graph with $v\geq 3$, then $e\leq 3v-6$.
  - If $G$ is a bipartite planar graph with $v\geq 3$, then $e\leq 2v-4$.
- **Number of Spanning Trees**: For a tree, there's 1 spanning tree; for a cyclic graph with $n$ vertices, $n$ spanning trees (there are $n$ ways to remove one edge); for a complete graph with $n$ vertices, $n^{n-2}$ spanning trees (Cayley's formula).
- **Kruskal's Algorithm**: Add minimum-weight edges without creating cycles until all vertices are included.
- **Prim's Algorithm**: Start with an arbitrary node, progressively add minimum-weight edges connecting to unvisited vertices.
- **Theorem 10.5.2**: Any tree with $n$ vertices ($n > 0$) has $n − 1$ edges.
- **Lemma 10.5.5**: Let $G$ be a simple, undirected graph. If there are two distinct paths from a vertex $v$ to a different vertex $w$, then $G$ contains a cycle (and hence $G$ is cyclic).
- **Proposition 10.7.1**: (i) Every connected graph has a spanning tree. (ii) Any two spanning trees for a graph have the same number of edges.
- We can systematically **draw non-isomorphic trees** by **progressively increasing node degrees** or by **modifying trees with one less vertex** by adding connections at different positions.
- **Binary Tree Traversal**: **Preorder** (Node, Left, Right), **Inorder** (Left, Node, Right), **Postorder** (Left, Right, Node); unique trees determined by combining Preorder with Inorder or Inorder with Postorder.
- With only inorder traversal, $2^n - n$ distinct binary trees can be drawn with $n$ vertices.
