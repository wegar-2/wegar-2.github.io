---
layout: post
title: "Kleene's Hilbert-Style System of Propositional Logic"
date: 2026-08-24
category: notes-from-basement
---

## Kleene's Hilbert-Style System of Propositional Logic

### Intro

This is an overview of what I call *Kleene's Hilbert-style
system for propositional logic* for the purpose of these notes

The system is introduced and used in the two 
books on logic and metamathematics (cf [references](#references))
by [Stephen C. Kleene](https://en.wikipedia.org/wiki/Stephen_Cole_Kleene).

As I find the system particularly handy to work with, I want 
to have a reference to point to later on.

### Notation

Uppercase letters from the later part of the Latin alphabet ($P, Q, R, \dots$)
are used to denote atomic formulae, whereas the uppercase letter 
from the early part of that alphabet ($A, B, C, \dots$) 
are used to denote any formulae, 

The notation for logical operators used here differ from those used by Kleene:
- $\wedge$ - conjunction (Kleene uses $\&$)
- $\lor$ - disjunction
- $\rightarrow$ - conditional statement (Kleene uses $\supset$)
- $\neg$ - negation
- $\leftrightarrow$ - equivalence

### The System

Kleene's Hilbert-style system for propositional logic 
(henceforth referred to as $KPL$) consists of:
- thirteen axiom schemata
- a single deduction rule

#### Axiom Schemata

Let $A$, $B$ and $C$ be any propositional formulae (possibly atomic):

(1) $A \rightarrow (B \rightarrow A)$

(2) $(A \rightarrow B) \rightarrow ((A \rightarrow (B \rightarrow C)) \rightarrow (A \rightarrow C))$

(3) $A \rightarrow (B \rightarrow (A \wedge B))$

(4) $(A \wedge B) \rightarrow A$

(5) $(A \wedge B) \rightarrow B$

(6) $(A \rightarrow C) \rightarrow ((B \rightarrow C) \rightarrow ((A \lor B) \rightarrow C))$

(7) $A \rightarrow (A \lor B)$

(8) $B \rightarrow (A \lor B)$

(9) $(A \rightarrow B) \rightarrow ((A \rightarrow \neg B) \rightarrow \neg A)$

(10) $\neg \neg A \rightarrow A$

(11) $(A \rightarrow B) \rightarrow ((B \rightarrow A) \rightarrow (A \leftrightarrow B))$

(12) $(A \leftrightarrow B) \rightarrow (A \rightarrow B)$

(13) $(A \leftrightarrow B) \rightarrow (B \rightarrow A)$

Note: since these are all axiom *schemata*, we have in principle a (countable)
infinity of *axioms* (any axiom is an instance of an axiom schemata)

#### Deduction Rule - *Modus Ponens*

$$
\frac{A, A \rightarrow B}{B}
$$


### Axiom Schemata - Intuition

One has right to inquire why Kleene picked this selection of axiom schemata

### Example of a Deduction in $KPL$

To make things more tangible, let's look 


<a id="reference"></a>
### References
1. Stephen C. Kleene, *Introduction to Metamathematics*, Ishi Press International, 1952
2. Stephen C. Kleene, *Mathematical Logic*, Dover Publications, 1967