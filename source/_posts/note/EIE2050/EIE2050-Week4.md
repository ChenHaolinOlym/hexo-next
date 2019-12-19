---
title: EIE2050 Week4
tags:
  - EIE2050
  - Digital Logic and Systems
categories:
  - note
  - EIE2050
date: 2019-09-23 13:33:58
mathjax: true
---

## Boolean Algebra

In Boolean Algrbra, a variable is a symbol used to represent an action, a condition, or data. A single variable can only have a value of 1 or 0.

**Compplement:** The complementrepresents the inverse of a variable and is indicated with an overbar. Thus, the complement of $A$ is $\overline{A}$.
**Literal:** A literalis a variable or its complement.

### Boolean Addition

In Boolean Algebre, addition is equivalent to the OR operation.

We called it "OR", we never called it addition.

### Boolean Multiplication

In Boolean algebra, multiplication is equivalent to the AND operation. The product of literals forms a product term. The product term will be 1 only if all of the literals are 1.

We called it "AND", we never called it multiply.

### Operation Rules

#### Communicative Law

$$A+B = B+A$$
$$AB = BA$$

#### Associative Law

$$A + (B + C) = (A + B) + C$$
$$A(BC) = (AB)C$$

#### Distributive Law

$$AB + AC = A(B+C)$$

#### Rules of Boolean Algebra

1. A + 0 = A
2. A + 1 = 1
3. A · 0 = 0
4. A · 1 = A
5. A + A = A
6. A + $\overline{A}$ = 1
7. A · A = A
8. A · $\overline{A}$ = 0
9. $\overline{\overline{A}} = A$
10. A + AB = A
11. A + $\overline{A}$B = A + B
12. (A + B)(A + C) = A + BC

## Boolean Analysis of Logic Circuits

Writing the expression for each gate and combining the expressions according to the rules for Boolean Algebra.

### SOP And POS Forms

Boolean expressions can be written in the **sum-of-productsform (SOP)** or in the **product-of-sumsform (POS)**. In both forms, an overbar (not) cannot extend over more than one variable.

#### SOP Standard Form

Every variable in the domain must appear in each term. This form is useful for constructing truth tables or for implementing logic in PLDs.

#### POS Standard Form

Every variable in the domain must appear in each sum term of the expression.

### Karnaugh Maps(卡诺图)

The Karnaugh Map is also called K-map. It is a tool for simplifying combinational logic with 3 or 4 variables. For 3 variables, 8 cells are required($2^3$).

![1](1.jpg)

The map shown is for three variables labeled A, B, and C. Each cell represents one possible product term.
Each cell differs from an adjacent cell by only one variable.

