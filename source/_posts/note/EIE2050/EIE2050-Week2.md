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

## Addition and Subtraction in digital system

We are able to use the addition operation to replace the subtraction operation.
In another word, addition and subtraction in digital system are the same.

$$
\begin
(111)_2-(101)_2\\\\
&=(111)_2+[ (1000)_2-(101)_2 ]\\\\

\end
$$
