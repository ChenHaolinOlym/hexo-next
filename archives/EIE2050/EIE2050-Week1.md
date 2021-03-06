---
title: EIE2050 Week1
tags:
  - EIE2050
  - Digital Logic and Systems
categories:
  - note
  - EIE2050
mathjax: true
date: 2019-09-02 13:44:26
---

## Before lecture

There's a difference in mathematical logic(数理逻辑), digital logic(数字逻辑).

## A new programming language

"AND", "OR", "NOT" can consist a programming language. And they are called logical gates.

These three can be compressed in to one element.

### One-base Half Adder(加法器)

#### Binary Add

0+0 = 0
0+1 = 1
1+0 = 1
1+1 = $(10)_2$

#### Binary Digital Operation

You can treat 0 as False and 1 as True

**Results:**

1 AND 1 = 1
1 AND 0 = 0
0 AND 1 = 0
0 AND 0 = 0

1 OR 1 = 1
1 OR 0 = 1
0 OR 1 = 1
0 OR 0 = 0

NOT 1 = 0
NOT 0 = 1

**One bit addition:**

Others are the same as binary addition.

1 + 1 = 0

#### Truth Table(真值表)

Z = X + Y

X | Y | Z
:-: | :-: | :-:
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 0

Z = [(not X) and Y] OR [X and not Y]

Can also be written into:

$$Z = \overline{X} · Y + X · \overline{Y}$$

**Notations:**

- +: OR
- ·: AND
- -(overline): NOT

Only consider the situation where Z == 1.

### n-base Half Adder

n-base half adder will have $2^{2n}$ lines.

How to solve the situation that have too many lines?

### Full Adder

Using Caries(进位)

$C_{in}$ for carry in and $C_{out}$ for carry out.

Z + $C_{out}$ = X + Y + $C_{in}$

X | Y | $C_{in}$ | Z | $C_{out}$
:-: | :-: | :-: | :-: | :-:
0 | 0 | 0 | 0 | 0
0 | 0 | 1 | 1 | 0
0 | 1 | 0 | 1 | 0
0 | 1 | 1 | 0 | 1
1 | 0 | 0 | 0 | 1
1 | 0 | 1 | 1 | 0
0 | 0 | 0 | 0 | 1
1 | 1 | 0 | 0 | 1
1 | 1 | 1 | 1 | 1

$$Z = \overline{X} · \overline{Y} · C_{in} + X · \overline{Y} · \overline{C_{in}} + \overline{X} · Y · \overline{C_{in}} + X · Y · C_{in}$$

$$C_{out} = X · Y · \overline{C_{in}} + X · \overline{Y} · C_{in} + \overline{X} · Y · C_{in} + X · Y · C_{in}$$

Put n For Adder together and linked their Carry Ins and Carry Outs together can be a n-bit adder.

The first adder's $c_{in}$ should be 0.

### Comparitor(比较器)

For one bit comparitor

F, G, H

F(smaller than): 1, if X=1, Y=0; 0, otherwise

G(equal): 1, if (X=1, Y=1) OR (X=0, Y=0); 0, otherwise

H(greater than): 1, if X=0, Y=1; 0, otherwise

So:
$$F = X · \overline{Y}$$
$$G = X · Y + \overline{X} · \overline{Y}$$
$$H = \overline{X} · Y$$

## Analog(模拟)

It is a big problem: digital vs. analog

From digital to analog:

Sampling(采样) + Quantization(量化)

Sampling: Select samples with the same time interval. (Avoid infinity in time)

Quantization: For each sample point, approximate the amplitude/magnitude to finite precision.

## Digital Waveforms and Pulse Definitions

![1](Week1/1.jpg)
![2](Week1/2.jpg)

**clock** is a *basic timing signal* that is an example of a periodic wave. It is used to synchronized actions.

## Serial(串行) and Parallel(并行) Data

Data can be transmitted by either serial transfer or parallel transfer.

## Basic Logic Functions

AND:
![3](Week1/3.jpg)

OR:
![4](Week1/4.jpg)

NOT:
![5](Week1/5.jpg)

You can use the above three to design any logical functions.

## Some More Key Items

- Fixed-function Logic: A category of digital integrated circuits having functions that cannot be altered.
- Programmable logic: A category of digital integrated circuits capable of being programmed to perform specified functions.

