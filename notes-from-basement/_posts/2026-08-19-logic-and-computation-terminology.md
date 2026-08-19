---
layout: post
title: "(WiP) Logic and Computation - Clarifying the Very Basic Terminology"
date: 2026-08-19
category: notes-from-basement
---

## Logic and Computation - Clarifying (Some of) the Very Basic Terminology

### 1. Intro

In this post I am writing down a (hopefully) clarifying note that will help me 
put in place the basic terminology pertaining to computation and logic.

My humble hope is that the process of writing these things down will help me 
put things in the right order once and for all in my mind. 

Also, I have neither hope nor intention of standardizing the terminology in the pertinent 
literature - this is merely a note to self (or to whoever find him/herself
in similar impasse - please be mindful that you are using this note at 
your own risk as I am self-learner in both areas and have no formalized
education in both areas to prop up my case).

In my case the predicament has arisen due to my (unintentional) simultaneous 
reading of two excellent books - cf. [references](#reference): Ullman et 
al. classic(al) *Introduction* 
and Smith's  *Introduction*

Certain sections of these books deal with concepts that are related but, given
different authors and purposes, not easy to reconcile - at least on quick reading.


Let's start by taking the computational view.

### 2. The Computational Perspective

To keep length of this text manageable I am assuming that the cornerstone
of the broader story, i.e. definition of *Turing machine* (TM) is given.

First, we will need to define language of a Turing machine:

**Definition (language of a Turing Machine)**
Let $M = (Q, \Sigma, \Gamma, \delta, q_0, F, B)$ be a Turing machine. 
The set of strings $w \in \Sigma^*$ such that $q_0 w \vdash\alpha p \beta$ where
$p \in F$ is called the language of TM $L$ and it is denoted $L(M)$.

Thinking rather abstractly, we have the universe of the string being members
of the Kleene's closure before our eyes now. We take a string $w \in \Sigma^*$, 
feed it into the TM $L$ and let it run. When it so happens, that the machine 
enters an accepting state $p \in F$ we implicitly assume that it comfortable
stops operating - i.e. that it halts.

One is, however, justified in asking now about what happens when the machine 
just keeps running - regardless of whether 

Let's first look at the broader kind of TM languages, namely at:

**Definition (Recursively Enumerable Language)**
Consider a language $L \subset \Sigma^*$. $L$ is called 
*recursively enumerable* iff there exists a TM $L$ such that $L = L(M)$.

The key observation to make here is that RE language definition makes no demands
concerning what happens when $w \in \Sigma*$ that is fed into $M$ 
happens to be such that $w \notin L$.

Clearly, we would like to have some guarantee about what happens 
when we feed $L$ a word $w \notin L$: what if, having started it, we wait 
for a long time? Under RE lang we have no assurance of success - we do not 
want to find ourselves waiting for the proverbial Godot...

This (reasonable) concern is addressed by imposing a requirement on the 
behavior of the TM when we feed into it a word not in $L$. In order
to feel slightly more comortable we want to know that the machine would stop 
in such scenario - or more precisely: halt. However, we are justified in asking about 
*how* it might halt? Can it halt in any manner? Clearly, one can imagine
a trajectory such that the machine passes through an accepting state when 
processing. Even worse: the danger of it halting in an accepting state is 
looming! Luckily, this would contradiction with the earlier 
definition of the very language we are considering. 

Therefore, the following definition feels natural:

**Definition (Recursive Language)**
Language $L$ is called *recursive* iff there exists a TM $M$ such that:

(1) $ \forall w \in L$: $M$ accepts $w$

(2) $ \forall w \notin L$: $M$ halts, but never enters any accepting state when processing $w$

Brief terminological remark is in order here: I am assuming 
(following Ullman et al.) that the acceptance of the states means that the 
machine halts in an accepting state.

In other words, when dealing with a *recursive* language we have the comfort of 


### 3. The Logical Perspective

The key to my investigation from the vantage point of logic is the 
definition given by Smith 



### 4. Summary



<a id="reference"></a>
## References
1. J. Ullman, Hopcroft et al., *Introduction to Automate Theory*
2. P. Smith, **

