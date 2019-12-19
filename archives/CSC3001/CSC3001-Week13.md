---
title: CSC3001 Week13
tags:
  - CSC3001
  - Discrete Mathematics
mathjax: true
categories:
  - note
  - CSC3001
date: 2019-11-30 09:56:31
---

 Counting by Mapping 

## Functions

F is a function that takes an element in "input set" and output an element in the "output set". What's important is that there is only one output for each input.

![image-20191206234941823](/image-20191206234941823.png)

The *domain*(input) of f is A, the *range*(output) of f is f(A), the *codomain* of f is $B \supseteq f(A)$

For each input there is exactly one output.

### Injections

$f: A \rightarrow B$ is *injective* if no two inputs have the same output.

### Surjections

$f: A \rightarrow B$ is *surjective* if every output is possible.

### Bijections

$f: A \rightarrow B$ is *bijective* if it is both *surjective* and *injective*.

## Bijection Rule

If f is a bijection from A to B, then |A| = |B|.  

### Power Set

Pow(S) = the power set of S = the set of all subsets of S.

### Power Set and Binary Strings

We define a bijection f between subsets and binary strings by the following way:

Given a subset $T \subseteq S$, we define f(T) as an n-bit string such that the i-th bit equal to 1 if and only if $s_i \in T$.

This mapping is a bijection.

Therefore, |A| = |B|, where |B| can be computed directly.

### Use Bijection

**Steps:**

1. Come up with B.

2. Come up with f.

3. Show f is a bijection.

4. Compute |B|. 

## Division Rule

If a function from A to B is k-to-1, meaning that each element in B is mapped by exactly k elements in A then |A| = k|B|

This generalizes the bijection rule.

## Catalan Number

### Monotone Path

A *monotone path* from (0,0) to (n,n) is a path consisting of “right" moves (x-coordinate +1) and “up" moves (y-coordinate +1), starting at (0,0) and ending at (n,n).  

We can map a "right" move to an "x" and a "up" move to a "y". There is  a bijection between monotone paths and words n x's and n y's. And so the answer is just $\binom{2n}{n}$.

A monotone path is called lower-right if any point $(x_i ,y_i)$ on the path has $x_i \geq y_i$

We can know that the size of the set is equal to Catalan Number: $r_n = \frac{1}{n+1}\binom{2n}{n}$

**Proof:** 

The idea is to define a bijection between:

(A) The set of non-lower-right monotone paths from (0,0) to (n,n)

(B) The set of monotone paths from (0,0) to (n-1,n+1)  

Clearly, $|B| = \binom{2n}{n+1}$

**Injection:** Every path in (A) must “cross” the diagonal at least once. We look at the first “crossing”, and then “flip the path”. 

![image-20191208192247048](/image-20191208192247048.png)

**Surjection:** Given a monotone path from (0,0) to (n-1,n+1), it must cross the diagonal. Look at the first such point and flip it, we get back a non-lower-right monotone path from (0,0) to (n,n), which is the preimage of the map. 

So the size = $\binom{2n}{n}-\binom{2n}{n+1} = \frac{(2n)!}{n!n!}-\frac{(2n)!}{(n+!!)(n-1)!} = \frac{(2n)!}{(n+1)!n!} = \frac{1}{n+1}\binom{2n}{n}$