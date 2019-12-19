---
title: CSC3001 Week6
tags:
  - CSC3001
  - Discrete Mathematics
categories:
  - note
  - CSC3001
date: 2019-09-30 14:14:53
---

greatest common divisors

## Common Divisors

c is a common divisor of a and b means c|a and c|b gcd(a, b) ::= the greatest common divisor of a and b.

**Claim:** If p is prime, and p does not divide a, then gcd(p, a) = 1.

### The Quotient-Remainder Theorem

For b > 0 and any a, there are *unique* integers q ::= quotient(a, b), r ::= remainder(a, b), such that a = qb + r and 0 $\leq$ r < b.

We also say q = a div b and r = a mod b

### Greatest Common Divisors

Given a and b, how to compute gcd(a, b)?

Let's say a $\geq$ b

1. If a = kb, the gcd(a, b) = b, and we are done
2. Otherwise, by the Division Theorem, a = qb + r where r > 0

### Euclid's GCD Algorithm

gcd(a, b) = gcd(b, r)

gcd(a, b)

if b = 0, the answer = a.

else: write a = qb + r

answer = gcd(b, r)

### Proof of Euclid's GCD Algorithm

When r = 0, clearly correct

When r > 0:

Let d be a common divisor of b, r

- b = $k_1$d and r = $k_2$d for some $k_1$, $k_2$
- a = qb + r = q$k_1$d + q$k_2$d = (q$k_1$ + $k_2$)d

You can also prove this from another direction.

### Linear Combination vs. Common Divisor

**Greatest Common Divisor:** 



**Theorem:** gcd(a, b) = spc(a, b)

