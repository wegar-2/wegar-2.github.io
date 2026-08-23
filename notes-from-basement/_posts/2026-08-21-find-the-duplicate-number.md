---
layout: post
title: "Find The Duplicate Number - Why Does The Solution Work?"
date: 2026-08-21
category: notes-from-basement
---

### 1. Problem Statement

Recall the Leetcode [Find the Duplicate Number Problem](https://leetcode.com/problems/find-the-duplicate-number/description/).
It is a classic use case for [Floyd's cycle dedection algorithm](https://cp-algorithms.com/others/tortoise_and_hare.html).

### 2. Lots of Notational Fuss About Nothing
As it happens to be the case with many other Leetcode problems that 
have an interesting mathematical aspect, this one is rarely 
analyzed sufficiently formally for my liking. 
So what I am going to to here is go over the top with notation
and see where this takes me.

### 3. Notation
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

### 4. Example

It's always instructive to consider a specific case. Let $f$ be the mapping
define by the table:


$$
\begin{array}{c|ccc}
n    & 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 \\
\hline
f(n) & 1 & 2 & 3 & 2 & 4 & 6 & 7 & 5
\end{array}
$$

In this case $$A = \{ 0, 1, 2, \dots 7 \}$$, $$B = \{ 1, 2, \dots , 6 \}$$ and $d = 2$.

There are two closed ''cycles''':
- 1-element cycle of $4$ into itself: $4 \rightarrow 4 \rightarrow \dots $
- 3-element cycle: $5 \rightarrow 6 \rightarrow 7 \rightarrow 5 \rightarrow \dots $


### 5. Proof I: Straightforward Approach

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
\exists n_1, n_2 \in A: f(n_1) = f(n_2) = d
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

### 6. Proof II: A Different use of Pigeonhole Principle

Let's start anew. We want to show that the duplicate number will be found
if we start iterating from $0$.

Let $\Theta \subseteq A$ be the set of values of the sequence starting from $0$:

$$ 
\Theta = \{ n \in B : \exists l \in \mathbb{N}_{+}:n = f^{(l)}(0)  \} \cup\{ 0 \}  
$$

Define $$\Theta_{+} := \Theta - \{0\}$$.

Let: 

$$ 
| \Theta | = m \leq n
$$

Suppose that $d \notin \Theta$. We then have $m < n$. 

By the pigeonhole principle applied to $\Theta_{+}$ we have that $m - 1$
numbers are mapped to $m$ numbers: $m$ members of $\Theta$ are mapped to $\Theta_{+}$.

This contradicts the pigeonhole principle, hence the assumption that $0$ 
is in a different cycle has to be rejected.

And that's it, I convinced myself now.
