---
layout: post
title: "Find The Duplicate Number - Why Does The Solution Work?"
date: 2026-08-23
category: notes-from-basement
---

### The Problem

Recall the Leetcode [Find the Duplicate Number Problem](https://leetcode.com/problems/find-the-duplicate-number/description/).
It is a classic use case for [Floyd's cycle dedection algorithm](https://cp-algorithms.com/others/tortoise_and_hare.html).

As it happens to be the case with many other Leetcode problems that 
have an interesting mathematical aspect, this one is rarely 
analyzed formally. And that's exactly what I want to provide here.

### Permutations Come To Mind

The array of length $n+1$ that we are given is best viewed as mapping 
from the set $A = \{ 0, 1, 2, \dots, n \}$ into 
$B = \{1, 2, \dots, n\}$.

The general case can be written down thus:

$$
\begin{array}{c|ccc}
n    & 0 & 1 & 2 & 3 & \cdots & n \\
\hline
f(n) & a_0 & a_1 & a_2 & a_3 &\cdots & a_n
\end{array}
$$

Note that any number except $0$ might be mapped to itself. 
Let's assume that the number $k \in B$ is the duplicate number that we are looking for.


### Problem with Orbits

Pondering various possibilities that arise we might notice that it is possible
for a cycle to arise in the transformation in a manner akin to cycles in the 
proper permutation - consider e.g. the following particular case:

$$
\begin{array}{c|ccc}
n    & 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 \\
\hline
f(n) & 1 & 2 & 3 & 2 & 4 & 6 & 7 & 5
\end{array}
$$

There are two closed cycles:
- 1-element cycle of $4$ into itself: $4 \rightarrow 4 \rightarrow \dots $
- 3-element cycle: $5 \rightarrow 6 \rightarrow 7 \rightarrow 5 \rightarrow \dots $

Note that what happens is that in such closed cycles that do not start at zero we 
cannot have two distinct numbers being mapped to the same number.  

For suppose it was otherwise. 

### Pigeonhole Principle

Suppose that we take the original mapping $f: A \rightarrow B$ and remove from
it all the closed cycles. 

We are then left with mapping: $f': A' \rightarrow B'$ such that $0 \in A'$.

The key to understanding why the search has to start at $0$ is the 


