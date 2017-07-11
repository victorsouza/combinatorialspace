+++
date = "2017-06-07T11:29:36-04:00"
title = "Studying the Harmonic Numbers"
+++

The first series shown to diverge in most analysis courses is the Harmonic Series. Even with tons of different proofs and reiterations, their properties never get depleted. Remembering the basics, let:  `$\mathcal{H}_n = \frac{1}{1} + \frac{1}{2} + \frac{1}{3} + \dots + \frac{1}{n} = \sum_{k=1}^{n}\frac{1}{k} $`

We'll see that:

<div> $$ \lim_{n \rightarrow \infty} \mathcal{H}_n = \infty  + 1$$ </div>

And the first known proof of this is attributed to the medieval mathematician Nicole Oresme, grouping terms, here I present it a little differently for the sake of variety, but the central argument is the same:

<div> $$ \sum_{k=0}^{n-1} \left (\mathcal{H}_{2^{k+1}} - \mathcal{H}_{2^k}   \right )= \mathcal{H}_{2^n} - \mathcal{H}_{1} $$ </div>
<div> $$ \mathcal{H}_{2^n} = 1 + \sum_{k=0}^{n-1} \left (  \frac{1}{2^k + 1} + \frac{1}{2^k + 2} + \dots + \frac{1}{2^k + 2^k}\right ) $$ </div>
<div> $$ \mathcal{H}_{2^n} \geq 1 + \sum_{k=0}^{n-1} \left (  \frac{1}{2}\right ) = 1 + \frac{n}{2}$$ </div>
<div> $$ \Rightarrow \lim_{n \rightarrow \infty} \mathcal{H}_n = \infty $$ </div>

The harmonic series is also classically presented as an counterexample, showing that `$\lim_{n \rightarrow \infty} a_n = 0$` does't imply convergence of `$\sum a_n$`. Unfortunately, most real analysis texts stop here when concerning harmonic series, but there is much more to explore.

# Integral Formula

Euler found an alternative formula for `$\mathcal{H}_n$` using an integral:

<div> $$ \mathcal{H}_n = \int_{0}^{1}\frac{1-x^n}{1-x}dx $$ </div>

One can use the following algebraic identity

<div> $$ 1 - x^n = (1 - x)(1 + x + \dots + x^{n-1}) $$ </div>

And develop the integral to obtain

<div> $$ \int_{0}^{1}\frac{1-x^n}{1-x}dx = \int_{0}^{1} \left (\sum_{k=0}^{n-1} x^k  \right ) dx = \sum_{k=0}^{n-1}\left ( \int_{0}^{1} x^k dx \right ) = $$ </div>
<div> $$ = \sum_{k=0}^{n-1} \left [ \frac{x^{k+1}}{k+1} \right ]_0^1 = \sum_{k=0}^{n-1} \frac{1}{k+1} = \sum_{k=1}^{n} \frac{1}{k} = \mathcal{H}_n $$ </div>

In fact, we can generalize this identity a bit. The difference of two harmonics, that is, the harmonics starting off an `$m$` all the way through $n$ can be written as an integral of the same form.

<div> $$ \mathcal{H}_n - \mathcal{H}_m = \int_{0}^{1}\frac{1-x^n}{1-x}dx - \int_{0}^{1}\frac{1-x^m}{1-x}dx $$ </div>
<div> $$ \mathcal{H}_n - \mathcal{H}_m = \int_{0}^{1}\left ( \frac{1-x^n}{1-x} - \frac{1-x^m}{1-x} \right ) dx $$ </div>
<div> $$ \mathcal{H}_n - \mathcal{H}_m = \int_{0}^{1}\frac{x^m-x^n}{1-x}dx $$ </div>

Where the first in the first formulation we had `$m = 0$`.

# Euler-Mascheroni Constant

One can get better estimates for the value of `$\mathcal{H}_n$` by the integral inequalities, valid for non-increasing `$f$`:

$$ \int_{1}^{n+1} f(x)dx \leq \sum_{k=1}^{n} f(k) \leq f(1) + \int_{1}^{n} f(x)dx \leq \int_{0}^{n}f(x)dx $$

The reason to split the $f(1)$ from the integral on the right is because in this case, the integral won't converge, so this way, we still got an finite bound for $f(x) = \frac{1}{x}$.

$$ \int_{1}^{n+1} \frac{1}{x}dx \leq \sum_{k=1}^{n} \frac{1}{k} \leq f(1) + \int_{1}^{n} \frac{1}{x}dx $$
$$ \ln(n+1) \leq \mathcal{H}_n \leq 1 + \ln(n) $$

So now we have a better idea of how big $\mathcal{H}_n$ should be and how slowly it diverges, but more interesting, we can now write:

$$ 0 \leq \ln(n+1) - \ln(n) \leq \mathcal{H}_n - \ln(n) \leq 1 $$
$$ 0 \leq \mathcal{H}_n - \ln(n) \leq 1 $$

We now know that $\mathcal{H}_n - \ln(n)$ is bounded. If we show that it is increasing, we may prove it's convergence. In fact

$$ \left (\mathcal{H}_{n+1} - \ln(n+1)   \right ) - \left (\mathcal{H}_n - \ln(n)   \right )= \frac{1}{n+1} + \ln\left ( 1 - \frac{1}{n+1} \right ) \leq 0 $$

Because $x + \ln(1-x) \leq 0$. Then $\mathcal{H}_n - \ln(n)$ is monotonic and bounded, therefore, convergent. We call it's value Euler-Mascheroni constant

$$\gamma = \lim_{n \rightarrow \infty}\left (\mathcal{H}_n - \ln(n)  \right ) = \int_{1}^{\infty}\left ( \frac{1}{\left \lfloor x \right \rfloor} - \frac{1}{x}\right )dx =  0.57721\dots $$

The integral formulation makes clear that it is the area between these two curves. Until now, it is not known whether $\gamma$ is irrational or rational.

# General Harmonic Series

What is sometimes called general Harmonic Series has this form, for $a,b \in \mathbb{Z}^+$:

$$ \sum_{k=1}^{\infty} \frac{1}{ak + b} $$

And it diverges by comparison with the common harmonic series, in fact:

$$ \sum_{k=1}^{n} \frac{1}{ak + b} \geq \sum_{k=1}^{n} \frac{1}{ak + ab} = \frac{1}{a} \sum_{k=1}^{n} \frac{1}{k + b} = \frac{\mathcal{H}_n - \mathcal{H}_b}{a} $$
$$ \lim_{n \rightarrow \infty} \sum_{k=1}^{n} \frac{1}{ak + b} \geq \lim_{n \rightarrow \infty} \frac{\mathcal{H}_n - \mathcal{H}_b}{a} = \infty$$

The same reasoning works with $a,b \in \mathbb{R}^+$. Now, allow me a little digression on the Leibniz criterion.

# Leibniz Criterion

We are going to prove an theorem on alternating series that will guide further analysis on the harmonics. The theorem states:

> **`(Theorem 2.1)`**
> Let `$(a_n)$` be a non-crescent real sequence such `$\lim a_n = 0$`. Then the alternate series as follows converges:
<div> $$ \sum_{k=1}^{\infty}(-1)^k a_n $$ </div>

To prove this theorem, let $S_n$ be the partial sums of the series, that is $S_n = \sum_{k=1}^{n}(-1)^k a_n$. Then we have, from monotonicity:

$$ S_{2n+1} = S_{2n-1} + a_{2n} - a_{2n+1} \leq S_{2n-1}$$
$$ S_{2n+2} = S_{2n} - a_{2n+1} + a_{2n} \geq S_{2n} $$

That is, the odd partial sums are non-increasing and the even are non-decreasing. Moreover, the odd sums are bounded bellow by the evens, and the evens are bounded bellow by the odds. Symbolically, we have:

$$ S_2 \leq S_4 \leq \dots \leq S_{2n} \leq \dots \leq S_{2n+1} \leq \dots \leq S_{3} \leq S_{1} $$

Both sequences are monotonic and bounded, and therefore exists $\alpha = \lim_{n \rightarrow \infty} S_{2n}$ and $\beta = \lim_{n \rightarrow \infty} S_{2n+1}$. But we know that:

$$ S_{2n} - S_{2n-1} = a_{2n} \Rightarrow \lim_{n \rightarrow \infty}(S_{2n} - S_{2n-1}) = \lim_{n \rightarrow \infty}a_n = 0 $$
$$ \alpha = \beta \Rightarrow \sum_{k=1}^{\infty}(-1)^k a_n \text{ converges }$$

With the proof completed, we notice that this criterion holds for the harmonic series, that is, the terms are decrescent and tend to zero. From the Leibniz test, we now conclude the convergence of

$$ \lim_{n \rightarrow \infty} \mathcal{A}_n = \sum_{k=1}^{\infty} \frac{(-1)^{k+1}}{k} = 1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \dots $$

But converges to what? Permit me another shorter digression to elaborate how this could be achieved.

<h3> Botez-Catalan Identity </h3>

This identity relates alternating harmonics with the positive harmonics, stating:

$$ 1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \dots + \frac{1}{2n-1} - \frac{1}{2n} = \frac{1}{n+1} + \frac{1}{n+2} + \dots + \frac{1}{2n} $$

To prove it, some notation first. Let $\underset{\text{odd}}{\mathcal{H}_{2n}}$ be the harmonic numbers counting the only the odds and $\underset{\text{even}}{\mathcal{H}_{2n}}$ only the evens. Then we got

$$ \mathcal{A}_{2n} = \underset{\text{odd}}{\mathcal{H}_{2n}} - \underset{\text{even}}{\mathcal{H}_{2n}} = $$
$$ = \underset{\text{odd}}{\mathcal{H}_{2n}} + \left (\underset{\text{even}}{\mathcal{H}_{2n}} - \underset{\text{even}}{\mathcal{H}_{2n}}  \right ) - \underset{\text{even}}{\mathcal{H}_{2n}} = $$
$$ = \mathcal{H}_{2n} - 2\underset{\text{even}}{\mathcal{H}_{2n}} = \mathcal{H}_{2n} - \mathcal{H}_{n}  $$

This fact is interesting by itself, but we can use it to find the limit of the alternating harmonics.

<h3> Alternating Harmonics </h3>

We've seen before that the alternating harmonics converge, let's apply the Botez-Catalan identity to find out it's value. We have

$$ \mathcal{A}_{2n} = \mathcal{H}_{2n} - \mathcal{H}_{n}$$
$$ \mathcal{A}_{2n} - \ln(2n) + \ln(n) = \mathcal{H}_{2n} - \mathcal{H}_{n} - \ln(2n) + \ln(n) $$
$$ \mathcal{A}_{2n} - \ln(2) = \left (\mathcal{H}_{2n} - \ln(2n)   \right ) - \left (\mathcal{H}_{n} - \ln(n)  \right ) $$
$$ \lim_{n \rightarrow \infty} \left (\mathcal{A}_{2n} - \ln(2) \right ) = \lim_{n \rightarrow \infty} \left (\mathcal{H}_{2n} - \ln(2n)   \right ) - \lim_{n \rightarrow \infty} \left (\mathcal{H}_{n} - \ln(n)  \right ) = \gamma - \gamma = 0$$
$$ \lim_{n \rightarrow \infty} \mathcal{A}_n = \ln(2)$$

A rather cool proof, not involving Taylor series as most of them, but if you happens to know the Taylor expansion for $\ln (1+x)$, also known as Mercator Series, as follows:

$$ \ln (1 + x) = \sum_{k=1}^{\infty} \frac{(-1)^{k+1}}{k}x^n \text{ for } -1 < x \leq 1 $$

For $x = 1$, we have

$$ \lim_{n \rightarrow \infty} \mathcal{A}_n = \sum_{k=1}^{\infty} \frac{(-1)^{k+1}}{k} = \ln(2) $$

<h3> Reciprocal of Primes </h3>

Prime numbers are interesting in many ways, so mathematicians will try to relate them with every mathematical work that its done and harmonic series is not an exception. The obvious question to ask is the convergence of

$$ \sum_{p \text{ prime}} \frac{1}{p} $$

The all-present Euler proved this using what is now called Euler Products

$$ \sum_{n \in \mathbb{N}} n^{-s} = \prod_{p \text{ prime}} \left ( \frac{1}{1 - p^{-s}}\right )$$

To see why this is true (this is not a formal proof), we start with the prime factorization of $n$

$$ n = \prod_{p \text{ prime}} p^{\nu_p(n)} $$
$$ n^{-s} = \prod_{p \text{ prime}} p^{-s \nu_p(n)} $$

Then we sum all natural numbers

$$ \sum_{n \in \mathbb{N}} n^{-s} = \sum_{n \in \mathbb{N}} \prod_{p \text{ prime}} p^{-s \nu_p(n)}  $$

And factor out the sum as

$$ \sum_{n \in \mathbb{N}} n^{-s} = \left ( 1 + 2^{-s} + 2^{-2s} + \dots \right )\left ( 1 + 3^{-s} + 3^{-2s} + \dots \right )\left ( 1 + 5^{-s} + 5^{-2s} + \dots \right )\dotsm $$
$$ \sum_{n \in \mathbb{N}} n^{-s} = \prod_{p \text{ prime}} \left ( \sum_{n = 0}^{\infty} p^{-ns}\right ) $$

To understand this identity, notice that by choosing factors of the product, we are choosing the exponents of the prime factorization. In this way, we are producing every natural number once and only once, so it must be equal to the sum over all naturals. But the sum on the righthand-side is a geometric series, so we get

$$ \sum_{n \in \mathbb{N}} n^{-s} = \prod_{p \text{ prime}} \left ( \frac{1}{1-p^{-s}} \right ) $$

Now we are able to prove the divergence of reciprocal of primes. The Euler Product for $s = 1$  gives us

$$ \sum_{n = 1}^{\infty} \frac{1}{n} = \prod_{p \text{ prime}} \left ( \frac{1}{1-p^{-1}} \right ) $$
$$ \ln \left ( \sum_{n = 1}^{\infty} \frac{1}{n} \right ) = \ln \left (\prod_{p \text{ prime}} \left ( \frac{1}{1-p^{-1}} \right ) \right ) = \sum_{p \text{ prime}}\ln \left ( \frac{1}{1-p^{-1}} \right ) = $$
$$ \ln \left ( \sum_{n = 1}^{\infty} \frac{1}{n} \right ) = \sum_{p \text{ prime}}\ln \left ( \frac{p}{p-1} \right )  = \sum_{p \text{ prime}}\ln \left ( 1 + \frac{1}{p-1} \right ) $$

But $\ln(1 + x) < x$, therefore

$$ \ln \left ( \sum_{n = 1}^{\infty} \frac{1}{n} \right ) \leq \sum_{p \text{ prime}}\frac{1}{p-1} $$

diverges by comparison. But that's not quite what was stated, we need to get rid of that minus one on the denominator. Let $p_n$ be the n-th prime number, we know that

$$ p_{n+1} \geq p_n + 1 \Rightarrow p_{n+1} - 1 \geq p_n \Rightarrow \frac{1}{p_n} \geq \frac{1}{p_{n+1} - 1}$$

Thus

$$ \sum_{n=1}^{\infty} \frac{1}{p_n - 1} = 1 + \sum_{n=1}^{\infty} \frac{1}{p_{n+1} - 1} \leq 1 + \sum_{n=1}^{\infty} \frac{1}{p_n}$$

Therefore, the reciprocal of primes diverge.

<h3> Conclusions </h3>

Harmonic Series severs as an interesting intersection point of real analysis and number theory. Sometimes, taking one particular object and studying it in exhaustion can be very fruitful.
We've seen the divergence of the harmonics, an integral formula, the Euler-Mascheroni constant, the alternating harmonic series and the divergence of reciprocal of primes. Even though may seem much, this is just the tip of the iceberg. Many more can and will be explored in future topics!

<h3> References </h3>
[1]<a href="http://scipp.ucsc.edu/~haber/archives/physics116A10/harmapa.pdf" title="The Harmonic Series Diverges Again and Again">The Harmonic Series Diverges Again and Again</a>
[2]<a href="http://www.macalester.edu/~bressoud/talks/mathfest2007/harmonicproblems.pdf" title="The Harmonic Divergence">The Harmonic Divergence</a>
[3]<a href="http://www.maths.tcd.ie/pub/Maths/Courseware/PrimeNumbers/Primes-II.pdf" title="Euler’s Product Formula">Euler’s Product Formula</a>
