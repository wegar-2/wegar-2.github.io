---
layout: post
title: "Find The Duplicate Number - Why Does The Solution Work?"
date: 2026-08-23
category: notes-from-basement
---

### The Problem

Recall the Leetcode [Find the Duplicate Number Problem](https://leetcode.com/problems/find-the-duplicate-number/description/).
It is a classic use case for [Floyd's cycle dedection algorithm](https://cp-algorithms.com/others/tortoise_and_hare.html).

### Lots of Notational Fuss About Nothing
As it happens to be the case with many other Leetcode problems that 
have an interesting mathematical aspect, this one is rarely 
analyzed sufficiently formally for my liking. 
So what I am going to to here is go over the top with notation
and see where this takes me.

### A little bit of notation
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

Let $d \in B$ be the duplicate number that we are looking for.

### Straightforward Approach

Let's start at $0$ and just keep applying $f$ over and over again.

Let $(b_n)$ be the resulting sequence:
$$
b_0 = 0 \rightarrow f(0) \rightarrow f(f(0)) \rightarrow f(f(f(0))) \rightarrow \dots  
$$

We have:
$$
b_m = f^{(m)}(0)
$$

The set of values of $f$ is finite with $|A| = n + 1 < |B| = n$. 
By the pigeonhole principle we immediately get:

$$
\exists k, l \in A: f(k) = f(l) = d
$$

What we can say at this point is that $d$ exists, i.e. we validated that
the problem is correctly stated.

Moreover, after departing from $0$, we move from one member of 
the set $B$ to another, since $0$ is transformed into member of $B$ and then
any member of $B$ is mapped to another member of $B$: $\forall n \in B: f(n) \in B$.

Since $B$ is finite, if we just keep composing $f$ with itself, 
we will get the first pair of indexes $(i, j)$ with $0 < i < j$, such that:

$$
f^{(i)}(0) = b_i = b_j = f^{(j)}(0) =: d
$$

What we now have is that both: $b_{i-1}$ and $b_{j-1}$
have the same duplicate natural $d$ as their successor which is the
number we are looking for.

Observe that we have: $b_{i-1} \neq b_{j-1}$. Suppose this was not the case, i.e.
that we have $b_{i-1} = b_{j-1}$ - this would immediately contradict the 
assumption that $(i, j)$ is the first pair for which we have repetition.

### 

### Are we Really Sure that We're in the Right Orbit

One can stay skeptical and say the following. Suppose that we  

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


