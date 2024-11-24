---
tags: NUS Cheat Sheet
---

# CS1231S Discrete Structures Cheat Sheet (Open-Book)

> _These are things I found pretty helpful as an average student. They might not cover everything, but I refer to them whenever I need some intuition._

**Note**: Taken in AY2024/25 Semester 1

## Propositional Logic and Proofs

- **Argument Validity**: An argument with premises $p_1$, $p_2$, ...,
  $p_k$ and conclusion $q$ is valid if and only if $(p_1 \land p_2 \land \cdots \land p_k) \rightarrow q$ is a tautology.

- **Tautology**: A propositional statement that is always true,
  regardless of the truth values of its variables.

- **Necessary Condition**: In a conditional statement \"If $p$, then
  $q$\", $p$ is a necessary condition for $q$.

- **Sufficient Condition**: In a conditional statement \"If $p$, then
  $q$\", $q$ is a sufficient condition for $p$.

- **If and Only If ($\leftrightarrow$)**: A logical connective that
  combines \"if\" and \"only if\". $p \leftrightarrow q$ is equivalent
  to $(q \rightarrow p) \land (p \rightarrow q)$.

- **Necessary and Sufficient Condition**: In the statement \"$p$ if
  and only if $q$\", $p$ is a necessary and sufficient condition for
  $q$.

- **De Morgan's Law**: $\sim (p \land q) \equiv \sim p \lor \sim q$
  and $\sim (p \lor q) \equiv \sim p \land \sim q$.

- **Implication Law**: $p \rightarrow q \equiv \sim p \lor q$.

- **Absorption Law**: $p \land (p \lor q) \equiv p$ and $p \lor (p \land q) \equiv p$.

- **Negation Law**: $p \land \sim p \equiv \mathrm{false}$.

- **Critical Row Method**: An argument is valid if and only if the
  conclusion is true in every row of the truth table where all the
  premises are true.

- **Converse Error**: Assuming that the converse is also true.

- **Inverse Error**: Assuming that the inverse is also true.

- **Counterexample**: An example that shows the falsity of a
  statement.

## Predicate Logic

- **Universal Quantifier ($\forall$)**: Means \"for all\" or \"for
  every\".

- **Existential Quantifier ($\exists$)**: Means \"there exists\" or
  \"for some\".

- **Domain**: The set of all possible values that a variable can take.

- **Well-formed Formula (wff)**: A syntactically correct expression.

- **Predicate**: A function that takes arguments and returns a truth
  value.

- **Universal Generalization**: If a property holds for an arbitrarily
  chosen element of a set, then it holds for all elements of the set.

## Sets

- **Power Set ($\mathcal{P}(A)$)**: The set of all subsets of $A$.

- **Set-Builder Notation**: A way to define a set by specifying the
  properties of its elements.

- **Interval Notation**: A shorthand way of representing intervals of
  real numbers.

- **Cartesian Product ($A \times B$)**: The set of all ordered pairs
  $(a, b)$ where $a$ is in $A$ and $b$ is in $B$.

- **Set Equality**: Two sets are equal $\leftrightarrow$ they have the
  same elements.

- **Subset ($\subseteq$)**: A set $A$ is a subset of a set $B$ if and
  only if every element of $A$ is also an element of $B$.

- **Partition**: A collection of non-empty, mutually disjoint subsets
  of a set whose union is the entire set.

- **Zero Product Property (Appendix A T11)**: This property states
  that if the product of two numbers is zero, then at least one of the
  numbers must be zero.

## Relations and Equivalence Relations

- **Relation**: A set of ordered pairs.

- **Inverse Relation ($R^{-1}$)**: The relation obtained by reversing
  the order of the pairs in $R$.

- **Composition of Relations ($S \circ R$)**: For relations
  $R \subseteq A \times B$ and $S \subseteq B \times C$,
  $R \circ S = \{(a, c) | \exists b \in B , ((a, b) \in R \land (b, c) \in S)\}$.

- **Associativity of Composition**:
  $(T \circ S) \circ R = T \circ (S \circ R)$.

- **Reflexivity**: A relation $R$ on a set $A$ is reflexive
  $\leftrightarrow$ for every $x$ in $A$, $xRx$.

- **Symmetry**: A relation $R$ on a set $A$ is symmetric
  $\leftrightarrow$ for every $x$ and $y$ in $A$, if $xRy$ then $yRx$.

- **Transitivity**: A relation $R$ on a set $A$ is transitive
  $\leftrightarrow$ for all $x$, $y$, and $z$ in $A$, if $xRy$ and
  $yRz$, then $xRz$.

- **Equivalence Relation**: A relation that is reflexive, symmetric,
  and transitive. For an equivalence relation $\sim$ on a set $X$, an
  equivalence class $[x] = \{y \in X | x \sim y\}$.

- **Lemma Rel.1 Equivalence Classes**: Let $\sim$ be an equivalence
  relation on a set $A$. The following are equivalent for all
  $x, y \in A$: (i) $x \sim y$; (ii) $[x] = [y]$; (iii)
  $[x] \cap [y] \neq \emptyset$.

## Partial Orders

- **Partial Order ($\preceq$)**: A reflexive, antisymmetric, and
  transitive relation.

- **Comparable Elements**: Two elements are comparable if one is
  related to the other by the partial order.

- **Compatible Elements**: Two elements are compatible if there exists
  a third element that is greater than or equal to both.

- **Hasse Diagram**: A graphical representation of a partial order
  where elements are represented by points, and an upward line is
  drawn from $x$ to $y$ if and only if $x \preceq y$ and there is no
  element $z$ such that $x \preceq z \preceq y$.

- **Minimal Element**: An element $x$ in a partially ordered set such
  that there is no element $y$ in the set with $y \preceq x$.

  **Smallest Element**: An element $x$ in a partially ordered set such
  that $x \preceq y$ for all elements $y$ in the set.

  **Maximal Element**: An element $x$ in a partially ordered set such
  that there is no element $y$ in the set with $x \preceq  y$.

  **Largest Element**: An element $x$ in a partially ordered set such
  that $y \preceq x$ for all elements $y$ in the set.

- **Linearization ($\preceq^*$)**: A total order that extends the
  partial order.

- **Well-ordered Set**: A partially ordered set where every non-empty
  subset has a smallest element.

## Functions

- **Function**: A relation that assigns to each element in the domain
  exactly one element in the codomain.

- **Domain**: The set of all possible input values of a function.

- **Codomain**: The set of all possible output values of a function.

- **Range**: The set of all actual output values of a function.

- **Image**: For a function $f: X \rightarrow Y$ and a set
  $A \subseteq X$, $f(A) = \{f(x) \mid x \in A\}$.

- **Injective (One-to-One)**: A function where no two distinct
  elements in the domain map to the same element in the codomain.

- **Surjective (Onto)**: A function where every element in the
  codomain is mapped to by at least one element in the domain.

- **Bijective (One-to-One/Onto)**: A function that is injective and
  surjective.

- **Inverse Function ($f^{-1}$)**: A function that reverses the
  mapping of the original function. Exists if and only if the original
  function is bijective.

- **Theorem 7.2.3**: If $f: X \rightarrow Y$ is a bijection, then
  $f^{-1}: Y \rightarrow X$ is also a bijection. In other words,
  $f: X \rightarrow Y$ is bijective iff $f$ has an inverse.

- **Theorem 7.3.3**: If $f: X \rightarrow Y$ and $g: Y \rightarrow Z$
  are both injective, then $g \circ f$ is injective.

- **Theorem 7.3.4**: If $f: X \rightarrow Y$ and $g: Y \rightarrow Z$
  are both surjective, then $g \circ f$ is surjective.

- **Functional Equality**: Two functions $f: X \rightarrow Y$ and
  $g: X \rightarrow Y$ are equal, denoted $f = g$, if and only if they
  have the same domain, codomain, and $f(x) = g(x)$ for all $x \in X$.

## Mathematical Induction and Recursion

- **Principle of Mathematical Induction**: If a statement $P(n)$ is
  true for $n = 1$ (base case) and whenever $P(k)$ is true, $P(k + 1)$
  is also true (inductive step), then $P(n)$ is true for all positive
  integers $n$.

- **Strong Mathematical Induction**: If a statement $P(n)$ is true for
  $n = 1$ (base case) and whenever $P(1)$, $P(2)$, $\dots$, $P(k)$ are
  true, $P(k + 1)$ is also true (inductive step), then $P(n)$ is true
  for all positive integers $n$.

- **Recursive Definition**: Defining an object in terms of itself,
  with:

  - A **base clause**, specifying initial element(s).

  - A **recursion clause**, defining how new elements are
    constructed from existing ones.

  - A **minimality clause**, ensuring no other elements belong
    except those generated by the previous two clauses.

- **Well-Ordering Principle**: Every non-empty subset of the natural
  numbers has a least element.

## Cardinality

- **Countable Set**: A set that is either finite or can be put into
  one-to-one correspondence with the set of natural numbers.

- **Uncountable Set**: A set that is not countable.

- **Pigeonhole Principle**: If $n$ items are put into $m$ containers,
  with $n > m$, then at least one container must contain more than one
  item.

- **Generalised Pigeonhole Principle (PHP)**: If $n$ items are put
  into $m$ containers, with $n > m$, then at least one container must
  contain more than one item.

- **Lemma 9.2**: An infinite set $B$ is countable if and only if there
  is a sequence $b_0, b_1, b_2, \ldots$ in which every element of $B$
  appears.

- **Lemma 9.4**: Let $A$, $B$ be countably infinite sets. Then
  $A \cup B$ is countable.

- **Proposition 9.1**: An infinite set $B$ is countable
  $\leftrightarrow$ there is a sequence $b_0, b_1, b_2, \ldots \in B$
  in which every element of $B$ appears exactly once.

- **Proposition 9.3**: Every infinite set has a countably infinite
  subset.

## Counting and Probability

- **Sum Rule**: If a task can be done in one of $m$ ways or in one of
  $n$ ways, where none of the $m$ ways is the same as any of the $n$
  ways, then there are $m + n$ ways to do the task.

- **Product Rule**: If a task can be done in $m$ ways and a second
  task can be done in $n$ ways after the first task has been done,
  then there are $m \times n$ ways to do both tasks.

- **Principle of Inclusion-Exclusion**: For two sets $A$, $B$, and
  $C$, $|A \cup B| = |A| + |B| - |A \cap B|$. This generalizes for
  more sets:
  $|A \cup B \cup C| = |A| + |B| + |C| - |A \cap B| - |A \cap C| - |B \cap C| + |A \cap B \cap C|$.

- **Permutation**: An arrangement of $n$ distinct objects in a
  specific order:
  $$P(n, r) = \frac{n!}{(n-r)!}, \quad \text{where } r \leq n,$$
  Permutation with Repetition Allowed: $n^r$,

  Multiset Permutation: $$\frac{n!}{n_1! \, n_2! \, \cdots \, n_k!}.$$

- **Combination**: A selection of $r$ objects from $n$ distinct
  objects without regard to order:
  $$C(n, r) = \binom{n}{r} = \frac{n!}{r!(n-r)!}$$
  Combination with
  Repetition Allowed (Stars and Bars):
  $$C(n+r-1, r) = \binom{n+r-1}{r}.$$

- **Binomial Theorem**: The expansion of $(a + b)^n$ is given by:
  $$(a + b)^n = \sum_{k=0}^{n} \binom{n}{k} a^{n-k} b^k.$$

- **Conditional Probability**:
  $$P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) \neq 0.$$

- **Bayes' Theorem**:
  $$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}.$$

* **Expected Value**: The expected value of a random variable $X$ is the long-run average value it takes over many trials and is defined as: $E(X) = \sum_{x \in \text{Range}(X)} x \cdot P(X = x)$.

* **Linearity of Expected Value**: The expected value of the sum of random variables is the sum of their expected values, regardless of whether they are independent: $E(aX + bY + c) = aE(X) + bE(Y) + c$, where $a$, $b$, and $c$ are constants.

## Graphs

- **Graph**: A collection of vertices (nodes) and edges (connections
  between vertices). A graph can be directed or undirected.

- **Simple Graph**: A graph with no loops or multiple edges between
  the same pair of vertices.

- **Multigraph**: A graph that may have multiple edges between the
  same pair of vertices.

- **Weighted Graph**: A graph where edges have associated weights
  (values).

- **Complement Graph ($\overline{G}$)**: A graph with the same
  vertices as $G$, where two vertices are adjacent in $\overline{G}$
  if and only if they are not adjacent in $G$.

- **Self-Complementary**: A graph that is isomorphic to its
  complement.

- **Degree of a Vertex ($\deg(v)$)**: The number of edges incident to
  a vertex $v$ in an undirected graph. For directed graphs:

  - **In-degree**: Number of incoming edges.

  - **Out-degree**: Number of outgoing edges.

- **Handshaking Lemma**: $\displaystyle\sum_{v \in V} \deg(v) = 2|E|$
  for undirected graphs.

- **Path**: A sequence of vertices where each pair of consecutive
  vertices is connected by an edge. A **simple path** has no repeated
  vertices.

- **Cycle**: A closed path in a graph that does not repeat vertices or
  edges (except the starting and ending vertex).

- **Triangle**: A cycle of length three.

- **Spanning Tree**: A subgraph that is a tree, includes all the
  vertices of the original graph, and is acyclic and connected.

- **Connected Graph**: A graph where there is a path between any two
  vertices. A **strongly connected graph** (directed) has paths in
  both directions for every pair of vertices.

- **Acyclic Graph**: A graph that contains no cycles. A **tree** is a
  connected acyclic graph.

- **Complete Graph ($K_n$)**: A graph where every pair of vertices is
  connected by an edge.
  $\displaystyle|E| = \binom{n}{2} = \frac{n(n-1)}{2}$.

- **Bipartite**: A graph whose vertices can be divided into two
  disjoint sets such that every edge connects a vertex in one set to a
  vertex in the other.

- **Complete Bipartite Graph ($K_{m,n}$)**: A bipartite graph where
  every vertex in the first set is connected to every vertex in the
  second set. $|E| = m \cdot n$.

- **Planar**: A graph that can be drawn in the plane without crossing
  edges.

- **Planarity Condition (Euler's Formula)**: $|V| - |E| + |F| = 2$ for
  planar graphs, where $V$ is vertices, $E$ is edges, and $F$ is
  faces.

- **Eulerian Path**: A path that traverses every edge of a graph
  exactly once. An **Eulerian Circuit** starts and ends at the same
  vertex.

- **Hamiltonian Path**: A path that visits every vertex of a graph
  exactly once. A **Hamiltonian Cycle** is a Hamiltonian Path that
  starts and ends at the same vertex.

- **Adjacency Matrix**: A square matrix used to represent a graph,
  where the entry at row $i$ and column $j$ indicates the presence
  (and optionally the weight) of an edge between vertices $i$ and $j$.
- **Isomorphic Graphs**: Two graphs $G_1 = (V_1, E_1)$ and $G_2 = (V_2, E_2)$ are isomorphic if there exists a bijection $f: V_1 \to V_2$ such that any two vertices $u, v \in V_1$ are adjacent in $G_1$ if and only if $f(u)$ and $f(v)$ are adjacent in $G_2$.

## Trees

- **Tree**: A connected acyclic graph.

- **Binary Tree**: A tree where each node has at most two children.

- **In-Order Traversal**: Visit the left, then the root, then the
  right subtree.

- **Pre-Order Traversal**: Visit the root, then the left, then the
  right subtree.

- **Post-Order Traversal**: Visit the left, the right subtree, then
  the root.

- **Minimum Spanning Tree (MST)**: A spanning tree with the smallest
  possible total edge weight.

- **Kruskal's Algorithm**: A greedy algorithm for finding an MST by
  repeatedly adding the smallest weight edge that does not create a
  cycle.

- **Prim's Algorithm**: A greedy algorithm for finding an MST by
  starting at an arbitrary vertex and repeatedly adding the smallest
  weight edge that connects to a vertex not yet in the tree.

- **Lemma 10.5.5**: Let $G$ be a simple, undirected graph. If there
  are two distinct paths from a vertex $v$ to a different vertex $w$,
  then $G$ contains a cycle (and hence $G$ is cyclic).

- **Proposition 10.7.1**:

  - Every connected graph has a spanning tree.

  - Any two spanning trees for a graph have the same number of
    edges.

- **Theorem 10.5.2**: Any tree with $n$ vertices ($n > 0$) has $n - 1$
  edges.

![image](/img/meme/cheerful.jpg)
