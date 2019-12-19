---
title: CSC3001 Week10
tags:
  - CSC3001
  - Discrete Mathematics
categories:
  - note
  - CSC3001
date: 2019-11-10 10:50:44
mathjax: true
---

Graph Matching

## Matching

Matching' goal is to "match" in a "good" way.

### Stable Matching

Given a matching *M* for the vertex set *V*, the pair (v,w) is unstable if

1. (v, w’) and (v’, w) are matched pairs in M, where v $\not=$ v’, w $\not=$ w’.
2. v prefers w rather than w’.
3. w prefers v rather than v’. 

**Stable Matching:** A stable matching is a matching with no unstable pair, and every item is matched.

**Stable Roommate Problem:**

- There are 2n people.
- There are n rooms, each can accommodate 2 people.
- Each person has a preference list of 2n-1 people.
- Find a stable matching (match everyone and no unstable pairs). 

To solve Stable Matching Problem is easier than solve Stable Roommate Problem, because we only need to satisfy one side.

There is always a stable matching in the stable matching problem.(Gale,Shapley[1962])

The proof is based on a Marrying Procedure.

#### Marrying Procedure

- Morning: boy propose to their favourite girl.
- Afternoon: girl rejects all but favourite.
- Evening: rejected boy writes off the girl.
- This procedure is then repeated until all boys propose to a different girl.

So what we need to check now is:

1. The procedure will terminate
2. Everyone is married
3. No unstable pairs

**Claim 1:** The procedure will terminate in at most $n^2$ days.

1. If every girl is proposed by at most one boy, then all girls are married (since #boys = #girls), so the procedure will terminate.
2. Otherwise, there must be a girl receiving more than one proposal.
3. She will reject at least one boy in this case. These boys will write off that girl from their lists, and propose to their next favourite girls.
4. There are n boys whose list has n girls, and at least one name will be written off each day. So the procedure will last for at most $n^2$ days. 

**Claim 2:** Everyone is married when the procedure ends.

**Proof** (by contradiction).

1. Suppose B is not married and his list is empty.
2. Then B was rejected by all girls.
3. A girl rejects a boy only if she already has a more preferable partner.
4. So every girl has her own partner.
5. That is, all girls are married, but some boys are not.
6. This implies boys are more than girls, a contradiction. 

**Claim 3:** There are no unstable pair.

**Case 1: G is the first choice for B:**

- Then B married to his most favourite.
- So B has no incentive to leave.

**Case 2: G is not B’s first choice:**

- If (B,G’) is unstable, then B prefers G’ than G.
- So G’ rejected B before.
- That is, G’ prefers her current partner than B.
- So G’ has no incentive to leave. 

So by **Claim 1**, **Claim 2** and **Claim 3**, the Gale-Shapley Theorem is proved.

#### More Questions

##### Uniqueness

Stable matching is not always unique when exists.

![image-20191112203045110](/image-20191112203045110.png)

##### Boys and Girls

- All boys get the best partners!
- All girls get the worst partners! 
- The marrying procedure will always choose the boy optimal one when situation like the above happens

### Bipartite Matching

#### Problem

**The Bipartite Marriage Problem:**

- There are n boys and n girls.
- Each boy/girl can only marry to some girls/boys.  

**Goal:** To maximize the number of matched pairs.

#### Graph Problem

A graph is **bipartite** if its vertex set can be partitioned into two subsets A and B so that each edge has one endpoint in A and the other endpoint in B.  

A **matching** is a subset of edges so that every vertex has degree at most one. 

#### Maximum Matching

**The bipartite matching problem:** Find a matching with the maximum number of edges.

A perfect matching is a matching that every vertex is matched (i.e. of degree 1).

**The perfect matching problem:** Is there a perfect matching? 

##### Some Notations

- Let S be a subset of vertices of a graph. (e.g. a bipartite graph)
- We denote the *neighbor set* of S by N(S) = { v | v is a neighbor of some vertex in S}. So |S| is the number of vertices in S, and |N(S)| is the number of neighbors of S. 

If |N(S)| < |S| for some S, then it is impossible to have a perfect matching. 

In other words, in order to have a perfect matching, a necessary condition is that for each subset S on either side, we must have |N(S)| $\geq$ |S|. 

#### Hall's Theorem

A bipartite graph G=(V,W;E) has a perfect matching if and only if |N(S)| ≥ |S| for each subset S of V and for each subset S of W.

#### Proof of Hall's Theorem

**Hall’s Theorem:** A bipartite graph G=(V,W;E) has a perfect matching if and only if |N(S)| ≥ |S| for every subset S of V and W.  

- If S = V, then |V| $\leq$ |N(V)| $\leq$ |W|.
- If S = W, then |W| $\leq$  |N(W)| $\leq$  |V|. 

So the theorem can be restated as:

**Hall’s Theorem:** A bipartite graph G=(V,W;E) with |V|=|W| has a perfect matching if and only if |N(S)| ≥ |S| for every subset S of V. 



