+++
date = "2018-03-06"
title = "Ramsey's Theorem for Graphs"
description = "A brief introduction - Part 1"
tags = [
"Graphs",
"Ramsey Theory"
]
+++

Ramsey theory is a vibrant branch of combinatorics that explores the unavoidability of ordered structures inside large enough combinatorial structures. This is a very vague description, so the purpose of this note is to make this claim precise in the language of graphs. As Ramsey theory and it's applications are one of my favourite themes in mathematics, this series of notes have also the purpose of being a reference in future notes to common notation, definitions and theorems. In fact, I even wrote my [undergraduate thesis](#references) in Ramsey theory! No previous knowledge of graph will be assumed.

Before we dive into the theory, let's make some standard notation clear. For `$n \in \mathbb{N}$`, define `$[n] = \{1,\dotsc,n\}$`. For any set `$A$` and `$k \in \mathbb{N}$`, define `${ A \choose k} = \{ S \subseteq A : |S| = k \}$`. Note that `$|{A \choose k}| = {|A| \choose k}$`. Sometimes we use `${A \choose \leq k} = \{ S \subseteq A : |S| \leq k\}$` and similar variants. The power set of `$A$` is denoted by `$\mathcal{P}(A) = \{ S : S \subset A\}$`.

In Ramsey theory, it is common to call partitions colourings. Let `$A$` be a set, we say that a colouring of `$A$` in `$r$` colours is any function `$c : A \to [r]$`. This induces a partition of `$A$` into the colour classes `$c^{-1}(1), \dotsc , c^{-1}(r)$`. It is common to have other finite sets as colours, for instance, a red-blue colouring of `$A$` is a colouring `$c : A \to \{R,B\}$`, and we can denote the colour classes by `$A_R = c^{-1}(R)$`, `$A_B = c^{-1}(B)$`.

# Graphs and Colourings

A __graph__ is a collection of vertices together with collection of pairs of vertices called edges. Formally a graph `$G$` is a pair `$G=(V,E)$` where `$V$` is a non-empty set and `$E \subseteq {V \choose 2}$`. If `$G$` is a graph, we denote `$V(G)$` for it's vertex set and `$E(G)$` for its edge set. This definition is the definition of a simple graph, and whenever the term graph is used, we mean a simple graph.

In a graph `$G$`, when an edge `$e = \{u,v\}\in E(G)$` for vertices `$u,v \in V(G)$` we say that `$e$` is __incident__ to `$u$` and `$v$`, and we say that `$u$` and `$v$` are __adjacent__. Given a vertex `$v$`, the __neighbourhood__ of `$v$`, denoted by `$N(v)$` is the set of vertices that are adjacent to `$v$`. The degree of a vertex `$v$`, denoted `$d(v)$`, is the size of the neighbourhood of `$v$`.

On Figure 1, we see the drawing of a graph. Each round dot represents a vertex, so we have 8 vertices. The edges are represented by curves with endpoints on it's vertices, so we have 10 edges. On this graph, we have one vertex of degree 1, four vertices of degree 2, two vertices of degree 3 and one vertex of degree 4.

{{< figure src="/img/graph_01.png" width="280px" alt="(Drawing of a simple graph)" caption="(Figure 1) Drawing of a simple graph.">}}

The useful information of a graph are the set of edges, they define structure between vertices. If we relabel all the vertices of a graph, and relabel the edges correspondingly, no information is lost. To capture this idea, we say that to graphs `$G$` and `$H$` are __isomorphic__ if there is a bijection `$\phi : V(G) \to V(H)$` such that `$\{\phi(u),\phi(v)\} \in E(H)$` if and only if `$\{u,v\} \in E(G)$`. Such function `$\phi$` is called an __isomorphism__ of graphs.

One important class of graphs are the __complete graphs__ `$K_n$`. The complete graph on a set of vertices `$V$` is the graph with all possible edges, that is, `$E = {V \choose 2}$`. Up to isomorphism, one can consider the complete graphs with `$n$` vertices to be the graph `$K_n = ([n], {[n] \choose  2})$`. On Figure 2, we have a graph isomorphic to `$K_5$`.

A __subgraph__ of a graph `$G$` is another graph `$H$` with `$V(H) \subseteq V(G)$` and `$E(H) \subseteq E(G)$`. We say that a graph `$G$` __has a copy of__ a graph `$H$` when `$G$` has a subgraph that is isomorphic to `$H$`. For instance, the graph `$K_5$` has a copy of `$K_3$`, indeed, it has `${5 \choose 3} = 10$` copies. When we say that a graph `$G$` has a graph `$H$`, we mean that `$G$` has a copy of `$H$`.

{{< figure src="/img/graph_02.png" width="200px" alt="(Drawing of a simple graph)" caption="(Figure 2) An edge colouring of $K_5$.">}}

An __edge colouring__  of `$G$` is a colouring `$c: E(G) \to [r]$`. Each colour class corresponds to a subgraph of `$G$`, namely `$G_i = (V(G), c^{-1}(i))$`, also called colour classes. We say that a colouring of `$G$` has a __monocromatic copy__ of `$H$` if one of the colour classes has a copy of `$H$`. The colouring given in Figure 2 does not have a monochromatic copy of a `$K_3$`, but has two monochromatic copies of the cycle on 5 vertices.

# Ramsey Theorem

We are now ready to do some basic Ramsey theory. Our main tool in proving our results will be the pigeonhole principle, which states that if we put objects into classes, and we have more objects than classes, then some class has more than one object. Formally, the pigeonhole principle is the statement that if `$f: [n] \to [r]$` is a function, and `$n > r$`, then there is some `$x \in n$` for which `$|f^{-1}(x)| > 1$.` One can improve that a little bit, as we always have an `$x \in [n]$` with `$|f^{-1}(x)| \geq \lceil \frac{n}{r} \rceil$`. In some sense, Ramsey theory is a sequence of generalizations of the pigeonhole principle.

The first result we will prove it's called Ramsey's theorem for graphs, even thought Ramsey did not prove it, he did an infinite version of this statement, which may appear in a future note. This theorem concerns about finding monochromatic copies of a given graph, and if we can find a monochromatic complete graph `$K_n$` in a colouring of `$G$`, we can also find a monochromatic copy of any graph `$H$` with at most `$n$` vertices. Therefore, we will only concern about complete graphs on this note.

> **Theorem (Ramsey)**
> For all `$t,r \in \mathbb{N}$` there is `$N$` such that any edge-colouring of `$K_N$` in `$r$` colours has a monochromatic copy of `$K_t$`.

If for a given `$t$` and `$r$`, `$N$` has the property of the conclusion of the theorem above, then `$N+1$` also have the same property. It is natural then to ask what is the smallest `$N$` with this property. So we the define the Ramsey number `$R_r(t)$` with `$r$` colours as:

<div> $$ R_r(t) = \min \{ N : \text{any } c:E(K_N) \to [r] \text{ has a monochromatic } K_t\}. $$</div>


So Ramsey's theorem can be stated as `$R_r(t) < \infty$`, for all `$r$` and `$t$`.

__Proof:__
Let `$G = K_N$` be a complete graph and we are given an arbitrary edge-colouring `$c : E(G) \to [r]$`. Let `$v_1$` be any vertex, and look at it's coloured neighbourhoods `$N_1(v_1), \dotsc, N_r(v_1)$`. As `$G$` is the complete graph, each other vertex of the graph is in one of these sets. If `$N \geq rN_2$`, by the pigeonhole principle, one of the neighbourhoods has at least `$N_2$` vertices, so let `$a_1 \in [r]$` be such `$|N_{a_1}(v_1)| \geq N_2$`. Let `$G_2$` be the graph subgraph of `$G$` induced by `$N_{a_1}$`, that is, `$G_2 = (N_{a_1}, {N_{a_1} \choose 2})$`, and restrict the colouring `$c$` to a colouring `$c_2$` on the edges of `$G_2$`. Now we repeat this argument on `$G_2$`.

Just for the sake of clarity, we will unroll the argument again. Let `$v_2 \in G_2$` be any vertex. Consider the coloured neighbourhoods `$N_1(v_2), \dotsc, N_r(v_2)$` in `$G_2$` and if `$N > rN_3$`, we pick a colour `$a_2$` where `$|N_{a_2}(v_2)| \geq N_3$`, and set `$G_3$` be the graph restricted to the vertices of `$N_{a_2}(v_2)$` and restrict the colouring to obtain `$c_3$`.

{{< figure src="/img/graph_03.png" width="400px" alt="(Drawing of a simple graph)" caption="(Figure 3) Process repeated after $K$ steps.">}}

After repeating this argument `$K$` times, we obtain a sequence of vertices `$v_1, \dotsc, v_K$`, and colours `$a_1, \dotsc, a_K$` with the property that if `$i < j$` then `$c({v_i, v_j}) = a_i$`, that is, the colour of an edge is determined by the vertex with smaller index, as can be seen from Figure 3. For that to apply, we assumed that `$N \geq Kr^K$`.

Finally, if `$K = r(t-1) + 1$`, then some colour `$b \in [r]$` will appear at least `$t$` times in the sequence `$a_1, \dotsc, a_K$`, let's say that `$a_{i_1} = \dotsc = a_{i_t} = i$`. Then the vertices `$v_{i_1}, \dotsc, v_{i_t}$` forms a monochromatic copy of `$K_t$`. Therefore, if `$N = Kr^K \geq rt r^{r(t-1) + 1} < tr^{rt}$`, then every `$r$`-edge-colouring of `$K_N$` has a monochromatic copy of a `$K_t$`. Therefore, `$R_r(t) < tr^{rt} < \infty$`.
<span class="qed">■</span>

__Remark 1:__ Before finishing this note, just a few remarks about this proof. Note that at each step, we potentially throw away a lot of the graph, keeping just a `$1/r$` proportion of the vertices. This may seem wasteful, but this is _essentially_ our best approach known for upper bounds of this kind. By essentially I mean that the more sophisticated ideas that leads to a better asymptotic bounds have the same constant under the exponential.

__Remark 2:__ We just showed an upper bound for the numbers `$R_r(t)$`, so the natural question for the lower bounds raises naturally. That requires a radically different approach, and may be the topic of a future note.

__Remark 3:__ We did prove a generic statement that holds for any `$r$` and `$t$`. If one of `$r =1$` or `$t \leq 2$`, the definition of `$R_r(t)$` trivializes. The only other pairs of numbers that are known exactly are `$R_2(3) = 6$`, `$R_2(4) = 18$` and `$R_3(3) = 17$`.

This theorem exemplifies the philosophy behind Ramsey theory. No matter how disordered a colouring can be, one can find a small portion of the colouring that is highly organized. On the next note in this series, we will explore an application of this result in number theory.

# References
<a name="references"></a>
[1] Souza, Campos - [Introdução à Teoria de Ramsey em Grafos](http://www.ic.unicamp.br/~reltech/PFG/2016/PFG-16-22.pdf) (Portuguese) [Introduction to Ramsey Theory on Graphs]. 2016, Undergraduate Thesis, Insitute of Computing, University of Campinas, 2016.
