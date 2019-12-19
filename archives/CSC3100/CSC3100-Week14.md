---
title: CSC3100 Week14
tags:
  - CSC3100
  - Algorithm
  - Data Structure
mathjax: true
categories:
  - note
  - CSC3100
date: 2019-11-29 21:05:16
---

Dynamic Programming

## Definition

- An algorithm design technique (like divide and conquer)

- Used for **Optimization Problems**

  - A set of choices must be made to get an optimal solution
  - Find a solution with the optimal value (minimum or maximum)
  - There may be many solutions that lead to an optimal value 
  - Our goal: **find** **an optimal solution**
  
- Applicable when subproblems are **not** independent(Subproblems share subsubproblems)

## Procedure

1. **Understand** the structure of an optimal solution
2. **Recursively** define the optimal solution
3. **Compute** the value of an optimal solution in a bottom-up fashion
4. **Construct** an optimal solution from computed information (not always necessary)

## Examples

### Assembly Line Scheduling

Automobile factory with two assembly lines: 

- Each line has n stations: $S_{1,1}, \dots , S_{1,n}$ and $S_{2,1}, \dots , S_{2,n}$

- Corresponding stations $S_{1, j}$ and $S_{2, j}$ perform the same function but can take different amounts of time $a_{1, j}$ and $a_{2, j }$

- Entry times are: $e_1$ and $e_2$; exit times are: $x_1$ and $x_2$

- After going through a station, can either:

  - stay on same line at no cost, or 

  - transfer to other line: cost after $S_{i,j}$ is $t_{i,j}$ , $j = 1, \dots , n - 1$

![image-20191203190615682](image-20191203190615682.png)

**Problems:** 

What stations should be chosen from line 1 and which from line 2 in order to minimize the total time through the factory for one car?

#### Brute Force Solution

- Enumerate all possibilities of selecting stations

- Compute how long it takes in each case and choose the best one
- There are $2^n$ possible ways to choose stations, unacceptable when n is large

#### Dynamic Programming

##### Structure of the Optimal Solution

Let’s consider all possible ways to get from the starting point through station $S_{1,j}$

- We have two choices of how to get to $S_{1,j}$:
  - Through $S_{1,j-1}$, then directly to $S_{1,j}$
  - Through $S_{2,j-1}$, then transfer over to $S_{1,j}$ 

![image-20191204142651371](/image-20191204142651371.png)

###### Optimal Substructure

- **Generalization**: an optimal solution to the problem “find the fastest way through $S_{1, j}$” contains within it an optimal solution to subproblems: “find the fastest way through $S_{1, j - 1}$ or $S_{2, j – 1}$”.

- This is referred to as the **optimal substructure** property

- We use this property to construct an optimal solution to a problem from optimal solutions to subproblems

##### A Recursive Solution

- Define the value of an optimal solution in terms of the optimal solution to subproblems

- **Definitions: **

  - $f^*$ : the fastest time to get through the entire factory

  - $f_i[j]$ : the fastest time to get from the starting point through station $S_{i,j}$

  - $f^* = min (f_1[n] + x_1, f_2[n] + x_2)$

- **Base Case:** j = 1, i = 1, 2
  -  $f_1[1] = e_1 + a_{1,1}$
  - $f_2[1] = e_2 + a_{2,1}$
  
- **General Case:** $j = 2, 3, \dots, n$ and i = 1, 2

- Fastest way through $S_{1, j}$ is either:

  - the way through $S_{1, j - 1}$ then directly through $S_{1, j}$: $f_1[j - 1] + a_{1,j}$

  - the way through $S_{2, j - 1}$, transfer from line 2 to line 1, then through $S_{1, j}$: $f_2[j -1] + t_{2,j-1} + a_{1,j}$
  - So $f_1[j] = min(f_1[j - 1] + a_{1,j} ,f_2[j -1] + t_{2,j-1} + a_{1,j})$

- **Summary:** 

- $$
  \begin{equation}
  f_1[j]=\left\{
  \begin{aligned}
  e_1 + a_{1, 1} & , & \text{if j=1} \\
  \text{min}(f_1[j - 1] + a_{1,j} ,f_2[j -1] + t_{2,j-1} + a_{1,j}) & , & \text{if j} \geq 2 \\
  \end{aligned}
  \right.
  \end{equation}
  $$

- $$
  \begin{equation}
  f_2[j]=\left\{
  \begin{aligned}
  e_2 + a_{2, 1} & , & \text{if j=1} \\
  \text{min}(f_2[j - 1] + a_{2,j} ,f_1[j -1] + t_{1,j-1} + a_{2,j}) & , & \text{if j} \geq 2 \\
  \end{aligned}
  \right.
  \end{equation}
  $$

##### Computing the Optimal Solution

Solving top-down would result in exponential running time.

For j $\geq$ 2, each value $f_i[j]$ depends only on the values of $f_1[j – 1]$ and $f_2[j - 1]$

###### Bottom-Up Approach

- First find optimal solutions to subproblems

- Find an optimal solution to the problem from the subproblems

- Use Bottom-Up Approach can compute the optimal solution in O(n)

##### Construct an Optimal Solution

Look back from Top to Bottom to find a path then construct the optimal solution.

### Matrix-Chain Multiplication

**Problem**: given a sequence $<A_1, A_2, \dots , A_n>$, compute the product: $A_1 \cdot A_2 \dots A_n$

Matrix compatibility:
$$
\begin{align}
C = A \cdot B & & C=A_1 \cdot A_2 \dots A_i \cdot A_{i+1} \dots A_n \\
col_A = row_B & & col_i = row_{i+1} \\
row_C = row_A & & row_C = row_{A_1} \\
col_C = col_B & & col_C = col_{A_n} \\
\end{align}
$$

- In what order should we multiply the matrices?
- We can parenthesize the product to get the order in which matrices are multiplied
- We should choose the order in which we multiply the matrices has a significant impact on the cost of evaluating the product
- The order can make a huge difference in the time cost.
- As the above example, it's also inefficient to use brute force solution as the number of paranthesizations grows as $\Omega(2^n)$, because $P(n) = \left\{\begin{align}1&&n=1 \\ \sum^{n-1}_{k=1} p(k)p(n-k)&&n \geq 2\end{align}\right.$

#### Structure of the Optimal Solution

**Notation:** $A_{i\dots j} = A_i A_{i+1} \dots A_{j}, i \leq j$

So we can easily get that: $A_{i\dots j} = A_{i\dots k} A_{k+1\dots j}$

##### Optimal Structure

- The parenthesization of the “prefix” $A_{i\dots k}$ must be an optimal parenthesization

- If there were a less costly way to parenthesize $A_{i\dots k}$ , we could substitute that one in the parenthesization of $A_{i\dots j}$  and produce a parenthesization with a lower cost than the optimum $\Rightarrow$ contradiction!

- An optimal solution to an instance of the matrix-chain multiplication contains within it optimal solutions to subproblems

#### A Recursive Solution

**Subproblem:** determine the minimum cost of parenthesizing  $A_{i\dots j} = A_i A_{i+1} \dots A_j$  for $1 \leq i \leq j \leq n$

- Let m[i, j] = the minimum number of multiplications needed to compute $A_{i…j}$

  - full problem ($A_{1\dots n}$): m[1, n]

  - i = j: $A_{i\dots i}$ = Ai $\Rightarrow$ m[i, i] = 0, for i = 1, 2, …, n

- Assume that the optimal parenthesization splits the product $A_i A_{i+1} \dots A_j$ at k ($i \leq k < j$)

- So $[i, j] = m[i, k] + m[k+1, j] + p_{i-1}p_kp_j$

- $$
  \begin{equation}
  m[i, j]=\left\{
  \begin{aligned}
  0 & , & \text{if i=j} \\
  \min_{i \leq k < j}\{m[i, k] + m[k+1, j] + p_{i-1}p_kp_j\} & , & \text{if i < j} \\
  \end{aligned}
  \right.
  \end{equation}
  $$

#### Computing the Optimal Costs

Computing the optimal solution recursively takes exponential time, and same subproblems will be computed for multiple times.

**Idea:** fill in m such that it corresponds to solving problems of increasing length

Take an example: 

![image-20191204183250701](/image-20191204183250701.png)

##### Memoization

- Top-down approach with the efficiency of typical dynamic programming approach

- Maintaining an entry in a table for the solution to each subproblem
  - **memoize** the inefficient recursive algorithm

- When a subproblem is first encountered its solution is computed and stored in that table

- Subsequent “calls” to the subproblem simply look up that value

##### Dynamic Programming vs. Memoization

- Advantages of dynamic programming
  - No overhead for recursion

- Advantages of memoized algorithms
  - Each programming
  - Some subproblems do not need to be solved

#### Summary

- Both the dynamic programming approach and the memoized algorithm can solve the matrix-chain multiplication problem in $O(n^3)$

- Both methods take advantage of the overlapping subproblems property

- There are only $\Theta(n^2)$ different subproblems 
  - Solutions to these problems are computed only once

- Without memoization the natural recursive algorithm runs in exponential time

## Elements

### Optimal Substructure

- An optimal solution to a problem contains within it optimal solutions of subproblems

- Optimal solution to the entire problem is build in a bottom-up manner from optimal solutions of subproblems

### Overlapping Subproblems

- If a recursive algorithm revisits the same subproblems over and over $\Rightarrow$ the problem has overlapping subproblems

### Parameters of Optimal Substructure

- How many subproblems are used in an optimal solution for the original problem
  - Assembly line: One subproblem (the line that gives best time)
  - Matrix multiplication: Two subproblems (subproducts $A_{i\dots k}$, $A_{k+1 \dots j}$)

- How many choices we have in determining which subproblems to use in an optimal solution
  - Assembly line: Two choices (line 1 or line 2)
  - Matrix multiplication: j - i choices for k (splitting the product)

- The running time of a DP algorithm depends on two factors:
  - Number of subproblems overall
  - How many choices we look at for each subproblem
  - Assembly line
    - $\Theta (n)$ subproblems (n stations)
    - 2 choices for each subproblem
    - $\Theta (n)$ overall
  - Matrix multiplication:
    - $\Theta (n^2)$ subproblems ($1 \leq i \leq j \leq n$)
    - At most n-1 choices
    - $\Theta (n^3)$ overall

## Longest Common Subsequence

### Definition

Given two sequences:

 $X = <x_1, x_2, \dots, x_m>$

 $Y = <y_1, y_2, \dots, y_n>$

find a maximum length common subsequence (LCS) of X and Y

**Subsequence** means that elements in it are in order but not necessary in consecutive order.

### Applications

- Sequence comparison among species

### Brute-Force Solution

- For every subsequence of X (length m), check whether it’s a subsequence of Y (length n)

- There are $2^m$ subsequences of X to check

- Each subsequence takes $\Theta(n)$ time to check
  - scan Y for first letter, from there scan for second, and so on

- Running time: $\Theta(n2^m)$

### Optimal Solution

#### Structure of the Optimal Solution

- If the last element is equal
  - Include one element into the common sequence and solve the resulting subproblem
  - ![image-20191204185248990](/image-20191204185248990.png)
- If the last element is not equal
  - Exclude an element from a string and solve the resulting subproblem
  - ![image-20191204185316577](/image-20191204185316577.png)

##### Notations

- Given a sequence $X = <x_1, x_2, \dots , x_m>$ we define the i-th prefix of X, for i = 0, 1, 2, …, m: $X_i = <x_1, x_2, \dots , x_i>$

- c[i, j] = the length of a LCS of the sequences $X_i = <x_1, x_2, \dots , x_i>$ and $Y_j = <y_1, y_2, \dots , y_j>$

#### A Recursive Solution

##### Case 1: the last element is equal

$x_i = y_j$

- $c[i, j] = c[i - 1, j - 1] + 1$

- Append $x_i = y_j$ to the LCS of $X_{i-1}$ and $Y_{j-1}$

- Must find a LCS of $X_{i-1}$ and $Y_{j-1}$

##### Case 2: the last element is not equal

$x_i \not= y_j$

- $c[i, j] = \max\{ c[i - 1, j], c[i, j-1]\}$
- Must solve two subproblems
  - find a LCS of $X_{i-1}$ and $Y_j$
  - find a LCS of $X_i$ and $Y_{j-1}$

##### Overlapping Subproblems

- To find an LCS of X and Y
  - we may need to find the LCS between X and $Y_{n-1}$ and that of $X_{m-1}$ and Y
  - Both the above subproblems has the subproblem of finding the LCS of $X_{m-1}$ and $Y_{n-1}$

- Subproblems share subsubproblems

#### Computing the length of the LCS

$$
\begin{equation}
c[i, j]=\left\{
\begin{aligned}
0 & , & \text{if i=0 or j=0} \\
c[i-1, j-1] + 1 & , & \text{if }x_i = y_j \\
\max(c[i, j-1], c[i-1, j]) & , & \text{if }x_i \not= y_j \\
\end{aligned}
\right.
\end{equation}
$$

##### Additional Information

![image-20191204190932349](/image-20191204190932349.png)

#### Constructing a LCS

- Start at b[m, n] and follow the arrows

- When we encounter a “$\nwarrow$“ in b[i, j] $\Rightarrow$ $x_i = y_j$  is an element of the LCS 

#### Improving the Code

- If we only need the length of the LCS
  - LCS-LENGTH works only on two rows of c at a time
    - The row being computed and the previous row

- We can reduce the asymptotic space requirements by storing only these two rows

## The Shortest Path

