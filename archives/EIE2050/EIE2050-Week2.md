---
title: EIE2050 Week2
tags:
  - EIE2050
  - Digital Logic and Systems
mathjax: true
categories:
  - note
  - EIE2050
date: 2019-09-04 14:55:20
---

## The meaning of Number

What's the meaning of $(123.456)\_{10}$, $(101.101)\_{2}$?

What's the meaning of $(abc.def)_{g}$?

$(123.456)\_{10} = 1\*10^2+2\*10^1+3\*10^{0}+4\*10^{-1}+5\*10^{-2}+6\*10^{-3}$

$(101.101)\_{2} = 1\*2^2+0\*2^{1}+1\*2^{0}+1\*2^{-1}+0\*2^{-2}+1\*2^{-3}$

$(abc.def)_{g} = a\*g^2+b\*g^{1}+c\*g^{0}+d\*g^{-1}+e\*g^{-2}+f\*g^{-3}$

We can understand any arbitrary number system in this way.

## Conversion of number system of different base with decimal

I have learned before.

## Problems in Computer Science

1. What is the problem?
2. How is the problem solved?
3. Why is the solution correct?

Ask the three questions for any topic in Computer Science.

## Represent Minus Number in Computer

### Leave a Bit for Minus Symbol

This is the easiest way to represent negative number. But it will cause some waste.
Because +0 and -0 is the same number, so there will be waste in every byte.

### Commonly Used Way

Computers use a modified 2’s complement for signed numbers. Positive numbers are stored in true form (with a 0 for the sign bit) and negative numbers are stored in complement form (with a 1 for the sign bit).

### Easy Way to Read Minus Number

Assign the sign bit a column weight of -128 (for an 8-bit number). Then add the column weights for the 1’s.

e.g. 

$(11000110)_2$ is 2's complement of -58

Then 1 1 0 0 0 1 1 0

-128+64+0+0+0+4+2 = -58

## Addition and Subtraction in digital system

We are able to use the addition operation to replace the subtraction operation.
In another word, addition and subtraction in digital system are the same.
$$
\begin
(111)_2-(101)_2\\\\
&=(111)_2+[ (1000)_2-(101)_2 ]\\\\

\end
$$





## 1's Complement

The 1’s complement of a binary number is just the inverse of the digits. To form the 1’s complement, change all 0’s to 1’s and all 1’s to 0’s.

In digital circuits, the 1’s complement is formed by using inverters.

## 2's Complement

The 2’s complement of a binary number is found by adding 1 to the LSB of the 1’s complement.

the 1’s complement of 11001010 is 00110101, 2's complement if 11001010 is 00110110.



