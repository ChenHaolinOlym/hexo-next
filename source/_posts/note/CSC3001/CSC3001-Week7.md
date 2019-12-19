---
title: CSC3001 Week7
tags:
  - CSC3001
  - Discrete Mathematics
categories:
  - note
  - CSC3001
date: 2019-09-30 14:25:16
---

Modular Arithmetic, Chinese Remainder Theorem

## Modular Arithmetic

**Definition:** $a \ \equiv b \ (\mod n) \ iff \  n|(a - b)$

### Modular Addition, Multiplication

#### Modular Addition

**Lemma:** If a $\equiv$ c (mod n), and b $\equiv$ d (mod n) then a+b = c+d (mod n)

#### Modular Multiplication

**Lemma:** If a $\equiv$ c (mod n), and b $\equiv$ d (mod n) then ab = cd (mod n)

### Applications

**Claim:** A number is divisible by 9 if and only if the sum of its digits is divisible by 9.

**Hint:** 10 $\equiv$ 1 (mod 9)

Let the decimal representation of n be $d_kd_{k-1}d_{k-2}...d_1d_0$

That means that n = $d_k10^k + d_{k-1}10^{k-1} + ... + d_110 + d_0$

So $d_i10^i$ mod 9 $\equiv$ ($d_i$ mod 9)($10^i$ mod 9) $\equiv$ $d_i$ mod 9

#### Invariant Method

1. Find properties (the invariants) that are satisfied throughout the whole process. 
2. Show that the target do not satisfy the properties.
3. Conclude that the target is not achievable.

### Multiplicative Inverses

The **Multiplicative Inverse** of a $\not\equiv$ 0 (mod n) is another integer a' such that: $a \times a' \equiv 1$ (mod n)

**Note:** Not every integer have a multiplicative inverse in modular arithmetic.

**Claim:** If integers k, n are not coprime (i.e. gcd(k, n) $\geq$ 2), then k does not have a multiplicative inverse modulo n.

**Proof:** Suppose k has a multiplicative inverse y

ky $\equiv$ 1 (mod n)

So ky = 1 + nx for some integer x

So ky - nx = 1

If they are not coprime, cannot be stract into 1.

### Cancellation

There is _**no** general cancellation in modular_ arithmetic.

If ac $\equiv$ bc (mod n) and c $\not\equiv$ 0 (mod n), it is not necessarily true that a $\equiv$ b (mod n)

When gcd(n, k) $\geq$ 2 and 0 < |a-b| < n, it's possible that a $\not=$ b and a $\equiv$ b (mod n) is not true.

**Claim:** If ik $\equiv$ jk (mod n) and gcd(k, n) = 1, then i $\equiv$ j (mod n)

### Fermat's Little Theorem, Wilson's Theorem

#### Fermat's Little Theorem

If p is a prime and gcd(k, p) = 1, the we can cancel k. So k (mod p), 2k (mod p), ..., (p-1)k (mod p) are all different.

This yields that k (mod p), 2k (mod p), …, (p-1)k (mod p) must be a must be a permutation of 1, 2, ..., (p-1) (each number appears exactly once.)

**Theorem:** Let p be a prime and gcd(k, p) = 1. Then $k^{p-1} \equiv$  1 (mod p)

**Proof:** 

1·2···(p -1) $\equiv$ (k mod p)· (2k mod p) ··· ((p-1)k mod p) (mod p) 
$\equiv$ (k· 2k ··· (p -1)k) (mod p)
$\equiv$ ($k^{p-1}$)·1·2 ··· (p -1) (mod p)

Since 1, 2, ..., (p -1) are coprime with are coprime with p, they can be cancelled on both side, we have:

$1 \equiv k^{p-1} (\mod p)$

#### Wilson's Theorem

**Theorem:** p is a prime if and only if $(p-1)! \equiv -1(\mod p)$

**Proof:** 

We first consider the converse.
W.l.o.g, suppose p is not a prime and p $\geq$ 6.
Then p = qr for some 2 $\leq$ q, r < p .
If q $\not=$ r, then both q and r appear in (p -1)! and so (p -1)! $\equiv$ 0 (mod p).
If q = r, then p = $q^2$> 2q (since p $\geq$ 6). Then both q and 2q are in (p -1)! and so again (p -1)! $\equiv$ 0 (mod p).

To prove the forward direction, we will need a lemma.

**Lemma:** Let p be a prime number. Then $x^2 \equiv 1 (\mod p)$ if and only if $x \equiv 1 (\mod p)$ or $x \equiv -1(\mod p)$

**Proof:**

$x^2 \equiv  1(\mod p)$

p | $x^2$ - 1 = (x-1)(x+1)

p | (x-1) or p | (x+1)

$x \equiv 1 (\mod p)$ or $x \equiv -1 (\mod p)$

Complete proof can be found on ppt

## Chinese Remainder Theorem

How to solve the following equation?
$$
ax \equiv b (\mod n)
$$
**Case 1:** gcd(a, n) = 1

We can multiply a' on both sides of the equation to obtain: $x \equiv a'b (\mod n)$

**Case 2:** gcd(a, n) = c > 1

**Case 2a:**



**Case 2b:**

