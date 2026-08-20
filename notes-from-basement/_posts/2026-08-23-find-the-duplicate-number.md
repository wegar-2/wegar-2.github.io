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

### Permutations Come To Mind...

The array of length $n+1$ that we are given is best viewed as mapping 
from the set $A = \{ 0, 1, 2, \dots, n \}$ into 
$B = \{1, 2, \dots, n\}$.

We know that 


### Minor Problem with Orbits


### Pigeonhole Principle


