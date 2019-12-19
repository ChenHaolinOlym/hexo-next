---
title: CSC3001 Week5
tags:
  - CSC3001
  - Discrete Mathematics
categories:
  - note
  - CSC3001
date: 2019-09-30 14:14:47
mathjax: true
---

Recursion is one of the most important techniques in computer science. The main idea is to capture the invariants over repeated actions.

## Setting up Recurrences

We can difine a sequence by specifying relation between the current term and the previous terms.

### Fibonacci Recurrence

#### Rebbit Populations

- A mature boy/girl rabbit pair reproduces every month.
- Rebbits mature after one month
  
  - $w_n$::= # newborn pairs in the n-th month
  - $r_n$::= # pairs in the n-th month
- Start with a newborn pair: $w_0 = 1$, $r_0 = 0$
- How many rabbits after n months?

**closed form:** A formula so that # steps for calculating $r_n \leq$ constant

#### Number of Bit Strings Without a Specific Pattern

**How many n-bit strings without the bit pattern 11?**

**Case 1:** The first bit is 0.

Then any (n -1)-bit string without the pattern 11 can be appended to the end form an an n-bit string without 11. So in this case there are exactly $r_{n-1}$ such n-bit strings.

**Case 2:** The first bit is 1.

Then the second bit must be 0. Then any (n-2)-bit string without the bit pattern 11 can be apppended to the end to form an n-bit string without 11. So in this case there are exactly $r_{n-2}$ such n-bit strings.


### Problem Solving Recurrences

#### Tower of Hanoi

![image-20191029164758449](/image-20191029164758449.png)

The **goal** is to move all the disks to post 3.

The **rule** is that a bigger disk cannot be placed on top of a smaller disk.

Think recursively

#### Merge Sort

See CSC3100.

### Catalan Recurrences

#### Parenthesis

How many valid ways to add n pairs of parenthesis?

Let $r_n$ be the number of ways to add n pairs of parenthesis.

**Case 1:** ()------------------   So there are $r_{n-1}$ in this case

**Case 2:** (--)----------------   So there are $r_{n-2}$ in this case

**Case 3:** (----)--------------   So there are $2r_{n-3}$ in this case

......

**Case k:** (-----------)-------   So there are $r_{k-1}r_{r-k}$ ways in case k

Therefore, by the sum rule, $r_n = \sum^n_{k=1}r_{k-1}r_{n-k}$

#### Stairs

An n-stair is the collection of unit squares bounded by x-axis, y=x and x=n+1.
For example 1-stair, 2-stair, and 3-stair are like this:

![image-20191030211422956](/image-20191030211422956.png)

Given the n-stair, the first observation is that positions on the diagonal (red numbers) must be covered by different recangles.

Since there are n positions in the diagonal and we can only use n rectangles, each rectangle must cover exactly one red number.

![image-20191030212202520](/image-20191030212202520.png)

Consider the rectangle R that covers the bottom right corner (marked with o). We consider different cases depending on which red number is covered by R.

Then go with recursion.

![image-20191030213705405](/image-20191030213705405.png)

Proof can be found in ppt.

The total number of ways is equal to $r_n = \sum^n_{i=1}r_{i-1}r_{n-i}$

### Catalan Number

The recursion for the stair problem is the same as the recursion for the parentheses problem. It can be showed that $r_n = \frac{1}{n+1} \binom{2n}{n}$

This is well known as the n-th Catalan number.

## Solving Recurrences

Two ways:

1. Guess + Mathematical Induction
2. Direct Compute

### Solving Fibonacci Sequence

#### Generating Functions

<$a_0$, $a_1$, $a_2$, $a_3$, ...> $\leftrightarrow$ F(x)

This is called the *ordinary generating function* for {$a_n$}

F(x) = $a_0$ + $a_1x$ + $a_2x^2$ + $a_3x^3$ + ...

**Right Shifting:** <0, 0, 0, 0, ..., $a_0$, $a_1$, $a_2$, $a_3$, ...> $\leftrightarrow$ $x^k$F(x)

**Differentiation:** <$f_0$, $f_1$, $f_2$, $f_3$, ...> $\leftrightarrow$ F(x) $\rightarrow$ <$f_1$, $2f_2$, $3f_3$, ...> $\leftrightarrow$ F'(x)

#### Solving

The generating function for {$f_n$} is F(X) = $f_0$ + $f_1x$ + $f_2x^2$ + $f_3x^3$ + ... = 0 + x + ($f_1$ + $f_0$)$x^2$ + ($f_2$ + $f_1$)$x^3$ + ...

![image-20191031013631922](/image-20191031013631922.png)

So F(x) = x + xF(x) + $x^2$F(x)

So we can get F(x) = $\frac{x}{1-x-x^2}$

Then we can do Partial Fractioning and Taylor Series Expand.

#### Second Order Recurrence Relation

$$
a_k = Aa_{k-1} + Ba_{k-2}
$$

This is called "second-order linear homogeneous recurrence relation with constant coefficients". Fibonacci sequence is when A=B=1.

#### Distinct-Roots Theorem

Suppose a sequence ($a_0$, $a_1$, $a_2$, $a_3$, ...) satisfies a recurrence relation $a_k = Aa_{k-1} + Ba_{k-2}$.

If $t^2-At-B = 0$ has two distinct roots r and s, then $a_n = Cr^n + Ds^n$ for some C and D.