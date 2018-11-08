---
layout:     post
title:      Combinatorial Nullstellensatz
date:       2018-10-29 20:28:15
categories: math
---

For the following theorems and examples we let $\mathbb{F}$ be a field
and $\mathcal{P}[x_1,\ldots,x_n]$ be a formal polynomial over
$\mathbb{F}$. Note that in our definition of formal polynomials we
consider a polynomial as being uniquely defined by its coefficients.

## Combinatorial Nullstellensatz

We now move on to the related Combinatorial Nullstellensatz,
[@Alon; @Michalek] which gives us conditions under which we are assured
a point within a defined sub-cube for which our polynomial doesn’t
vanish.

Let $\mathcal{P}(x_1,\ldots,x_n)$ be a polynomial in
$\mathbb{F}[x_1,\ldots,x_n]$ with deg$(\mathcal{P})=\sum_{i=1}^n k_i$
where each $k_i\in\mathbb{N}$ and suppose that the coefficient
$x_1^{k_1}x_2^{k_2}\cdots x_n^{k_n}$ in $\mathcal{P}$ is non-zero. Then
for any collection of subsets $S_1,\ldots,S_n\subseteq \mathbb{F}$ such
that $|S_i|>k_i$ for all $i$ we have that there exists
$\overline{x}\in S_1\times\cdots\times S_n$ such that
$\mathcal{P}(\overline{x})\neq 0$.

We show the above result through induction on
$d\triangleq \text{deg}(\mathcal{P})$. The base case of $d=1$ is trivial
since a polynomial of degree $d$ will have at most $d$ roots. Now let
$d>1$ and for contradiction’s sake assume that $\mathcal{P}$ satisfies
all of our theorem’s assumptions and yet $\mathcal{P}\equiv 0$ on
$S_1\times S_2\times\cdots\times S_n$. We can assume without loss of
generality that $\alpha_1>0$. Now fix any $s\in S_1$. We can then use
the division algorithm to give us the following polynomial:
$$\mathcal{P}(x_1,\ldots,x_n)=(x_1-s)\mathcal{Q}(x_1,\ldots,x_n)+R(x_2,\ldots,x_n).$$

Now let $x\in \{s\}\times S_2\times\cdots\times S_n$. We then have that
$\mathcal{P}(x)=0$ implies that $R(x)=0$. Since $R$ does not contain
$x_1$ we can also say that $R$ vanishes on
$(S_1-\{s\})\times S_2\times\cdots\times S_n$. Now if we fix
$x\in (S_1-\{s\})\times S_2\times\cdots\times S_n$ it follows that
$x_1-s$ is non-zero but since we assumed the polynomial vanishes it must
be true that $Q(x)=0$ and we thus have that $Q$ vanishes on
$(S_1-\{s\}\times S_2\times\cdots\times S_n$. Since we also have
deg$(Q)=\text{deg}(P)-1$ this vanishing implies a smaller counterexample
which contradicts our inductive hypothesis.

We now look at some possible applications of the above result, starting
with the Cauchy-Davenport Theorem.

Let $p$ be a prime and $A,B$ be two non-empty subsets of $\mathbb{F}_p$
and define $A+B=\{a+b\mid a\in A, b\in B\}$. Then,
$$|A+B|\geq \text{min}\{p, |A|+|B|-1\}.$$

The $|A|+|B|>p$ case is straightforward since for any
$x\in \mathbb{F}_p$ there are $p$ distinct expressions of the form $a+b$
that equal $x$. Since the sum of elements in our sets is greater than
$p$ we must then have that these expressions overlap and thus
$A+B=\mathbb{F}_p$. Now we consider the $|A|+|B|\leq p$ case. Assume for
contradiction’s sake that $|A+B|\leq |A|+|B|-2$ and let
$C\subseteq \mathbb{F}_p$ such that $A+B\subset C$ and $|C|=|A|+|B|-2$.
Now define $\mathcal{P}(x,y)=\prod_{c\in C}(x+y-c)$ be a polynomial over
$\mathbb{F}_p$. (Note that $\mathcal{P}(a,b)=0$ for all
$a\in A, b\in B\colon a+b\in C$.) Now let
$S_1\triangleq A, S_2\triangleq B$ and since the coefficient of
$x^{|A|-1}y^{|B|-1}$ is given by ${|A|+|B|-2\choose |A|-1}$ and since
$p$ is a prime by assumption we know that this coefficient is non-zero
in $\mathbb{F}_p$ and thus by the CNSS we have that there exists
$(x,y)\in A\times B$ such that $\mathcal{P}(x,y)\neq 0$. Since our
polynomial was constructed such that it vanishes for all points in $C$
we reach a contradiction since $A+B\not\subset C$.

Now we look at the Chevalley-Warning Theorem, which concerns algebraic
varieties in $\mathbb{F}_p^n$.

Let $\mathcal{P}_1,\ldots,\mathcal{P}_m$ be a collection of polynomials
in $\mathbb{F}_p^n$. We then define the vanishing set:
$$\mathcal{V}(\{\mathcal{P}_i\}_i)\triangleq \{x\in\mathbb{F}_p^n\colon \mathcal{P}_i(x)=0\text{ for all i}\}.$$

Given the above definition, however, we note that different collections
can have the same vanishing set, e.g. for $\vec{c}=\{c_1,\ldots,c_n\}$
we could consider
$\mathcal{A}=\{x-c_1,x-c_2,\ldots,x-c_n\}, \mathcal{B}=\prod_{i=1}^n(x-c_i)$
and it is clear that
$\mathcal{V}(\mathcal{A})=\mathcal{V}(\mathcal{B})=\vec{c}$. We can thus
associate a “cost measure” to the collections of polynomials, namely the
sum of the degrees of each polynomial in the collection, which define a
singleton vanishing set. Further, we can bound the minimum of this cost
measure required to specify such a vanishing set.

Let $\mathcal{P}_1,\ldots,\mathcal{P}_m\in \mathbb{F}[x_1,\ldots,x_n]$
and assume that $\mathcal{V}(\{\mathcal{P}_i\}_i)=\{\overline{c}\}$
where $\overline{c}\in \mathbb{F}_p^n$. Then,
$$\sum_{i=1}^m \text{deg}(\mathcal{P}_i)\geq n.$$

Assume for sake of contradiction that we have the desired singleton
vanishing set but $\sum d_i<n$. Let
$$\mathcal{P}\triangleq \prod_{i=1}^m \left[1-\mathcal{P}^{p-1}\right]-\delta\prod_{j=1}^n\prod_{a\neq c_j}(x_j-a)$$
where we choose $\delta$ such that $\mathcal{P}(\overline{c})=0$. (Note
that the LHS evaluates to $1$ on $\overline{c}$ so $\delta\neq 0$.)

Let $S_i=\mathbb{F}$ for all $i$ and define
$\vec{\alpha}\triangleq (p-1,p-2,\ldots,p-n)$ and consider
$x^{\vec{\alpha}}$. We claim that $F\equiv 0$ on
$S_1\times\cdots\times S_n$ and to show this we will prove the existence
of some leading term with degree $\leq p-1$ in $x_1,\ldots x_n$.

In the $x=\vec{c}$ case it is clear that $\mathcal{P}\equiv 0$ by
definition. Now we consider the $x\neq\vec{c}$ and assume WLOG that
$x_k\neq \vec{c}_k$. In this case we note that $x\neq\vec{c}$ implies
that for some $i$ we have $\mathcal{P}_i(x)\neq 0$ which implies that
the LHS evaluates to $0$ since $1-\mathcal{P}_i(x)^{p-1}=0$ and we must
also have that the RHS evaluates to $0$ since by our assumption
$x_k\neq c_k$ and thus $\prod_{a\neq c_k}(x_k-a)$ will have a zero term.
Since the degree of the LHS is $(p-1)\cdot\sum d_i<(p-1)n$ but it has a
non-zero coefficient of the term $\prod x_i^{p-1}$ it thus gives us a
contradiction through CNSS, which assures us a non-zero value of
$\mathbb{F}$.

Our final application is that of covering the boolean cube,
$C^n\triangleq \{0,1\}^n$, with hyperplanes. We define a hyperplane,
$H$, as follows:
$$H\triangleq \{\vec{x}\colon \langle \vec{a}, \vec{x}\rangle=b\}\text{ for a given }\vec{a},b$$

Let $H_1,\ldots,H_m$ cover all of $C^n$ except for one point. Then we
have that $m\geq n$.

Assume without loss of generality that the one point not covered by our
hyperplanes is $\vec{0}$ and let our collection of hyperplanes,
$\{H_i\}$, be defined such that $H_i=\{\langle a_i,x\rangle=b_i\}$. For
contradiction’s sake assume that $m<n$ and consider
$$\mathcal{P}(x)\triangleq(-1)^{n+m+1}\left(\prod_{j=1}^mb_j\right)\left(\prod_{i=1}^n(x_i-1)\right)-\prod_{i=1}^m\left(\langle a_i,x\rangle - b_i\right).$$
From the left term we clearly have that deg$(\mathcal{P})=n$ and the
coefficient of it is $(-1)^{m+n+1}\prod_{j=1}^mb_j\neq 0.$ By CNSS we
then have that there exists $\vec{x}\in\{0,1\}^n$ such that
$\mathcal{P}(\vec{x})\neq0$. This point $\vec{x}$, however, is not
$\vec{0}$ since the LHS of our polynomial is designed to cancel the RHS
under $\vec{0}$, and thus $\mathcal{P}(\vec{0})=0$. We know that our LHS
vanishes for $\vec{x}\neq 0$ and thus $\mathcal{P}(\vec{x})\neq 0$
implies that the RHS doesn’t vanish. We thus have
$\langle a_i,\vec{x}\rangle -b_i\neq 0$ for all $i$ and thus $\vec{x}$
is not in any $H_i$, giving us the desired contradiction.
