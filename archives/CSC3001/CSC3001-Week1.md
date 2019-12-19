---
title: CSC3001 Week1
tags:
  - CSC3001
  - Discrete Mathematics
  - Propositional Logic
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
Universal Bound Laws | $p \vee{} t \equiv{} t$ | $p \land{} c \equiv{} c$
De Morgan's Laws | $\neg{}(p \land{} q) \equiv{} \neg{}p \vee{} \neg{} q$ | $\neg{}(p \vee{} q) \equiv{} \neg{}p \land{} \neg{} q$
Absorption Laws | $p \vee{} (p \land{} q) \equiv{} p$ | $p \land{} (p \vee{} q) \equiv{} p$
Negation of **t** and **c** | $\neg{}t \equiv{} c$ | $\neg{}c \equiv{} t$

**t** means "tautology" and **c** means "contradiction"

You can use those rules to simplify the statement.

#### Tautology, Contradiction

A tautology is a statement that is always true.

A contradiction is a statement that is always false.(negation of a tautology)

### Conditional Statement (if, if and only if)

#### If-Then Statement

**If p the q/ p implies q:** $p \rightarrow q$

*p* is called the hypothesis; *q* is called the conclusion.

#### Logic Operator

$$\rightarrow ::= IMPLIES$$

P | Q | $P \rightarrow Q$
:-: | :-: | :-:
T | T | T
T | F | F
F | T | F
F | F | T

**Convention:** if we don’t say anything wrong, then it is not false, and thus true.

<p style="color: red;font-size: 24px">The above is the most important point</p>
#### Logical Equivalence

$p \rightarrow q \equiv$ ?

Also three ways to deal with it:

1. Truth Table
2. Logical Rules
3. Intuition

##### Truth Table

P | Q | $P \rightarrow Q$
:-: | :-: | :-:
T | T | T
T | F | F
F | T | T
F | F | T

Obviously, take the false row is easier.

$\therefore \neg (P \land \neg Q) \equiv \neg P \vee Q$

#### Negation of If-Then

$\neg (p \rightarrow q) \equiv$ ?

$$\neg (P \rightarrow Q)$$
$$\equiv \neg (\neg P \vee Q)$$
$$\equiv \neg \neg P \land \neg Q$$
$$\equiv P \land \neg Q$$

#### Contrapositive(逆否)

The contrapositive of "if p then q” is “if %\neg$ q then %\neg$ p".

**Fact:** A conditional statement is logically equivalent to its contrapositive.

*Proof with Logical Rules:* $P \rightarrow Q \equiv \neg P \vee Q \equiv Q \vee \neg P \equiv \neg Q \rightarrow \neg P$

#### If, Only If(Necessary AND Sufficient Condition)

$\leftrightarrow ::= IFF$

R if S means: **"if S then R"**, then S is sufficient condition for R

R only if S means: **"if R then S**", then S is a necessary condition for R

#### Necessary, Sufficient Condition

If A is necessary condition of B, then B is sufficient condition of A.

### Arguments

An argument is a sequence of statements.

All statements but the final one are called *assumptions* or *hypothesis*.
The final statement is called the *conclusion*.

An argument is valid if:
whenever all the assumptions are true, then the conclusion is true.

Valid argument not implies True conclusion
True conclusion implies Valid argument

#### Two Types of Valid Arguments

##### Assumptions and Conclusions Have Connection

Such argument should contain conditional statement.

If there exists conditions that makes the assumptions and conclusions to be true at the same time, the argument is a valid argument.

##### Assumptions and Conclusions Do not Have Connection

Whether the argument is valid or not have nothing to do with the assumptions.

Valid argument means true conclusion and vice versa.

#### Ways to Identify Valid Arguments

##### Tautology

An argument is valid iff $(P_{1} \land P_2 \land ... \land P_n) \rightarrow Q$ is tautology.

##### Contradiction

Set the conclusion to be False, is it possible that call hypothesis is True?

If it is possible, then it is an invalid argument; On the contrary, it is a valid argument.

#### Valid Argument Forms

Name | Expression A | Expression B
:-: | :-: | :-:
Modus Ponens | $p \rightarrow q$<br>$p$<br>$\therefore q$
Modus Tollens | $p \rightarrow q$<br>$\neg q$<br>$\therefore \neg p$
Generalization | $p$<br>$\therefore p \vee q$ | $q$<br>$\therefore p \vee q$
Speciallization | $p \land q$<br>$\therefore p$ | $p \land q$<br>$\therefore q$
Conjunction | $p$<br>$q$<br>$\therefore p \land q$
Elimination | $p \vee q$<br>$\neg q$<br>$\therefore p$ | $p \vee q$<br>$\neg p$<br>$\therefore q$
Transitivity | $p \rightarrow q$<br>$q \rightarrow r$<br>$ \therefore p \rightarrow r$
Proof by Division into Cases | $p \vee q$<br>$p \rightarrow r$<br>$q \rightarrow r$<br>$\therefore r$
Contradiction Rule | $\neg p \rightarrow c$<br>$\therefore p$

