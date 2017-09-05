+++
date = "2017-08-01"
title = "The Birkhoff Polytope"
description = "An application of Hall's Theorem"
tags = [
"Matchings",
"Polytopes",
"Geometry"
]
+++

This is my first post on [combinatorial.space](http://combinatorial.space). What I have in mind for this page is to post short articles on mathematical topics that interest me, and sporadically, I'll cover other topics.

One aspect of mathematics that amazes me is the connection between seemingly unrelated concepts. For me, this is where true beauty lies, and what drives me to keep exploring all sorts of topics. We will see an interplay between graph theory and geometry by studying a class of matrices that arises in probability theory.

A real matrix `$A = (a_{ij})$` is called __doubly stochastic__ if it's entries are nonnegative and the sum of the entries of each row and each column adds up to one, that is, `$\forall j \sum_{i}a_{ij} = 1$` and `$\forall i \sum_{j}a_{ij} = 1$`. By adding all entries of the matrix columnwise and rowwise, we see that a doubly stochastic matrix should be a square matrix.

Define then `$B_n \subset \mathbb{R}^{n^2}$` as the natural embedding of the set of all doubly stochastic matrices into `$\mathbb{R}^{n^2}$`. It is easy to see that this set is convex. Indeed, any convex combination of matrices in `$B_n$` remains positive and have the stochastic property.

The set `$B_n$` is not empty, indeed, the identity matrix is doubly stochastic. Additionally, any permutation matrix `$P_\sigma = (\delta_{i,\sigma(j)})$` is doubly stochastic. Here, `$\delta_{x,y}$` is the indicator for `$x=y$`, so a permutation matrix have exactly one entry 1 on every column and every row, all other entries are 0. We have `$n!$` such matrices. It is easy to see that these matrices are the only doubly stochastic matrices with integer coordinates.
Indeed, these are the points where `$B_n$` intersects the integer lattice `$\mathbb{Z}^{n^2}$`.

Our goal is to show this characterization of `$B_n$`:

> __Theorem (Birkhoff–von Neumann)__
> The set `$B_n$` forms a convex polyhedron where the vertices are the permutation matrices.

In particular, this show that a doubly stochastic matrix can be written as a convex combination of permutation matrices. Our proof to this theorem will use perfect matchings in bipartite graphs, so we need a little detour into graph theory.

# Bipartite Graphs

A __graph__ is a pair `$G = (V,E)$` where `$V$` is a set of vertices and `$E$` is a set of pairs of vertices, called edges. When `$\{u,v\} \in E$`, we say that `$u$` and `$v$` are adjacent vertices. The edge `$\{u,v\}$` is said to be incident to `$u$` and `$v$`. Denote by `$N(v)$` neighbourhood of `$v$`, that is, the set of vertices adjacent to `$v$`. A graph is __bipartite__ when the vertex set can be partitioned into two sets, `$A$` and `$B$`, such that every edge is incident to both `$A$` and `$B$`. Alternatively, `$A$` and `$B$` forms a bipartition of `$G$` if for every vertex `$v \in A$`, we have `$N(v) \subset B$`, for every vertex `$v \in B$`, `$N(v) \subset A$`.

Let `$G = (V,E)$` be a graph. A __matching__ in `$G$` is a subset `$M \subset E$` of disjoint edges. A vertex `$v \in V$` is said to be covered by a matching if it has an edge incident to `$v$`. A matching is a __perfect matching__ if it also cover every edge of the graph.

We will study the special case of perfect matchings on bipartite graphs, in which a very natural necessary condition turns out to be sufficient. Let `$G = (V,E)$` be a bipartite graph with bipartition `$V = A \cup B$`. Clearly a perfect matching in `$G$` is only possible if `$|A| = |B|$`. Another obstacle for having a perfect matching is if there is a subset `$S \subset A$`, such that `$|N(S)| < |S|$`, where `$N(S)$` is the union of the neighbourhoods of vertices in `$S$`.

> **Theorem (Hall)**
> A bipartite graph `$G = (V,E)$` with parts `$A$` and `$B$` has a perfect matching if and only if `$|A| = |B|$` and for every subset `$S \subset A$`, we  have `$|N(S)| \geq |S|$`.

**Proof:**
The condition is clearly necessary. Indeed, for every subset `$S\subset A$`, its neighbourhood `$N(S)$` are precisely the vertices that can be used to match vertices in `$S$`. We will proceed by induction on `$n = |A| = |B|$`. The case `$n = 1$` is trivial.

For bigger `$n$`, suppose we have a proper subset `$S \subset A$` that is saturated, meaning that `$|N(S)| = |S|$`. Then we can only match vertices in `$N(S)$` with vertices in `$S$`. As `$S$` is a proper subset, one can find a perfect matching for `$S$` and `$N(S)$` by induction.

We now have to show that we can match `$A \setminus S$` with `$B \setminus N(S)$`. Note that they have the same cardinality, which is less than `$n$`. Therefore it is sufficient to show that we have Hall's condition inside this pair and apply the induction hypothesis. Let `$A' = A \setminus S$`, `$B' = B \setminus N(S)$` and `$H \subset A'$`. Suppose that `$|N(H) \cap B'| < |H|$`. Thus `$|N(H \cup S)| = |N(S) \cup (N(H)\cap B')| < |S| + |H|$`, absurd. Thus, `$|N(H) \cap B'| \geq |H|$`, so we can apply induction.

The only case left is when all proper subsets `$S \subset A$` have `$|N(S)| \geq |S| + 1$`. This case is easier as we can pick any edge `$\{ x,y \}$` to be in our perfect matching and still have Hall's condition on the remaining graph, obtained by removing both vertices. This is easy to see as for any set `$S \subset A \ \{x\}$`, its neighbourhood can be decreased by at most one.
`$\blacksquare$`

# Completing the Proof

We are now ready to prove the Birkhoff-von Neumann theorem. Given a `$n \times n$` doubly stochastic matrix `$A$`, one can associate to it a bipartite graph `$G_A$` with bipartition `$X \cup Y$`, where `$X = \{x_1, \dots, x_n \}$`, `$Y = \{y_1, \dots, y_n \}$` and the edge `$\{x_i, y_j\}$` is in `$G_A$` precisely when `$A_{i,j} > 0$`.

We will show that such bipartite graph `$G_A$` has a perfect matching by the means of the Hall's theorem. Let `$S \subset X$` be any subset of vertices. They correspond to a subset of rows of the matrix `$A$`. The set `$N(S)$` is the set of columns that intersects the rows `$S$` on a positive entry. Alternatively, the columns `$N(S)$` covers all the nonzero entries of `$S$`.
By summing the entries on the columns `$N(S)$`, we get:

<div> $$ |N(S)| = \sum_{j \in N(S)}\sum_{i \in Y}a_{ij}  = \sum_{i \in Y}\sum_{j \in N(S)}a_{ij}  \geq \sum_{i \in S}\sum_{j \in N(S)}a_{ij} = |S| $$ </div>

In words, the columns `$N(S)$` holds all the weight of the rows `$S$`, as each column or row carries the same weight, there must be at least the same number of columns as rows.
