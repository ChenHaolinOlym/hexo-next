---
title: CSC3001 Week12
tags:
  - CSC3001
  - Discrete Mathematics
mathjax: true
categories:
  - note
  - CSC3001
date: 2019-11-30 09:55:26
---

Combinatorial Proofs and its Principles

Combinatorics is a typical technique in discrete mathematics. This technique is proved very useful in counting and enjoys wide range applications from evolutionary biology to computer science, etc.  

## Binomial Coefficients, Combinational Proof

### Binomial Theorem

$(1+x)^n = c_0 + c_1x + c_2x^2 + \dots + c_nx^n$

- Each term corresponds to selecting 1 or x from each of the n factors.
- So the coefficient $c_k$ corresponds to the number of ways for choosing k positions of x from n factors. 
- Therefore, $c_k = \binom{n}{k}$, these are called the binomial coefficients

$(1+x)^n = \binom{n}{0} + \binom{n}{1}x + \binom{n}{2}x^2 + \dots + \binom{n}{n}x^n$

- We see that the coefficients are the sums of two coefficients in the upper level.

- This is called the Pascal’s formula.

### Binomial Coefficients

In general we have the following identity:

$(y+x)^n = \binom{n}{0}y^n + \binom{n}{1}xy^{n-1} + \dots + \binom{n}{n}x^n$

because if we choose k x’s then there will be n-k y’s. 

#### Corollary

- When x = 1, y = 1, it implies that $2^n = \binom{n}{0} + \binom{n}{1} + \dots + \binom{n}{k} + \dots + \binom{n}{n}$, that is,  the sum of the binomial coefficients is equal to $2^n$.
- When x = -1, y = 1, it implies that $0 = \binom{n}{0} - \binom{n}{1} + \binom{n}{2} - \binom{n}{3} + \binom{n}{4} + \dots + (-1)^n\binom{n}{n}$, that is, The sum of “odd” binomial coefficients **equals to** the sum of “even” binomial coefficients.

### Proving Identities

$\binom{n}{k} = \binom{n}{n-k}$

**Direct Proof:** $\binom{n}{k} = \frac{n!}{k!(n-k)!} = \binom{n}{n-k}$

**Combinational Proof:**  Number of ways to choose *k* items from *n* items **equals to** number of ways to choose *n-k* items from *n* items.

### Combinational Proof

A **combinatorial proof** is an argument that establishes algebraic facts by counting principles. Many such proofs follow the same basic outline:

1. Define a set S.
2. Show that |S| = n by counting one way.
3. Show that |S| = m by counting another way.
4. Conclude that n = m. 

#### Pascal's Formula

$\binom{n+1}{k} = \binom{n}{k-1} + \binom{n}{k}$

**Combinatorial proof:**

LHS =  number of ways to choose *k* elements from *n+1* elements

For RHS, fix an element x in the n+1 elements.

1) If the *k* elements contain *x*, then we need to choose *k-1* elements from the remaining *n* elements, so$\binom{n}{k-1}$. 

2) If the *k* elements do not contain *x*, then we need to choose *k* elements from the remaining *n* elements, so $\binom{n}{k}$.

Hence, we complete the proof.  

## Inclusion-exclusion Principle

**The inclusion-exclusion formula for the union of n sets:** 
$$
|\cup^n_{i=1}A_i| = \sum^n_{i=1}|A_i| - \sum_{1 \leq i \leq j \leq n}|A_i \cap A_j| + \sum_{1 \leq i \leq j \leq k \leq n}|A_i \cap A_j \cap A_k| + \dots + (-1)^{n+1}|A_1 \cap \dots \cap A_n|
$$
## Pigeonhole Principle

A function from a larger set to a smaller set cannot be injective. (There must be at least two elements in the domain that are mapped to the same element in the range.) 

### Generalized Pigeonhole Principle

If n pigeons and h holes, then some hole has at least $\lceil \frac{n}{h}\rceil$ pigeons.
