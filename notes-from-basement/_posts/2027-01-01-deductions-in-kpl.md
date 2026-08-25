---
layout: post
title: "Deductions in KPL, Theorem 5, $\S$ 26 of *ItM*"
date: 2026-08-26
category: notes-from-basement
---

# Deductions in $KPL$: Theorem 5, $\S$ 26 of *ItM*

This is proof of claims given in Theorem 5, $\S$26 of Kleene's 
*Introduction to Metamathematics* (*ItM*) - cf. [references](#references).

Working within [$KPL$](https://wegar-2.github.io/notes-from-basement/2026/08/23/kleenes-hilbert-style-system-propositional-logic.html).

Let $A$, $B$ and $C$ be formulae of $KPL$. 

As usual, intermixing metalinguistic operations and 
object language operations for brevity.

## I. Basic Claims

### 1. Principle of Identity
Claim: $\vdash A \rightarrow A$

Deduction: 

1. $A \rightarrow (A \rightarrow A)$ (instance of ax. sch. (1))
2. $(A \rightarrow (A \rightarrow A)) \rightarrow ((A \rightarrow ((A \rightarrow A) \rightarrow A)) \rightarrow (A \rightarrow A))$ (instance of ax. sch. (2))
3. $(A \rightarrow ((A \rightarrow A) \rightarrow A)) \rightarrow (A \rightarrow A)$ (modus ponens on 1., 2.)
4. $A \rightarrow ((A\rightarrow A) \rightarrow A)$ (instance of ax. sch. (1))
5. $A \rightarrow A$ (modus ponens on 4., 3.)

### 2. Chain Inference
Claim: $A \rightarrow B, B \rightarrow C \vdash A \rightarrow C$

The claim can be obtained from the deduction:

$A, A \rightarrow B, B \rightarrow C \vdash C $

by application of deduction theorem. 

Proof:
1. $A$ (given)
2. $A \rightarrow B$ (given)
3. $B$ (modus ponens on 1., 2.)
4. $B \rightarrow C$ (given)
5. $C$ (modus ponens on 3., 4.)


### 3. Interchange of Premises
Claim: $A \rightarrow (B \rightarrow C) \vdash B \rightarrow (A \rightarrow C)$

The claim can be obtained from the following deduction by two applications
of the deduction theorem:

$A, B, A \rightarrow (B \rightarrow C) \vdash C$

Proof: 
1. $A$ (given)
2. $A \rightarrow (B \rightarrow C)$ (given)
3. $B \rightarrow C$ (modus ponens on 1., 2.)
4. $B$ (given)
5. $C$ (modus ponens on 3., 4.)


### 4. Importation
Claim: $A \rightarrow (B \rightarrow C) \vdash A \wedge B \rightarrow C$

Proof 1 (straightforward):

The claim can be obtained from the following claim:

$A \wedge B, A \rightarrow (B \rightarrow C) \vdash C$

by single application of the deduction theorem.

1. $A \wedge B$ (given)
2. $A \wedge B \rightarrow A$ (ax. sch. (4))
3. $A$ (modus ponens on 1., 2.)
4. $A \wedge B \rightarrow B$ (ax. sch. (5))
5. $B$ (modus ponens on 3., 4.)
6. $A \rightarrow (B \rightarrow C)$ (given)
7. $B \rightarrow C$ (modus ponens on 3., 6.)
8. $C$ (modus ponens on 5., 7.)

Proof 2 (no use of shortcut provided by deduction theorem - all steps fully written out):

It is instructive to write out a direct proof of the claim without using the 
deduction theorem directly, but using the techniques that were used in the 
proof of the deduction theorem to see how they work in practice.

In the deduction that follows, I am mapping the steps of proof 1 to 
extended proof in which all the steps involved in the proof whose existence 
is assured by the deduction theorem.

Note that the deduction theorem is a metalinguistic theorem - i.e. a theorem
in the metalanguage about existence of a certain sequence of formulae in the
object language.

1.1. $A \wedge B \rightarrow A \wedge B$ (principle of identity)

2.1. $(A \wedge B \rightarrow A) \rightarrow (A \wedge B \rightarrow (A \wedge B \rightarrow A))$ (ax. sch. (1))

2.2. $A \wedge B \rightarrow A$ (ax. sch. (4))

2.3. $A \wedge B \rightarrow (A \wedge B \rightarrow A)$ (modus ponens on 2.1., 2.2.)

3.1. $(A \wedge B \rightarrow A \wedge B) \rightarrow ((A \wedge B \rightarrow (A \wedge B \rightarrow A)) \rightarrow (A \wedge B \rightarrow A))$ (ax. sch. (2))

3.2. $(A \wedge B \rightarrow (A \wedge B \rightarrow A)) \rightarrow (A \wedge B \rightarrow A)$ (modus ponens on 3.1., 1.1.) 

3.3. $A \wedge B \rightarrow A$ (modus ponens on 3.2., 2.3.)

4.1. $(A \wedge B \rightarrow B) \rightarrow (A \wedge B \rightarrow (A \wedge B \rightarrow B))$

4.2. $A \wedge B \rightarrow A$ (ax. sch. (5))

4.3. $A \wedge B \rightarrow (A \wedge B \rightarrow A)$ (modus ponens on 4.1., 4.2.)

5.1. $(A \wedge B \rightarrow A \wedge B) \rightarrow ((A \wedge B \rightarrow (A \wedge B \rightarrow A)) \rightarrow (A \wedge B \rightarrow A))$ (ax. sch. (2))

5.2. $(A \wedge B \rightarrow (A \wedge B \rightarrow A)) \rightarrow (A \wedge B \rightarrow A)$ (modus ponens on 5.1., 1.1.) 

5.3. $A \wedge B \rightarrow A$ (modus ponens on 5.2., 5.3.)

6.1. $$

Proof 3 (simplification of proof 2)

Notice that in proof 2 

1. $((A \wedge B) \rightarrow B) \rightarrow ( (A \wedge B \rightarrow (B \rightarrow C)) \rightarrow (A \wedge B \rightarrow C))$ (ax. sch. (2))
2. $A \wedge B \rightarrow B$ (ax. sch. (5))
3. $(A \wedge B \rightarrow (B \rightarrow C)) \rightarrow (A \wedge B \rightarrow C)$  (modus ponens on 1., 2.)
4. $(A \rightarrow (B \rightarrow C)) \rightarrow (A \wedge B \rightarrow (A \rightarrow (B \rightarrow C)))$ (ax. sch. (2))
5. $A \rightarrow (B \rightarrow C)$ (given)
6. $A \wedge B \rightarrow (A \rightarrow (B \rightarrow C))$ (modus ponens on 4., 5.)
7. $(A \wedge B \rightarrow (A \rightarrow (B \rightarrow C))) \rightarrow ( (A \wedge B \rightarrow ()) \rightarrow (A \wedge B \rightarrow C))$

### 5. Exportation
Claim: $A \wedge B \rightarrow C \vdash A \rightarrow (B \rightarrow C)$

Proof 1 (using deduction theorem):


Proof 2 (convoluted):

## II. Introductions

### 6. Introduction of a Conclusion

### 7. Introduction of a Premise

## III. Demonstrations of Implication

## IV. Contraposition

## V. Properties of Equivalence


<a id="reference"></a>
### References
1. Stephen C. Kleene, *Introduction to Metamathematics*, Ishi Press International, 2009 printing of 1952 edition
2. Stephen C. Kleene, *Mathematical Logic*, Dover Publications, 2002 unabridged republication of 1967 edition 
