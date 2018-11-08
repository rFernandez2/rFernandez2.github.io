---
layout:     post
title:      Schwartz-Zippel Lemma
date:       2018-10-25 09:00:21
categories: math
---

For the following theorems and examples we let $\mathbb{F}$ be a field
and $\mathcal{P}[x_1,\ldots,x_n]$ be a formal polynomial over
$\mathbb{F}$. Note that in our definition of formal polynomials we
consider a polynomial as being uniquely defined by its coefficients.

## Schwartz-Zippel Lemma


The Schwartz-Zippel lemma [@Schwartz; @Zippel] provides us with
sufficient conditions under which we can bound the probability that a
specific evaluation of a polynomial vanishes, and thus allows us to make
statements about whether a polynomial is identically zero.

Let $\mathcal{P}\in \mathbb{F}[x_1,\ldots,x_n]$ be a non-zero polynomial
with deg$(\mathcal{P})=d\geq 0$. We then consider a finite subset
$S\subseteq \mathbb{F}$. If we randomly and independently sample
$r_1,\ldots,r_n$ from $S$ then
$$\mathbb{P}[\mathcal{P}(r_1,\ldots,r_n)=0]\leq \frac{d}{|S|}.$$

We prove this by induction on $n$. The base case is immediate since
$n=1$ gives us a univariate polynomial, for which we know
deg$(\mathcal{P})=d$ implies at most $d$ roots. Now we assume it holds
for all polynomials with degree $n-1$. Given that
$\mathcal{P}\not\equiv 0$ we can, without loss of generality, assume
that $x_1$ occurs in some nonzero monomial. We can then consider each
monomial and factor out this $x_1$ component so that we can write
$\mathcal{P}$ as a polynomial in $x_1$:
$$\mathcal{P}(x_1,\ldots,x_n)=\sum_{i=1}^d x_1^i Q_i(x_2,\ldots,x_n).$$
By our assumption that $x_1$ occurs in a nonzero monomial we know that,
for some $i$, we have $Q_i\not\equiv 0$, let $k$ denote such monomial
with the highest degree. We know that
deg$(x_1^kQ_k(x_2,\ldots,x_n))\leq d$ and thus deg$(Q_k)\leq d-k$.

Now let $A$ denote the event that $Q_k(y_2,\ldots,y_n)=0$, where
$y_2,\ldots,y_n$ is randomly sampled from $S^{n-1}$. It follows by our
inductive hypothesis that $\mathbb{P}[A]\leq \frac{d-k}{|S|}$. If we
then have such $\overline{y}\triangleq y_2,\ldots,y_n$ with
$Q_k(\overline{y}) \not\equiv 0$ then it follows that
$\mathcal{P}(x_1, y_2,\ldots,y_n)$ is univariate in $x_1$, nonzero, and
of degree $k$. If we then condition this polynomial on $\overline{y}$ we
can use the base case and get that
$\mathbb{P}[\mathcal{P}(x_1,y_2,\ldots,y_n)=0\mid (y_2,\ldots,y_n)]\leq \frac{k}{|S|}.$
Ultimately, we can write:
$$\mathbb{P}[\mathcal{P}\equiv0]\geq (1-\mathbb{P}(A))\left(1-\frac{k}{|S|}\right)=\left(1-\frac{d-k}{|S|}\right)\left(1-\frac{k}{|S|}\right)\geq 1-\frac{d-k}{|S|}-\frac{k}{|S|}=1-\frac{d}{|S|}.$$
It then clearly follows that
$\mathbb{P}[\mathcal{P}\neq 0]=1-\left(1-\frac{d}{|S|}\right)=\frac{d}{|S|}$,
just as desired.

The above theorem thus tells us that, if applicable, we can find a
$\overline{x}\in S^n$ such that $\mathcal{P}(\overline{X})\neq 0$ with
high probability after $\mathcal{O}\left(\frac{|S|}{d}\right)$ trials.

We now consider our first application of the Schwartz-Zippel Lemma,
Polynomial Identity Testing (PIT):

Let our input be an arithmetic circuit representing a formal polynomial
over variables $x_1,\ldots,x_n$ in a field $\mathbb{F}$. We are then
interested on whether $\mathcal{P}\equiv 0$. This can be used to test
the equivalence of two polynomials $\mathcal{P}_1, \mathcal{P}_2$ over
this same field since we can simply write
$\mathcal{Q}=\mathcal{P}_2-\mathcal{P}_2$ and test whether
$\mathcal{Q}\equiv 0$.

Given our above result we can provide an algorithm which shows that PIT
$\in$ co-RP, at least in cases where our polynomial has bounded degree.
If we have $\mathcal{P}(x_1,\ldots,x_n)$ over our field $\mathbb{F}$
such that deg$(\mathcal{P})\leq |\mathbb{F}|$ we can use the following
algorithm.

1.  Randomly and uniformly sample
    $\overline{y}\triangleq y_1,\ldots,y_n$ from $\mathbb{F}^n$.

2.  If $\mathcal{P}(\overline{y})\neq 0$ then conclude $\mathcal{P}$ is
    not identically $0$ and conclude execution.

3.  If $\mathcal{P}(\overline{y})=0$ return that $\mathcal{P}$ is
    identically zero with a probability error of at most
    $\frac{d}{|\mathbb{F}|}<1$, due to Schwartz-Zippel. We can thus
    repeat this procedure until this error has reached an appropriate
    bound.

This bound on our error gives us, even in the worst case under our
assumptions of $d=|\mathbb{F}|-1$, that our bound decreases by
$$\left(\frac{|\mathbb{F}|-1}{|\mathbb{F}|}\right)^{|\mathbb{F}|}\leq \left(1-\frac{1}{|\mathbb{F}|}\right)^{|\mathbb{F}|}=e^{-1}.$$

We can now look at another application of the Schwartz-Zippel Lemma:
checking for the existence of perfect matches in bipartite graphs.
[@Tutte]

Let $G=(U,V,E)$ be a bipartite graph with $|V|=|U|=n$ and
$E\subseteq U\times V$. We thus want to check if there exists a set of
edges $M\subseteq E$ such that every vertex is contained in exactly one
edge of $M$. We call such a subset $M$ a perfect matching of $G$.

Let $G=(U,V,E)$ be a bipartite graph. We then define the tutte matrix,
$M_G$, of our graph as follows: $$M_{i,j}=\begin{cases}
      x_{i,j} & (i,j)\in E \\
      0 & (i,j)\not\in E
   \end{cases}$$ where $x_{i,j}$ is a fresh symbolic variable at each
iteration (i.e. each $x_{i,j}$ value is unique.)

The determinant of $M_G$, which is a polynomial in $(x_{i,j})$ with
degree at most $n$, is nonzero as a formal polynomial if and only if $G$
has a perfect matching.

We can use the Leibniz Formula for the determinant:
$$\text{det}(M_G)=\sum_{\sigma\in S_n}\left(\text{sgn}(\sigma)\prod_{i=1}^n M_{i,\sigma(i)}\right)$$
and we then have a 1-1 correspondence between $\sigma\in S_n$ and the
possible perfect matchings in $G$ which can be written as
$\{(u_1,v_{\sigma(1)}),\ldots,(u_n,v_{\sigma(n)}\}$. By the definition
of the tutte matrix we can see that if for some $i$ we have
$(u_i,v_{\sigma(i)})$ (i.e. the possible perfect matching is not in $G$)
then that term of our summation will be $0$ since $M_{i,\sigma(i)}=0$.
We can then restrict our summation range to solely consider
$\sigma\in P$, where $P$ is the set of perfect matchings in $G$. We thus
write
$$\text{det}(M_G)=\sum_{\sigma\in P}\left(\text{sgn}(\sigma)\prod_{i=1}^n M_{i,\sigma(i)}\right)=\sum_{\sigma\in P}\left(\text{sgn}(\sigma)\prod_{i=1}^n x_{i,\sigma(i)}\right)$$
and using this expression we can show the lemma. If the determinant is
$0$ then it is clear that $P=\emptyset$ and thus $G$ has no perfect
matching. If $P\neq\emptyset$, however, we know that for $\sigma\in P$
we have
$\text{sgn}(\sigma)\prod_{i=1}^n M_{i,\sigma(i)}=\text{sgn}(\sigma)\prod_{i=1}^n x_{i,\sigma(i)}\neq 0$
and by our definition of $x_{i,\sigma(i)}$ always being a fresh variable
we know that there does not exist another term in our sum that has the
same set of variables and thus this value is not cancelled out and we
must have a non-zero determinant.

Given the above result and the PIT algorithm we can define an algorithm,
in $RP$, for determining whether $G$ has a perfect matching.
Furthermore, we can also design an algorithm to return a perfect
matching. One major advantage of this tutte matrix approach compared to
the traditional max flow approach is that of easy parallelization. Refer
to [@Mulmuley].

