---
title: CSC3001 Week2
tags:
  - CSC3001
  - Discrete Mathematics
  - Sets
mathjax: true
categories:
  - note
  - CSC3001
date: 2019-09-10 13:33:17
---

## Set

### Basic Definitions

#### Definition

**Definition:** A set is an *unordered* collection of *distinct* objects.

Objects in a set is called *element* or *member*, and they are *contain* in the set.

#### Classical Sets

symbol | meaning
:-: | :-:
$Z$ | the set of all integers
$Z^{+}$ | the set of all positive integers
$Z^{-}$ | the set of all negative integers
$N$ | the set of all nonnegative integers
$R$ | the set of all real numbers
$Q$ | the set of all rational numbers
$C$ | the set of all complex numbers

#### Method to Define Set by Properties

${x \in A | P(x)}$ means that it is a set that its elements *x*, in A, such that x satisfies property P.
$|S|$ is defined as the number of elements contained in S.

#### Membership

$A \subseteq B$ $\leftrightarrow$ For any $x \in A$, $x \in B$
A = B $\leftrightarrow$ $A \subseteq B$ and $B \subseteq A$
$A \subset B$ $\leftrightarrow$ $A \subseteq B$ and $A \ne B$

### Operations on Sets

#### Basic Operation

Intersection: $A \cap B = {x \in U | x \in A \ and \ x \in B}$
Union: $A \cup B = {x \in U | x \in A \ or \ x \in B}$

$|A \cup B| = |A| + |B| - |A \cap B|$

difference: $A - B = {x \in U | x \in A \ and \ x \not\in B}$

$|A - B| = |A| - |A \cap B|$

complement: $\overline{A} = A^C = {x \in U | x \not\in A}

If $A \subseteq B$, then $\overline{B} \subseteq \overline{A}$

#### Union and Intersection of an Indexed Collection of Sets

$\underset{i=0}{\overset{n}{\cup}} A_i$ = {x $\in$ U | x $\in \ A_i$ for at least one i = 0, 1, 2, .., n}

$\underset{i=0}{\overset{\infin}{\cup}} A_i$ = {x $\in$ U | x $\in \ A_i$ for at least one nonnegative integer i}

$\underset{i=0}{\overset{n}{\cap}} A_i$ = {x $\in$ U | x $\in \ A_i$ for all i = 0, 1, 2, .., n}

$\underset{i=0}{\overset{\infin}{\cup}} A_i$ = {x $\in$ U | x $\in \ A_i$ for all nonnegative integers i}

#### Partitions of Sets

Disjoint: Two sets are disjoint if their intersection is empty.

Partition: A collection of nonempty sets ${A_1, A_2, ..., A_n}$ is a partition of A, where $A = A_1+ A_2+ ...+ A_n$ and they are pairwise disjoint.

#### Cartesian Products

$A \times B = {(a, b) | a \in A, b \in B}$

So: $|A_1 \times A_2 \times ... \times A_k| = |A_1| \times |A_2| \times ... \times |A_k|$

**Note:** (a, b) is ordered pair, means the ordering is *important*

### Set Identities

Name | Expression
:-: | :-:
Communicative Law | $A \cup B = B \cup A$ / $A \cap B = B \cap A$
Associative Law | $(A \cup B) \cup C = A \cup (B \cup C)$ / $(A \cap B) \cap C = A \cap (B \cap C)$
Distributive Law | $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$ / $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$
Identity Law | $A \cup \varnothing = A$ / $A \cap U = A$
Complement Law | $A \cup A^C = U$ / $A \cap A^C = \varnothing$
De Morgan's Law | $(A \cup B)^C = A^C \cap B^C$ / $(A \cap B)^C = A^C \cup B^C$
Set Difference Law | $A - B = A \cap B^C$

## First Order Logic

### Quantifiers

#### Predicates

Predicates are propositions (i.e. statements) with variables.

The truth of a predicate depends on the domain.

Universal Quantifier: $\forall x$: For *all* x
Existential Quantifier: $\exists y$: There *exists* some y

### Negation

$$\neg \forall xP(x) \equiv \exists x \neg P(x)$$
$$\neg \exists xP(x) \equiv \forall x \neg P(x)$$

### Multiple Quantifiers

### Order of Quantifiers

Order of quantifiers is very important.
You can change the order of two "forall"s and two "exists"s, but you can't change the order of "forall" and "exists".

### Arguments of Quantified Statements

#### Validity

A quantified argument (i.e. arugment with variables, quantifiers) is valid if the conclusion is true whenever the assumptions are true.

#### Universal Generalization

$$
\frac{a \rightarrow R(c)}{A \rightarrow \forall x .R(x)}
$$

providing c is independent of A