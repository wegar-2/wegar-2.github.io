---
layout: post
title: "Some Derived Rules for KPL"
date: 2026-08-24
category: notes-from-basement
---

## Some Derived Rules for $KPL$

Some metalinguistic results for [$KPL$](https://wegar-2.github.io/notes-from-basement/2026/08/23/kleenes-hilbert-style-system-propositional-logic.html).

Naming of the dereived rule consistent with Kleene's 
*Introduction to Metamathematics* - cf. [references](#references).

Note that in the deductions below I am deliberately intermixing 
the metalinguistic operations and object language operations for brevity.
Lack of precision is the cost of brevity.

### 1. Negation Introduction
Statement of the rule:

if $\Gamma, A \vdash C$ and $\Gamma, A \vdash \neg C$, then $\Gamma \vdash \neg A$.

Deduction:

1. $\Gamma \vdash A \rightarrow C$ (from $\Gamma, A \vdash C$ by deduction theorem)
2. $\Gamma \vdash A \rightarrow \neg C$ (from $\Gamma, A \vdash \neg C$ by deduction theorem)
3. $\Gamma$ (given)
4. $A \rightarrow C$ (deduction from 1., 3.)
5. $A \rightarrow \neg C$ (deduction from (2., 3.))
6. $(A \rightarrow C) \rightarrow ((A \rightarrow \neg C) \rightarrow \neg A)$ (ax. sch. (9))
7. $(A \rightarrow \neg C) \rightarrow \neg A$ (modus ponens on 4., 6.)
8. $\neg A$ (modus ponens on 5., 7.)

### 2. Proof By Cases

Statement of the rule:

if $\Gamma, A \vdash C$ and $\Gamma, B  \vdash C$, then $\Gamma, A \lor B \vdash C$

Deduction:

1. $\Gamma \vdash A \rightarrow C$ (from $\Gamma, A \vdash C$ by deduction theorem)
2. $\Gamma \vdash B \rightarrow C$ (from $\Gamma, B \vdash C$ by deduction theorem)
3. $\Gamma$ (given)
4. $A \rightarrow C$ (deduction using 1., 3.)
5. $B \rightarrow C$ (deduction using 2., 3.)
6. $(A \rightarrow C) \rightarrow ((B \rightarrow C) \rightarrow (A \lor B \rightarrow C))$ (ax. sch. (6))
7. $(B \rightarrow C) \rightarrow (A \lor B \rightarrow C)$ (modus ponens on 6., 4.)
8. $A \lor B \rightarrow C$ (modus ponens on 7., 5.)

We have now established that:

$\Gamma \vdash A \lor B \rightarrow C$

So:

$\Gamma, A \lor B \vdash C$


<a id="reference"></a>
### References
1. Stephen C. Kleene, *Introduction to Metamathematics*, Ishi Press International, 2009 printing of 1952 edition
2. Stephen C. Kleene, *Mathematical Logic*, Dover Publications, 2002 unabridged republication of 1967 edition 
