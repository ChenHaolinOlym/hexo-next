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

**Input:** a sequence of n numbers < $a_1$, $a_2$,…, $a_n$> 

**Output:** a permutation (reordering) < $a’_1$, $a’2$,…, $a’_n$> of input such that $a’1 \leq a’2\leq…\leq a’n$ .

- Stored in arrays.

- The numbers are referred as keys.

- Associated with additional information (satellite data)

- Several ways to solve.

### Bubble Sort

Bubble sort and insertion sort has the same running time.

### Loop Invariant

A property of the loop:

- Initialization: true before the begin of loop
- Maintenance: if true before an iteration, then also true after it.
- Termination: when the loop stops, use the invariant to show the algorithm is correct
- Similar to the mathematical induction

### Insertion Sort

- Incremental Sorting Algorithm

- Start with an empty left hand
- Pick up one card and insert it into the correct position
- To find the correct position, compare it with each of the cards in the hand, from right to left
- The cards held in the left hand are sorted

#### Analysis of Insertion Sort

##### Best Case: The array is sorted

$T(n) = 1$

##### Worst Case: The array is in reverse order

$T(n) = \sum^n_{j=2}j = (\sum^n_{j=1}) - 1 = \frac{n(n+1)}{2} - 1$

T(n) = cost*times

Always consider the worse case

When comparing them, we only keep the higher order term.

##### Average Case of Insertion Sort

The worst case is about half of the worst case time, but still a quadratic of n.

### Recursion

- Self-reference
- Recursive function: based upon itself
- Solution of the whole problem is composed of solutions of sub-problems

#### Insertion Sort in Recursion

- Base Case: If array size is 1 or smaller, return.
- Recursively sort first n-1 elements
- Insert the element in the correct position in sorted array

### Devide and Conquer

**Divide** the problem into a number of subproblems

**Conquer** the subproblems by solving them recursively (further divide if not small enough).

**Combine** the subproblem solutions to give a solution to the original problem.

### Merge Sort

Based on **Devide and Conquer**.

Its worst-case running time has a lower order of growth rate than insertion sort.

Devide into smaller arrays, recursively devide, sort them, combine.

#### Merge

- Think of two piles of cards. 
- Each pile is sorted and placed face-up on a table with the smallest cards on top. 
- We will merge them into a single sorted pile.
- Basic idea
  - Choose the smaller of the two top cards
  - Remove it from its pile
  - Repeat

#### Imporvement

Need to check whether one of two arrays is empty

Low efficiency and not good implementation

Solution:
Put a special sentinel card at bottom
We use ∞,  which is guaranteed to lose to any other value.

#### Compare with Insertion Sort

- Compared to insertion sort (worst-case time is a quadratic of n), merge sort is faster. 

- On small inputs, insertion sort may be faster. But for large enough inputs, merge sort will always be faster.

### Analyzing Dibide and Conquer Algorithms

Suppose N is a power of 2
$$
\begin{equation}  
\left\{  
             \begin{array}{**lr**}  
             c & if \ n = 1 \\
             2T({\frac{n}{2}}) + cn & if \ n > 1
             \end{array}  
\right.  
\end{equation}  
$$
$T(1) = C$

$T(N) = 2T(\frac{N}{2})+CN$

$\frac{T(N)}{N} = \frac{T(\frac{N}{2})}{\frac{N}{2}}+C = ... = \frac{T(1)}{1} + C\log N$

So $T(N) = CN\log N + CN = O(N\log N)$