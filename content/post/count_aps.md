+++
date = "2017-08-02"
title = "Counting Arithmetic Progressions"
draft = true
+++

Let's count the number of $k$-term arithmetic progressions contained inside the
interval `$[N]$`. Let `$A_k(N)$` denote such quantity. Intuitively, we expect roughly `$N^2$` such progressions, as we have order of `$N$` choices for the first term and order `$N$` choices for the common difference.  

# Estimating

An arithmetic progression of length `$k$` inside `$[N]$` cannot have the first
term bigger than `$N - k + 1$`. An progression `$\{an + b : 0 \leq n < k\} \subset [N]$` has last term `$a(k-1) + b \leq N$`, therefore the common  difference is bounded above by `$\frac{N-b}{k-1} \leq \frac{N-1}{k-1}$`. Thus, we get the upper bound:

$$ A_k(N) \leq  \frac{(N-k+1)(N-1)}{k-1} \leq \frac{N^2}{k-1} $$

For a lower bound, we must show that we have many progressions contained in
that interval. Indeed, if the first term is inside the interval `$[x]$`, then,
the common difference can by any positive integer less than `$\frac{N-x}{k-1}$`.
Thus, we get

$$ A_k(N) \geq \frac{x(N-x)}{k-1} = \frac{N^2}{4(k-1)}, $$

by choosing `$x = N/2$`. Therefore, we see that we really have order of `$N^2$` arithmetic progressions of constant length.

# Refining

To be more precise, we observe that we have `$\left \lfloor \frac{N-a}{k-1} \right \rfloor$` arithmetic progressions of length `$k$` with first term `$a \in [N]$`. Therefore

<div> $$ A_k(N) = \sum_{a = 1}^{N} \left \lfloor \frac{N-a}{k-1} \right \rfloor
=  \sum_{a = 0}^{N-1} \left \lfloor \frac{a}{k-1} \right \rfloor $$ </div>

By using that `$x - 1 \leq \lfloor x \rfloor \leq x$`, and that,

<div> $$ \sum_{a = 0}^{N-1} \frac{a}{k-1}  = \frac{N(N-1)}{2(k-1)} = \frac{N^2}{2(k-1)} - \frac{N}{2(k-1)} $$ </div>

we have that:
<div> $$ \frac{1}{2(k-1)}N^2 - \left (1+\frac{1}{2(k-1)} \right)N \leq A_k(N) \leq \frac{1}{2(k-1)}N^2 - \frac{1}{2(k-1)}N $$ </div>

Which gives `$A_k(N) \sim \frac{N^2}{2(k-1)}$` .

# Typical Progressions

Let `$\mathcal{A}_k(N)$` be the set of all `$k$`-term arithmetic progressions inside the set `$[N]$`. What can we say about a typical element of `$\mathcal{A}_k(N)$`?

Lets carry out the expected common difference:

<div> $$  \sum_{a = 0}^{N-1} $$ </div>
