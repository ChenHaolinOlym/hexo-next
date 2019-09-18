---
title: CSC3100 Week2
tags:
  - CSC3100
  - Data Structure
  - Algorithm
categories:
  - note
  - CSC3100
date: 2019-09-14 09:58:20
---

## Sorting Problem

### Bubble Sort

Bubble sort and insertion sort has the same running time.

### Loop Invariant

A property of the loop:

- Initialization: true before the begin of loop
- Maintenance: if true before an iteration, then also true after it.
- Termination: when the loop stops, use the invariant to show the algorithm is correct

### Insertion Sort

- Start with an empty left hand
- Pick up one card and insert it into the correct position
- To find the correct position, compare it with each of the cards in the hand, from right to left
- The cards held in the left hand are sorted

#### Analysis of Insertion Sort

T(n) = cost*times

Always consider the worse case

When comparing them, we only keep the higher order term.

#### Average Case of Insertion Sort

### Recursion

- self-reference
- recursive function: based upon itself
- Solution of the whole problem is composed of solutions of sub-problems

#### Insertion Sort in Recursion

- Base Case: If array size is 1 or smaller, return.
- Recursively sort first n-1 elements
- Insert the element in the correct position

### Devide and Conquer

Divide the problem into a number of subproblems

Conquer the subproblems by solving them recursively (further divide if not small enough).

Combine the subproblem solutions to give a solution to the original problem.

### Merge Sort

Based on Devide and Conquer.

Its worst-case running time has a lower order of growth rate than insertion sort.

Devide into smaller arrays, recursively devide, sort them, combine.

#### Merge

Think of two piles of cards. 
Each pile is sorted and placed face-up on a table with the smallest cards on top. 
We will merge them into a single sorted pile.
Basic idea
Choose the smaller of the two top cards
Remove it from its pile
Repeat

#### Imporvement

Need to check whether one of two arrays is empty

Low efficiency and not good implementation

Solution:
Put a special sentinel card at bottom
We use ∞,  which is guaranteed to lose to any other value.
