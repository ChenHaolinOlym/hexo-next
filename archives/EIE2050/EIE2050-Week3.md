---
title: EIE2050 Week3
tags:
  - EIE2050
  - Digital Logic and Systems
categories:
  - note
  - EIE2050
date: 2019-09-18 12:51:07
---

## Inverter

![1](/1.jpg)

It performs the NOT operation.

A group of inverters can be used to form the 1's complement of a binary number

## AND Gate

![2](/2.jpg)

In this course, the AND gate can have at most 4 inputs

### Mask

10100011 AND 00001111 = 00000011

00001111 is a mask.

The digit with mask 1 will stay the same, with mask 0 will always be 0.

## OR Gate

![3](/3.jpg)

In this course, the OR gate can have at most 4 inputs

## NAND Gate

![4](/4.jpg)

In hardware, it's more simple than AND Gate. Practically, an AND Gate is implemented by two NAND Gate, an OR Gate is implemented by three NAND Gate.

You can represent NOT, OR, AND with NAND Gate. So NAND Gate is called universal gate.

Inputs A | Inputs B | Output X
:-: | :-: | :-:
0 | 0 | 1
0 | 1 | 1
1 | 0 | 1
1 | 1 | 0

## NOR Gate

![5](/5.jpg)

You can represent NOT, OR, AND with NOR Gate. So NOR Gate is also called universal gate.

Inputs A | Inputs B | Output X
:-: | :-: | :-:
0 | 0 | 1
0 | 1 | 0
1 | 0 | 0
1 | 1 | 0

## XOR Gate

![6](/6.jpg)

X means exclusive. XOR--Exclusive-Or.

XOR Gate produces a HIGH output when both inputs are at *opposite* logic levels.

Inputs A | Inputs B | Output X
:-: | :-: | :-:
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 0

It's written as $X = \overline{A}B + A\overline{B}$ or $X = A \oplus B$

## XNOR Gate

![7](/7.jpg)

XNOR Gate produces a HIGH output when both inputs are at *same* logic levels.

Inputs A | Inputs B | Output X
:-: | :-: | :-:
0 | 0 | 1
0 | 1 | 0
1 | 0 | 0
1 | 1 | 1
