---
title: CSC3001 Week1
tags:
  - CSC3001
  - Discrete Mathematics
mathjax: true
categories:
  - note
  - CSC3001
date: 2019-09-03 13:45:06
---

## Problems in Computer Science

- Problem Modelling
- Model Analysis(feasibility, complexity, etc.)
- Design Algorithms
- Algorithm Analysis(efficiency, bugs, etc.)
- Problem Detection

## Discrete Mathematics

Discrete Mathematics is a collection of some topics in math.

## Topics discussed in class

- Logic and Proofs
- Number Theory
- Graph Theory
- Counting

## Propositional Logic

### Mathematical Proof

We need a rigorous system to prove mathematic theorems.

### Logic, Basic Operators

**Statement:** A statement is a sentence that is either *True* or *False*

**Logic Operators:** Logic operators are used to construct new statements from old statements.

Three main logic operators: "NOT", "AND", "OR"

*Notations:*  $$\lnot{} ::=NOT$$ $$\neg{}P = \overline{P}$$ $$\land{} ::= AND$$ $$\vee{} ::= OR$$

Some more logical operatrs:

exclusive-or: $\oplus$

p | q | $p\oplus{}q$
:-: | :-: | :-:
T | T | F
T | F | T
F | T | T
F | F | F

majority:

P | Q | R | M(P, Q, R)
:-: | :-: | :-: | :-:
T | T | T | T
T | T | F | T
T | F | T | T
T | F | F | F
F | T | T | T
F | T | F | F
F | F | T | F
F | F | F | F

### Using Simple Operators to Construct Any Operator

Take the example of the exclusive-or:

#### Idea 0: Guess and Check

$p\oplus{}q \equiv{} (p \land{} q) \vee{} \neg{}(p \vee{} q)$

**Logical Equivalence:** Two statements have the same *truth table*.

#### Idea 1: Look at Each True Row

p | q | $p\oplus{}q$
:-: | :-: | :-:
T | T | F
T | F | T
F | T | T
F | F | F

$(p \land{} \neg{}q) \vee{} (\neg{}p \land{} q)$

Only the second row *or* the third row is true that the input is true.

**So:**
$(p \land{} \neg{}q)$ is for second row.
$(\neg{}p \land{} q)$ is for third row.
and use "OR" $\vee{}$ to linked them.

**Look at the true rows and take the "or"**

#### Idea 2: Look at Each False Row

Almost the same thinking pattern as Idea 1

**Look at the false rows, negate and take the "and"**

### Logical Equivalence, DeMorgan's Law

#### DeMorgan's Law

$\neg{}(p \land{} q) \equiv{} \neg{}p \vee{} \neg{}q$
$\neg{}(p \vee{} q) \equiv{} \neg{}p \land{} \neg{}q$

#### Logical Rules

name | expression1 | expression2
:-: | :-: | :-:
Communicative Laws | $p \land{} q \equiv{} q \land{} p$ | $p \vee{} q \equiv{} q \vee{} p$
Associative Laws | $(p \land{} q) \land{} r \equiv{} p \land{} (q \land{} r)$ | $(p \vee{} q) \vee{} r \equiv{} p \vee{} (q \vee{} r)$
Distributive Laws | $p \land (q \vee r) \equiv (p \land q) \vee (p \land r)$ | $p \vee (q \land r) \equiv (p \vee q) \land (p \vee r)$
Identity Laws | $p \land{} t \equiv{} p$ | $p \vee{} c \equiv{} p$
Negation Laws | $p \vee{} \neg{}p \equiv{} t$ | $p \land{} \neg{}p \equiv{} c$
Double Negative Law | $\neg{}(\neg{}p) \equiv{} p$
Idempotent Laws | $p \land{} p$ | $p \vee{} p$
Universal Bound Laws | $p \vee{} t equiv{} t$ | $p land{} c \equiv{} c$
De Morgan's Laws | $\neg{}(p \land{} q) \equiv{} \neg{}p \vee{} \neg{} q$ | $\neg{}(p \vee{} q) \equiv{} \neg{}p \land{} \neg{} q$
Absorption Laws | $p \vee{} (p \land{} q) \equiv{} p$ | $p \land{} (p \vee{} q) \equiv{} p$
Negation of **t** and **c** | $\neg{}t \equiv{} c$ | $\neg{}c \equiv{} t$

**t** means "tautology" and **c** means "contradiction"

You can use those rules to simplify the statement.

#### Tautology, Contradiction

A tautology is a statement that is always true.

A contradiction is a statement that is always false.(negation of a tautology)

### Conditional Statement (if, if and only if)

### Arguments
