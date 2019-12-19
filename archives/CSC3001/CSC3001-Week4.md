---
title: CSC3001 Week4
tags:
  - CSC3001
  - Discrete Mathematics
  - Mathematical Induction
categories:
  - note
  - CSC3001
date: 2019-09-19 22:53:20
mathjax: true
---

## The Idea of Mathematical Induction

**Objective:** Prove $\forall n \geq 0 \ P(n)$

**Universal Generalization:** To prove a for-all statement is to prove that R(c) is true for any c, but this is often difficult to prove directly.

**Mathematical Induction** provides another way to prove a for-all statement. It allows us to prove the statement **step-by-step**.

__*e.g. :*__

### Odd Powers are Odd

**Fact:** If m is odd and n odd, then nm odd. 

**Proposition:** for an odd number m, $m^i$ is odd for all non-negative integer i.
$$
\forall i \in Z \ odd(m^i)
$$
Let P(i) be the proposition that $m^i$ is odd
$$
\forall i \in Z \ P(i)
$$
**Idea of Induction:**

- P(1) is true by definition.
- P(2) is true by P(1) and the fact
- P(3) is true by P(2) and the fact
- P(i+1) is true by P(i) and the fact
- So P(i) is true for all i

### The Induction Rule

Induction Rule is an axiom.
$$
\frac{P(0),\ \forall n \in Z\ P(n)\rightarrow P(n+1)}{\forall m \in Z\ P(m)}
$$




## Basic Induction Proofs

### Proving an Equality

$$
\forall n \geq 1 \ 1^3+2^3+...+n^3=(\frac{n(n+1)}{2})^2
$$

Let P(n) be the induction hypothesis that the statement is true for n.

**Base Case:** P(1) is true

**Induction Step:** Assume P(n) is true, prove P(n+1) is true.

### Property

$\forall n \geq 1, \ 2^{2n} - 1$ is divisible by 3

**Base Case:** $2^{2n} - 1 = 2^2 - 1 = 3$

**Induction Step:** Assume P(i) for some $i \geq 1$ and prove P(i+1)

### Inequality

$$
\forall n \geq 2, \ \frac{1}{\sqrt{1}}+\frac{1}{\sqrt{2}}+...+\frac{1}{\sqrt{n}} > \sqrt{n}
$$

**Base Case:** (n=2) is true.

**Induction Step:** Assume P(i) for some $i \geq 2$ and prove P(i+1)

### Cauchy-Schwarz Inequality

For any $a_1$,..., $a_n$, and any $b_1$, ..., $b_n$, $a_1b_1+a_2b_2+...+a_nb_n \leq \sqrt{a_1^2+a_2^2+...+a_n^2}\sqrt{b_1^2+b_2^2+...+b_n^2}$

**Base Case:** When n = 1, LHS $\geq$ RHS

**Induction Step:** Assume true for all $\leq$ n, prove n+1

So is to prove: $a_1b_1+a_2b_2+...+a_nb_n+a_{n+1}b_{n+1} \leq \sqrt{a_1^2+a_2^2+...+a_n^2}\sqrt{b_1^2+b_2^2+...+b_n^2}+a_{n+1}b_{n+1}$

if we treat $\sqrt{a_1^2+a_2^2+...+a_n^2}$ and $\sqrt{b_1^2+b_2^2+...+b_n^2}$ as c and d, it fits P(2)

So the formula above is less equal than $\sqrt{c^2+a^2_{n+1}}\sqrt{d^2+b^2_{n+1}}$

The problem is solved.

### Some Remarks

There are three important steps in mathematical induction:

- Write down clearly the inductive hypothesis P(n).
- prove the base case P(1) or P(2) etc.
- prove the inductive case, that is, show P(n) implis P(n+1)

## Inductive Constructions

### Gray Code

It's an ordering of all the n-bit strings in a way such that two consecutive n-bit strings differed by only one bit. Think inductively to construct them.

Every (n+1)-bit string appears exactly once. So by induction, Gray Code exists for any n.

### Puzzle

**Goal:** tile the squares, except one in the middle for Bill.

There are only trominos (L-shaped tiles) covering three squares:

![image-20191028214558403](/image-20191028214558403.png)

**Theorem:** For any $2^n \times 2^n$ puzzle, there is a tiling with Bill in the middle

**Base Case:** (n=0) no tile is needed

**Induction Step:** Assume can tile $2^n \times 2^n$, prove can handle $2^{n+1}\times 2^{n+1}$

**Idea:** It would be nice if we could control the locations of the empty square

**New Idea:** Prove that we can always find a tiling with Bill _anywhere_.

**Theorem B:** For any $2^n \times 2^n$ puzzle, there is a tiling with Bill anywhere.

**Base Case:** (n=0) no tile is needed

**Induction Step:** Assume we can get Bill anywhere in $2^n \times 2^n$, Porve we can get Bill anywhere in $2^{n+1}\times 2^{n+1}$.

### Some Remarks

- It may help to choose a stronger statement than the desired result, 
- The proof of "Bill Anywhere" implicitly defines a recursive algorithm for finding such a tiling.

### Hadamard Matrix

Hadamard Matrix is an $n \times n$ matrix that all entries are $\pm 1$ and all the rows are orthogonal to each other.

So by induction there is a $2^k \times 2^k$ Hadamard Matrix for any k

For odd n, there isn't $n \times n$ Hadamard Matrix 

## A Paradox

**Theorem:** All horses have the same color

**Base Case:** (n=0) no horse, true

**Inductive Steps:** Assume any n horse have the same color, prove that any n+1 horses have the same color.

So it's true.

**Pay attention to the base case.** The inductive steps should be inductable to the base case.

## Strong Induction

### Unstacking Game

**Start:** a stack of boxes

**Move:** split any stack into two stacks of sizes, a, b > 0

**Scoring:** *ab* points

Keep Moving until stuck

**Overall Score:** Sum of move scores

![image-20191028220851756](/image-20191028220851756.png)

What is the best way to play the game?

**If we just move one box at a time:**

Total Score = $\sum^{n-1}_{i=1} = \frac{n(n-1)}{2}$

**Claim:** Starting with size n stack, the highest score will be $\frac{n(n-1)}{2}$

**Base Case:** (n=0) is okay

**Inductive Step:** Assume for n-stack, and then prove C(n+1)

(n+1)-stack score = $\frac{(n+1)n}{2}$

**Case** n+1 = 1, verify i-stack, true

**Case** n+1 > 1:

(a+b)-stack score = ab + a-stack score + b-stack score

**by induction:** 

a-stack score = $\frac{a(a-1)}{2}$

b-stack score = $\frac{b(b-1)}{2}$

So ab + $\frac{a(a-1)}{2}$ + $\frac{b(b-1)}{2}$ = $\frac{(n+1)n}{2}$

So C(n+1) is okay.

### Induction Hypothesis

We assume C(a) and C(b) where 1 $\leq$ a, b $\leq$ n. But by (to use) induction can only assume C(n).

**the fix:** rephrase the induction hypothesis to Q(n) ::= $\forall m \leq n. \ C(m)$

Proof goes through fine using Q(n) instead of C(n). So it’s OK to assume C(m) for all m $\leq$ n to prove C(n+1).

### Strong Induction

**Strong Induction:** Prove P(0). Then prove P(n+1) assuming all of P(0), P(1), ..., P(n) (instead of just P(n)). Conclude $\forall n. \ P(n)$

**Ordinary Induction:** 0 $\rightarrow$ 1, 1 $\rightarrow$ 2, 2 $\rightarrow$ 3, …, n-1$\rightarrow$ n.
So by the time we get to n+1, already know all of P(0), P(1), ..., P(n).

**The point is:** assuming P(0), P(1), up to P(n), it is often easier to prove P(n+1)

#### Divisible by a Prime

**Theorem:** Any integer n > 1 is divisible by a prime number.

**Proved by Strong Induction:** 

**Theorem:** Every integer > 1 is a product of primes.

**Proof:** (by strong induction)

- Base case is easy.
- Suppose the claim is true for all 2 $\leq$ i < n.
- Consider an integer n.
- If n is prime, then we are done.
- Otherwise n = k·m for integers k, m where 2 $\leq$ k,m < n.
- By the induction hypothesis, both k and m are product of primes.
  - k = $p_1 \times p_2 \times ... \times p^{94}$
  - m = $q_1 \times q_2 \times ... \times q_{214}$
- So n = k $\times$ m = $p_1 \times p_2 \times ... \times p^{94} \times q_1 \times q_2 \times ... \times q_{214}$ is a prime product.
- Proof complete

## Well Ordering Principle

**Axiom:** Every nonempty set of *natural numbers* has a *least element*

This axiom is in fact a consequence of mathematical induction.

### Without Common Factors

For $\sqrt{2} = \frac{m}{n}$ We can always find such m, n *without common factors*

If m, n with common factors, by WOP, there's a minimum, but both can be divided by a same number, contradiction.

### Non-Fermat Theorem

$$
4a^3 + 2b^3 = c^3
$$

There is no positive integer solutions for it.

**Proof:** We construct the set, S ::= {a $\in \ Z^+$ | $\exist \ b, c \in Z^+, \ 4a^3 + 2b^3 = c^3$}

By WOP, there exists (a, b, c) $\in$ S where a is the smallest among all "a"s

Since $c^3$ is even, c is even. Let c = 2c', then $4a^3 + 2b^3 = (2c')^3$

So $b^3 = 4c'^3 - 2a^3$

Since $b^3$ is even, b must be even. Let b = 2b', then $(2b')^3 = 4c'^3 - 2a^3$

So $a^3 = 2c'^3 - 4b'^3$

Since $a^3$ is even, a must be even

### Well Ordering Principle in Proofs

*To prove " $\forall$ n$\in$N. P(n)" using WOP:*

1. Construct the set
S ::= { n$\in$N | $\neg$P(n)}
2. Assume $\neg$P(n) exists, so that S is a well-ordered set.
3. By WOP, have a "least" element $n_0 \in S$ (we may have different meaning of “ small ” in some circumstances. )
4. Reach a contradiction (use whatever methods you want including mathematical induction) – usually by finding an element of S that is < $n_0$ .
5. Conclude that P(n) is true. QED

## Invariant Method

1. Find properties (the invariants) that are satisfied throughout the whole process. 
2. Show that the target do not satisfy the properties.
3. Conclude that the target is not achievable.