---
title: CSC3100 Week3
tags:
  - CSC3100
  - Data Structure
  - Algorithm
categories:
  - note
  - CSC3100
date: 2019-09-20 09:57:53
mathjax: true
---

## Asymptotic notation of function growth

### Three Key Definitions

1. $T(N) = O(g(N)) \ if \  \exists c, n_0 \in R^+ \ s.t. \  T(N) \leq cg(N) \ when \  N \geq n_0$
2. $T(N) = \Omega (g(N)) \ if \  \exists c, n_0 \in R^+ \ s.t. \  T(N) \geq cg(N) \ when \  N \geq n_0$
3. $T(N) = \Theta (g(N)) \ if \ T(N) = O(g(N)) \ and \ T(N) = \Omega (g(N))$

The increasing speed of O and $\Omega$ usually are the same.
Usually we just use Big Oh to represent $\Theta$

### Big Oh Notation

O(g(n)) = {T(n): there exist positive constants c and $n_0$ such that 0 $\leq$ T(n) $\leq$ cg(n) for all n $\geq$ $n_0$}

g(n) is an asymptotic **upper** bound for T(n). If T(n) $\in$ O(g(n)), we write T(n)=O(g(n))

#### Relationship

$O(1) < O(\log n) < O(n) < O(n\log n) < O(n^2) < O(n^3) < O(2^n) < O(n!) < O(n^n)$

### $\Omega$ Notation

$\Omega$ (g(n)) = {T(n): there exist positive constants c and $n_0$ such that 0 $\leq$ cg(n) $\leq$ T(n) for all n $\geq$ $n_0$}.

g(n) is an asymptotic **lower** bound  for T(n). If T(n) $\in$ $\Omega$(g(n)), we write T(n)=$\Omega$(g(n))

### $\Theta$ Notation

$\Theta$(g(n))={f(n): there exist positive constants $c_1$, $c_2$ and $n_0$ such 0 $\leq$ $c_1$g(n) $\leq$ T(n) $\leq$ $c_2$ g(n)  for all n $\geq$ $n_0$}.

g(n) is an asymptotic tight bound for T(n) if and only if T(n)=O(g(n)) and T(n)=$\Omega$(g(n)).

## Relational Properties

**Transitivity:** T(N) = $\Omega$(g(n)) and g(n) = $\Theta$(h(n)) $\Rightarrow$ T(N) = $\Theta$(h(n)). *Same for O and $\Omega$*
**Reflexivity:** T(N) = $\Theta$(T(N)). *Same for O and $\Omega$*
**Symmetry:** T(N) = $\Theta$(g(n)) if and only if g(n) = $\Theta$(T(N))
**Transpose Symmetry:** T(N) = O(g(n)) if and only if g(n) = $\Omega$(T(N))

## Typical Growth Rate

Function | Name
:-: | :-:
c | Constant
logN | Logarithmic
$log^2$N | Log-Squared
N | Linear
NlogN | 
$N^2$ | Quadratic
$N^3$ | Cubic
$2^N$ | Exponential

## Growth Rate Computation

### Rule 1

If $T_1(N) = O(f(N))$ and $T_2(N) = O(g(N))$, then:
(a) $T_1(N)+T_2(N) = max(O(f(N))), O(g(N)))$
(b) $T_1(N)\*T_2(N) = O(f(N)\*g(N))$

### Rule 2

If T(N) is a polynomial of degree k, then T(N) = $\Theta$($N^k$)

### Rule 3

**************************

$log^kN = O(N)$ for any constant k. This tells that logarithms grow very slowly.

**************************

### Addition

$log^{k}n = O(n)$

implies

$log^{k}n = O(2^{logn})$

implies

$n^k = O(2^n)$

## Analyzing Algorithms Using Notations

**Rule 1:** For Loops is O(N)

**Rule 2:** Nested For Loop is $O(N^n)$, n is the number of nested layers

**Rule 3:** Consecutive Statements, choose the growing fastest one.

**Rule 4:** Conditional Statement:

```en
if (condition)
    S1
else
    S2
```

The larger running time of S1 and S2

## Maximum Subarray Problem

The task of finding a contiguous subarray with the largest sum.

### A Divide and Conquer Solution

If we pick the middle point of the array, there are three situations of the subarray: left, right and cross the mid point.

Solve the left, right case recursively, then compare them with the third case, choose the largest.

### Analyze Running Time

For base case, $T(1) = \Theta (1)$
For subarrays, $2T(\frac{n}{2})$
For mid point situation, $\Theta (n)$

So the running time $T(n) = 2T(\frac{n}{2})+ \Theta n$

Same as Merge Sort $\Theta (nlogn)$

## Recurrence

A recurrence is a function defined in terms of:

1. One base
2. Itself with smaller arguments

### Method to Compute the Recurrence

- Guess the solution
- Use induction to prove
- Called substitution method

### Recursion Trees

Summing accross each level in te recursion tree.

### Master Method

Used for many divide-and-conquer recurrences of the form:

$T(n) = aT(\frac{n}{b}) + f(n)$ where $a \geq 1$, $b > 1$ and $f(n) > 0$