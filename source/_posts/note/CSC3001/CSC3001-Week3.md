---
title: CSC3001 Week3
tags:
  - CSC3001
  - Discrete Mathematics
  - Methods of Proof
mathjax: true
categories:
  - note
  - CSC3001
date: 2019-09-18 10:09:02
---
Methods of Proof

## Direct Proof

### Proving an Implication

To prove an implication: If P, the Q.

**Method 1:** Write assume P, then show that Q logically follows.

## Contrapositive

### Proving an Implication

To prove an implication: If P, the Q.

**Method 2:** Prove the *contrapositive*, i.e. prove "not Q implies not P"

### Proving an "if and only if"

**Method 1a:** Prove P implies Q and Q implies P

**Method 1b:** Prove P implies Q and not P implies not Q

**Method 2:** Construct a chain of if and only if statement(What is this?)

## Proof by Contradiction

$$
\frac{\overline{P} \rightarrow F}{P}
$$

To prove P, you prove that not P would lead to a ridiculous result, and so P must be true.

### Infinitude of the Primes

**Theorem:** There are infinitely many prime numbers.

**Proof** by contradiction:

Assume there are only finitely many primes.
Let $p_1$, $p_2$, ..., $p_k$ be all the primes.
(1) We will construct a number N so that is not divisible by any $p_i$ 
By our assumption, it means that N is not divisible by any prime number.
(2) On the other hand, we show that any number is divisible by any $p_i$.
This will lead to a contradiction, and therefore the assumption must be false.
So there must be infinitely many primes.

## Proof by Cases

e.g. want to prove the square of a nonzero number is always positive.

x is positive or x is negative

if x is positive, then $x^2 > 0$

if x is negative, then $x^2 > 0$

$\therefore x^2 > 0$