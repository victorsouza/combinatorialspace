+++
date = "2018-03-31"
title = "Bonferroni Inequalities"
description = "via integration and unimodal sequences"
tags = [
"Measure",
"Combinatorics",
"Unimodal"
]
+++

The __principle of inclusion-exclusion__ is a fundamental tool in combinatorics. It relates the cardinality of a union of sets to the cardinality of the intersection of these sets. We will use the following notation: denote `$[n] = \{1, \dots, n\}$` and for a set `$A$`, define `${ A \choose k} = \{ S \subseteq A : |S| = k \}$`. The inclusion-exclusion principle can be stated in a compact way as follows, for finite sets `$A_1, \dotsc, A_n$`:

<div> $$ \begin{align}
\left | \bigcup_{i\in [n]} A_i  \right| &= \sum_{\emptyset \neq I \subset [n]} (-1)^{|I|+1} \left | \bigcap_{i \in I} A_i\right | \\
&= \sum_{k=1}^n (-1)^{k+1} \sum_{I \in {[n] \choose k}} \left | \bigcap_{i \in I} A_i\right | .
\end{align}$$</div>

We gave two different expressions for this formula. The first one is more compact, but the second one is often more useful, as we separate the terms by the number of sets in the intersection. Indeed another common way to write such identity is by expanding the notation:

<div> $$ \begin{align}
\left | \bigcup_{i\in [n]} A_i  \right| &= \sum_{1 \leq i \leq n} |A_i| - \sum_{1 \leq i < j \leq n } | A_i \cap A_j| \\
&+ \sum_{1 \leq i < j < k \leq n} |A_i \cap A_j \cap A_k| \\
&+ \dotsc + (-1)^{n-1} \left| \bigcap_{i \in [n]} A_i \right |.
\end{align} $$</div>

Grouping the terms in this way, one can see the terms as successive approximations of the cardinality of the union of the `$A_i$`. If we stop at the first term, it is easy to see that we overestimate the size of the union, that is, `$|\bigcup_{i \in [n]}A_i | \leq \sum_{i \in [n]} |A_i|$`. If we add the second term as a correction, then we underestimate the size. If then we add the third term, we overestimate it again. Indeed, this behaviour is captured in general by the __Bonferroni's inequalities__, that states that for `$N$` even we have

<div>$$ \displaystyle \left | \bigcup_{i\in [n]} A_i  \right| \geq \sum_{k=1}^N (-1)^{k+1} \sum_{I \in {[n] \choose k}} \left | \bigcap_{i \in I} A_i \right | $$</div>

and  for `$N$` odd we have

<div> $$ \displaystyle \left | \bigcup_{i\in [n]} A_i  \right| \leq \sum_{k=1}^N (-1)^{k+1} \sum_{I \in {[n] \choose k}} \left | \bigcap_{i \in I} A_i \right |. $$</div>

The canonical way to prove all these propositions is by induction on `$n$`. We will not prove it here, so consider it an exercise if you haven't done it at least once.

The goal of this note is to prove a measure theoretical version of this identity via integration and properties of unimodal sequences.

# Inclusion-Exclusion via Integration

Let `$(\Omega, \mathcal{A}, \mu)$` be a measure space and `$A_1, \dots, A_n \in \mathcal{A}$` be measurable sets with finite `$\mu$`-measure. Denote `$A = \bigcup_{i \in [n]} A_i$`. As `$A$` is measurable, it's indicator function `$\unicode{x1D7D9}_A$` is a measurable function. Define the function `$F$` as

<div> $$
F(\omega) = \prod_{i \in [n]} (\unicode{x1D7D9}_A(\omega) - \unicode{x1D7D9}_{A_i}(\omega)).
$$ </div>

Note that if `$\omega \not\in A$`, then `$\unicode{x1D7D9}_A(\omega) = 0$` and `$\unicode{x1D7D9}_{A_i}(\omega) = 0$` for `$i \in [n]$`, so `$F(\omega) = 0$`.
On the other hand, if `$\omega \in A$`, then there is `$i$` so that `$\omega \in A_i$`, so `$\unicode{x1D7D9}_A(\omega) - \unicode{x1D7D9}_{A_i}(\omega) = 0$`, this also implies that `$F(\omega) = 0$`, that is, `$F$` is identically 0. Expanding the product, we have:

<div> $$
0 = \prod_{i \in [n]} (\unicode{x1D7D9}_A - \unicode{x1D7D9}_{A_i}) = \unicode{x1D7D9}_A + \sum_{\emptyset \neq I \in [n]}(-1)^{|I|} \prod_{i \in I}\unicode{x1D7D9}_{A_i} .
$$ </div>

Therefore

<div> $$
\unicode{x1D7D9}_A = \sum_{\emptyset \neq I \in [n]}(-1)^{|I|+1} \unicode{x1D7D9}_{\cap_{i \in I}A_i} .
$$ </div>

Integrating both sides, we have

<div> $$ \begin{align}
\int \unicode{x1D7D9}_A d\mu &=  \int \sum_{\emptyset \neq I \in [n]}(-1)^{|I|+1} \unicode{x1D7D9}_{\cap_{i \in I}A_i} d\mu \\
&= \sum_{\emptyset \neq I \in [n]}(-1)^{|I|+1} \int \unicode{x1D7D9}_{\cap_{i \in I}A_i} d\mu
\end{align}$$ </div>
<div> $$ \begin{align}
\mu\left( \bigcup_{i \in [n]}A_i \right) &= \sum_{\emptyset \neq I \in [n]}(-1)^{|I|+1} \mu \left( \bigcap_{i \in I}A_i \right).
\end{align}$$ </div>

This is the principle of inclusion exclusion for measures. Note that we had to assume that `$\mu(A_i) < \infty$`, for all `$i \in [n]$`. If we have the counting measure, this corresponds exactly to the first identity on this note. We will prove the Bonferroni's inequalities using a similar approach, but we need a little detour.

# Unimodal Sequences

A sequence of real numbers `$\{a_i\}_{i \geq 0}$` is called unimodal if there is an index `$m$` such that `$a_0 \leq a_1 \leq \dotsc \leq a_m$` and `$a_m \geq a_{m+1} \geq \dotsc$`. That is, a sequence is unimodal if it is monotonic nondecreasing until some point, and after that, it is monotonic nonincreasing.

> **Lemma:**
> If `${a_i}$` is a nonnegative unimodal sequence such that `$\sum_{i=0}^n (-1)^{i}a_i = 0$`, then for every `$k \leq n$`, we have `$(-1)^k\sum_{i=0}^k (-1)^{i}a_i \geq 0$`.

__Proof:__
First, let's prove that this property holds for monotone sequences. Suppose that `$\{a_i\}_{i \geq 0}$` is monotone nondecreasing. Thus we have

<div> $$ \begin{align}
\sum_{i=0}^{2k+1} (-1)^{i}a_i &= \sum_{i=0}^{k} (a_{2i} - a_{2i+1}) \leq 0, \\
\sum_{i=0}^{2k} (-1)^{i}a_i &= a_0 + \sum_{i=1}^{k} (a_{2i} - a_{2i-1}) \geq 0.
\end{align} $$ </div>

Therefore, the result holds for nondecreasing sequences. Now, if a sequence `$\{a_i\}_{i \geq 0}$` is unimodal with turning point `$m$`, we know that the lemma holds for all `$k \leq m$`. For `$k > m$` we use the fact that `$\sum_{i=0}^n (-1)^{i}a_i = 0$` to get

<div> $$ \begin{align}
\sum_{i=0}^{k} (-1)^{i}a_i &= \sum_{i=0}^{k} (-1)^{i}a_i - \sum_{i=0}^n (-1)^{i}a_i\\
&= - \sum_{i=k+1}^{n} (-1)^{i}a_i \\
&= - \sum_{i=0}^{n-k-1} (-1)^{n-i}a_{n-i}.
\end{align} $$ </div>

But the sequence `$\{a_{n-i}\}_{i \geq 0}$` is then unimodal with turning point `$n - m$`. Therefore, the index `$n-k-1\leq n - m$`, so the sequence is monotone nondecreasing up to that index. This gives us

<div> $$
(-1)^k\sum_{i=0}^{k} (-1)^{i}a_i = -(-1)^{k}\sum_{i=0}^{n-k-1} (-1)^{n-i}a_{n-i} \\
= (-1)^{n-k-1}\sum_{i=0}^{n-k-1} (-1)^{i}a_{n-i} \geq 0.
$$ </div>

The lemma is then proved. <span class="qed">■</span>

One natural sequence that we can use with this lemma is the sequence defined by binomial numbers, that is `$a_i = { n \choose i}$`. The fact that the alternating sum is zero is a consequence of the __binomial theorem__, as we have `$\sum_{i=0}^n {n \choose i}(-1)^i = (1-1)^n = 0$`.

# Bonferroni via Integration

Let again `$(\Omega, \mathcal{A}, \mu)$` be a measure space and `$A_1, \dots, A_n \in \mathcal{A}$` be measurable sets with finite `$\mu$`-measure. Denote `$A = \bigcup_{i \in [n]} A_i$`. Define the function `$L : \Omega \to \mathcal{P}([n])$` as the set of indices `$i$` such that `$\omega \in A_i$`. Formally, set

<div> $$L(\omega) = \{ i \in [n] : \omega \in A_i \}. $$ </div>

Now, note that

<div> $$
\sum_{I \in {[n] \choose k}} \unicode{x1D7D9}_{\cap_{i \in I} A_i}(\omega) = { |L(\omega)| \choose k}.
$$ </div>

Now, consider the following function `$F_N$`.

<div> $$ \begin{align}
F_N(\omega) &=  \unicode{x1D7D9}_{A}(\omega) +
\sum_{k = 1}^{N}(-1)^k\sum_{I \in {[n] \choose k}} \unicode{x1D7D9}_{\cap_{i \in I} A_i}(\omega)\\
&= \unicode{x1D7D9}_{A}(\omega) +
\sum_{k=1}^{N}(-1)^j{ |L(\omega)| \choose k}.
\end{align} $$ </div>

Integrating `$F_N$` over `$A$`, we obtain:

<div> $$ \begin{align}
\int_A F_N d\mu &=  \int_A \unicode{x1D7D9}_{A} d\mu +
\int_A \sum_{k=1}^{N}(-1)^k{ |L(\omega)| \choose k} d\mu \\
&=  \int_A \sum_{k=0}^{N} (-1)^k{ |L(\omega)| \choose k} d\mu.
\end{align} $$ </div>

For every `$\omega \in \Omega$`, the sequence `${ |L(\omega)| \choose k}$` is unimodal and has the alternating zero sum property, as discussed before. Therefore, we have

<div> $$ (-1)^N \int_A F_N d\mu \geq 0.  $$ </div>

This can be rewritten as, for `$N$` even, we have

<div>$$\mu\left( \bigcup_{i \in [n]}A_i \right) \geq \sum_{k=1}^{N} (-1)^{k+1} \sum_{I \in {[n] \choose k}} \mu \left( \bigcap_{i \in I} A_i \right) , $$</div>

and for `$N$` odd we have

<div>$$\mu\left( \bigcup_{i \in [n]}A_i \right) \leq \sum_{k=1}^{N} (-1)^{k+1} \sum_{I \in {[n] \choose k}} \mu \left( \bigcap_{i \in I} A_i \right). $$</div>

These are the Bonferroni inequalities on the measure setting.

# Conclusion

We have show both the principle of Inclusion-Exclusion and the Bonferroni inequalities via integration of the adequate measurable function over a measure space, and also exploiting some properties of unimodal sequences. Again, one can prove such identities by induction, but knowing different proofs for a proposition is always useful to find connections and parallels with different areas. These proofs sheds light into connection of this set of inequalities and properties of the binomial numbers. It will be nice to discover other nice applications of the Lemma we've proved about unimodal sequences in different problems.
