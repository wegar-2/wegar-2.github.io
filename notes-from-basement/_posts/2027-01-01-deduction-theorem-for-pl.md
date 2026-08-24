---
layout: post
title: "Deduction Theorem in KPL"
date: 2027-01-01
category: notes-from-basement
---

## Deduction Theorem in $KPL$

This is a proof of the deduction theorem for the $KPL$ system
(Kleene's Hilbert-style system for propositional logic) that
I summarize [here](https://wegar-2.github.io/notes-from-basement/2026/08/23/kleenes-hilbert-style-system-propositional-logic.html).
I am rewriting this proof for my own comprehension and to fill-in the missing 
case in the (Basis $T(1)$ step: one line deduction consisting of modus ponens on premises of the given deduction) in the Kleene's proof in *Introduction to Metamathematics* - cf. [references](#references)  


**Theorem (Deduction Theorem)** Consider the $KPL$ system. 
Let $\Gamma$ denote any set of formulae from $KPL$ (possibly empty).
Let $B, C$ be formulae in this system. 
Suppose that the deduction $\Gamma, B \vdash C$ holds. 
Then: $\Gamma \vdash B \rightarrow C$.

**Proof**: using meta-induction w.r.t. *length* of the given deduction
$\Gamma, B \vdash C$. 

Let $T(n)$ denote the metalinguistic
claim that the theorem holds for all derivations of length $n$.

Note: the following cases are allowed in the system considered
* *Case 1*: line in the deduction is one of the assumptions
* *Case 2*: line in the deduction is an instance of the axiom schemata
* *Case 3*: line in the deduction results from two of previous lines in the 
deduction by application of *modus ponens*

Basis $T(1)$: considering the three possible cases.

*Case 1*: 
If $C$ is one of the $\Gamma, B$. 
There are two possibilities: either $C$ is $B$ or $C$ is one of the $\Gamma$.

Let's consider the former possibility first, i.e. $B = C$. We need to show that $\Gamma \vdash C \rightarrow C$:

1. $C \rightarrow (C \rightarrow C)$ (instance of ax. sch. (1))
2. $(C \rightarrow (C \rightarrow C)) \rightarrow ((C \rightarrow ((C \rightarrow C) \rightarrow C)) \rightarrow (C \rightarrow C))$ (instance of ax. sch. (2))
3. $(C \rightarrow ((C \rightarrow C) \rightarrow C)) \rightarrow (C \rightarrow C)$ (modus ponens on 1., 2.)
4. $C \rightarrow ((C\rightarrow C) \rightarrow C)$ (instance of ax. sch. (1))
5. $C \rightarrow C$ (modus ponens on 4., 3.)

Let's consider the latter case now:
1. $C$ (assmptn. - in this case $C$ is one of the $\Gamma$s)
2. $C \rightarrow (B \rightarrow C)$ (ax. sch. (1))
3. $B \rightarrow C$ (modus ponens on 1., 2.)

*Case 2*: $C$ is an instance of an axiom schemata. 
The given deduction $\Gamma, B \vdash C$ is just:
1. $C$

We can write, then, the following deduction from just $\Gamma$:
1. $C$ (instance of an axiom schemata)
2. $C \rightarrow (B \rightarrow C)$ (instance of ax. sch. (1))
3. $B \rightarrow C$ (modus ponens on 1. and 2.)

*Case 3*: $C$ results from applying modus ponens to two formulae $P \rightarrow C, P$ 
which are two formulae from $\Gamma, B$.
In this scenario we can write the following deduction:
1. $P$ (assmptn.)
2. $P \rightarrow (B \rightarrow P)$ (instance of ax. sch. (1))
3. $B \rightarrow P$ (modus ponens on 1., 2.)
4. $P \rightarrow C$ (assmptn.)
5. $(P \rightarrow C) \rightarrow (B \rightarrow (P \rightarrow C))$ (instance of ax. sch. (1))
6. $B \rightarrow (P \rightarrow C)$ (modus ponens on 4., 5.)
7. $(B \rightarrow P) \rightarrow ((B \rightarrow (P \rightarrow C)) \rightarrow (B \rightarrow C))$ (instance of ax. sch. (2))
8. $(B \rightarrow (P \rightarrow C)) \rightarrow (B \rightarrow C)$ (modus ponens on 3., 7.)
9. $B \rightarrow C$ (modus ponens on 6., 8.)

Induction step $T(n) \implies T(n+1)$:
suppose that the theorem holds for deductions of length $n$. Consider
deduction $\Gamma, A \vdash B$ of length $n + 1$.
The last line of this deduction falls into one of the three cases - analogously
to the Basis step. Of these, cases 1 and 2 are straightforward.
 
I am only considering case 3 here: $B$ is obtained via *modus ponens* from
two of previous formulae $P, P \rightarrow B$.

The crucial observation here: since both: $P$ and $P \rightarrow C$
show up in the proof of the deduction $\Gamma, B \vdash C$ before line $n+1$, 
the inductive assumption can be applied to them. In other words 
we can assume that we have the proofs of statements:

1. $B \rightarrow P$ (inductive assumption applied to proof of $\Gamma, B \vdash P$)
2. $B \rightarrow (P \rightarrow C) $ (inductive assumption applied to proof of $\Gamma, B \vdash P$)

From now on, we use analogous device i.e. axiom schema 2. that allows for chaining
of arguments under common assumption:




<a id="reference"></a>
### References
1. Stephen C. Kleene, *Introduction to Metamathematics*, Ishi Press International, 2009 printing of 1952 edition
2. Stephen C. Kleene, *Mathematical Logic*, Dover Publications, 2002 unabridged republication of 1967 edition 
