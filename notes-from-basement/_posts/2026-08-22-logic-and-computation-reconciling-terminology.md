---
layout: post
title: "(WiP) Logic and Computation - Reconciling (Some of) the Very Basic Terminology"
date: 2026-08-19
category: notes-from-basement
---

## (WiP) Logic and Computation - Reconciling (Some of) the Very Basic Terminology

### 1. Intro

In this post I am writing down a (hopefully) clarifying note that will help me 
put in place the basic terminology pertaining to computation and logic.

My humble hope is that the process of writing these things down will help me 
put things in the right order once and for all in my mind. 

Also, I have neither hope nor intention of standardizing the terminology in the 
pertinent literature - this is merely a note to self (or to whoever find 
him/herself in similar impasse - please be mindful that you are using this note 
at your own risk as I am self-learner in both areas and have no formalized
education to prop up my authority on the matters discussed).

In my case the predicament has arisen due to my (unintentional) simultaneous 
reading of two excellent (in my view, at least) books - cf. [references](#reference):

(1) Hopcroft, Motwani and Ullman's *Introduction to Automata Theory, ...* - chapters 8 and 9. 

(2) Peter Smith's *Introduction to Godel's Theorems* - chapters 3 and 4.

I will use abbreviations: *HMU* and *ITGT* when referring to, respectively, 
(1) and (2) in this text.

Certain sections of these books deal with concepts that are related but, given
different authors and purposes, not easy to reconcile - at least on quick reading.

So what I want to do seems to be an exercise in reverse-engineering of the underlying 
currents of thought that led to the definitions I am interested in. 

One can't help observing here, that although decoding of the great concepts 
is already a challange, the formulation of a great concept such as 
e.g. machine of Turing is many orders of magnitude further on the scale of
difficulty - a compression problems of its own kind, requiring you to 
put intuition into a limited number of words that then give rise to an ocean
of deductions.

Let's cut blabbering short here and get started by taking the computational view.

### 2. The Computational Perspective

To keep length of this text manageable I am assuming that the cornerstone
of the broader story, i.e. definition of *Turing machine* (TM) is given.

First, we will need to define language of a Turing machine:

**Definition (language of a Turing Machine)**
Let $M = (Q, \Sigma, \Gamma, \delta, q_0, F, B)$ be a Turing machine. 
The set of strings $w \in \Sigma^*$ such that $q_0 w \vdash\alpha p \beta$ where
$p \in F$ is called the language of TM $L$ and it is denoted $L(M)$.

Thinking rather abstractly, we have the universe of the string being members
of the Kleene's closure before our eyes now. 

We take a string: 
$$w\in \Sigma^*$$
feed it into the TM $L$ and let it run. 
When it so happens that the machine enters an accepting state $p\in F$ we 
implicitly assume that it *comfortably* stops operating - i.e. that it halts.

This brings us to the definition of the first, broad kind of TM languages, 
namely:

**Definition (Recursively Enumerable Language)**
Consider a language $L \subset \Sigma^*$. $L$ is called 
*recursively enumerable* iff there exists a TM $L$ such that $L = L(M)$.

The key observation to make here is that RE language definition makes no demands
concerning what happens when $w\in \Sigma^*$ that is fed into $M$ 
happens to be such that $w\notin L$.

Clearly, we would like to have some guarantee about what happens 
when we feed $L$ a word $w\notin L$: what if, having started it, we wait 
for a long time? Under RE lang we have no assurance of success - we do not 
want to find ourselves waiting for the proverbial Godot...

This (reasonable) concern is addressed by imposing a requirement on the 
behavior of the TM when we feed into it a word not in $L$. In order
to feel slightly more comfortable we want to know that the machine would stop 
in such scenario - or more precisely: halt. However, we are justified in asking about 
*how* it might halt? Can it halt in any manner? Clearly, one can imagine
a trajectory such that the machine passes through an accepting state when 
processing. Even worse: the danger of it halting in an accepting state is 
looming! Luckily, this would contradiction with the earlier 
definition of the very language we are considering. 

Therefore, the following definition feels natural:

**Definition (Recursive Language)**
Language $L$ is called *recursive* iff there exists a TM $M$ such that:

(1) $\forall w\in L$: $M$ accepts $w$

(2) $\forall w\notin L$: $M$ halts, but never enters any accepting state when processing $w$

Brief terminological remark is in order here: I am tacitly using the fact that 
acceptance of a state means that the machine *halts* in that accepting state.

In other words, when dealing with a *recursive* language we have the
certainty that the machine would halt - it is, so to speak, worth our wait in the 
sense that we know it will halt, even if the run will take a lot of time e.g.
the age of Universe.

So the picture that we have before us can be summarized as follows.

We pick an alphabet of input symbols, e.g. $\Sigma = B = \{0, 1\}$.

We cut out a slice $L$ of our (uncountable infinite binary) universe that 
might happend to be a RE lang or a recusive lang.

We then probe a word $w \in \Sigma^*$, e.g. $w=101100101101$, feed it into 
TM $M$ and watch what happens (possibly infinitely long).

This diagram (courtesy of ChatGPT) can be of a little help:
![diagram](../graphics/lang_euler_chart.png)

Having looked at the concepts (slightly) more formally, let's try to reconcile
them with the intuitive idea of a decidable problem. 

(Note: I am deliberately NOT discussing here how languages relate to 
problems - consult Ullman et al. for clarification if needed.)

If our problem is such, that its language $L$ happens to be *recursive*, 
we have the determinism in that we will (given enough time) get the answer 
if we feed it into the TM $M$ such that $L = L(M)$. Given the nature 
of the TM we might in such case say that we have an unquestionably clear
set of rules that we need to follow in order to get the answer i.e. 
we are dealing with an *algorithm*.

Let's summarize these considerations by putting down the following definitions:

**Definition(Decidable Problem)** If out problem $\Pi$ is *represented* by language $L$
and there exists a TM $M$ such that $L=L(M)$, we say that problem 
$\Pi$ us *decidable*.

**Definition (Undecidable Problem)** Problem $\Pi$ that is not decidable 
is called *undecidable*.

Taking stock of what we have discussed:
- we picked an alphabet $\Sigma$
- we then constructed all the strings that it permits i.e. $\Sigma^*$
- we considered what conditions a machine (Turing machine) should satisfy if we are to be ''comfortable'' about setting it in motion.

We noted, that we want the procedure to terminate regardless of outcome.
To quote HMU themselves (section 9.2.1, p. 349):

> We call a language $L$ *recursive* if $L = L(M)$ for some Turing 
> machine $M$ such that: 
> 1. If $w$ is in $L$, then $M$ (an therefore halts). 
> 2. If $w$ is not in $L$, then $M$ eventually halts, although it never enters 
> an accepting state. 
> A TM of this type corresponds to our informal notion of an ''algorithm'',
> a well-defined sequence of steps that always finishes and produces an answer.
> If we think of the language $L$ as a ''problem'', as will be the case 
> frequently, then problem $L$ is called *decidable* if it is a recursive
> language, and it is called *undecidable* if it is not a recursive langugage. 

So what we clearly see is that HMU clearly associate the notion of *algorithm*
with the certainty as to the occurrence of *halting*. Let's record this
observation thus:

$$
\boxed{ 
\text{algorithm for deciding }L 
\Longleftrightarrow L\text{ is recursive} 
\Longleftrightarrow L\text{ is decidable}}
$$


### 3. The Logical Perspective

*ITGT* is a book that deals with formal theories. The chapters that 
are of interest here introduce the relevant terminology. Given that 
*words* of the natural language are used to *name* these concepts, one might
get confused when jumping into the logical considerations having previously
studied computation. 

#### 3.1 Concerning the Notion of *Algorithm*

Let's take off by talking a little bit more about the notion of 
*algorithm*. In chatper 3 of *ITGT* we have the following passage 
(pp. 14-15):

> What is meant by talkin of an *effective* computational procedure? The core
> idea is that an effective computation involves (1) executing and *algorithm*
> 1. An algorithm is a set ot step-by-step instructions (instructions which are
> pinned down in advance of their execution), with each small step clearly
> specified in every detail (leaving no room for doubt as to what does and 
> what doesn't count as executing the step, and leaving no room for chance) 
> (...) In sum, we might say that executing an algorithm is something that can 
> be done by a suitable deterministic computing machine.
> 2. But there's more: plainly, if executing an algorithm is actually to compute 
a total function - i.e. a function which outputs a value for any relevant 
> input(s) - then the procedure must *terminate* in a finite number of steps
> for every input, and produce the right sort of output. Note, then, 
> it isn't part of the very idea of an algorithm that its execution always 
> terminates; so in general an algorithm might only compute a partial function.

So we clearly see that the *ITGT* and *HMU* do agree on the notion of
what is meant by *algorithm*.

#### 3.2 Effective Computability

We will start by quoting definition of *effectively computable function* from *ITGT*:

**Definition (Effectively Computable Function)** 
A total, one-place function  $f: \Delta \rightarrow \Theta$ is called 
*effectively computable* iff there is an *algorithm* which can be used to calculate,
in a finite number of steps, the value of the function for *any* $x \in \Delta$.

Let's simplify things a little bit here. 
Taking $\Sigma$ to be the binary alphabet i.e.: $\Sigma = B = \{0, 1\}$,
we have enough symbols to nicely represent the members of the set of 
natural numbers $\mathbb{N} = \{0, 1, 2, ... \}$:

$$
\begin{aligned}
0_{10} &= 0_{2} \\
1_{10} &= 1_{2} \\ 
2_{10} &= 10_{2} \\
3_{10} &= 11_{2} \\
4_{10} &= 100_{2} \\
5_{10} &= 101_{2} \\
&...
\end{aligned}
$$

Observe that we have an obvious bijection between set of non-empty binary 
strings $B^{+}$ and the set $\mathbb{N}$ - given $w \in B^{+}$:

$$
g(w) = \text{natural number whose binary representation is }w
$$

There is one minor glitch here - the empty string $\epsilon$. 
It can be easily handled by first mapping $B^{*}$ bijectively to 
$\mathbb{N}_{+} = \{1, 2, 3, ...\}$ and then $\mathbb{N}_{+}$ to
$\mathbb{N}$. The latter bijection is simply $p(n) = n - 1$ 
($p$ - predecessor).

The former is:
$$
\begin{aligned}
\epsilon & \longleftrightarrow (1\epsilon)_2 = 1_{10} \\
0 & \longleftrightarrow (10)_2 = 2_{10} \\
1 & \longleftrightarrow (11)_2 = 3_{10} \\
00 & \longleftrightarrow (100)_2 = 4_{10} \\
01 & \longleftrightarrow (101)_2 = 5_{10} \\
10 & \longleftrightarrow (110)_2 = 6_{10} \\
11 & \longleftrightarrow (111)_2 = 7_{10} \\
000 & \longleftrightarrow (1000)_2 = 8_{10} \\
&...
\end{aligned}
$$

which consists in taking consecutive binary strings in shortlex 
(*not* lexicographic!) order, 
adding prefix $1$ to each, and then treating it as binary representation 
of a natural number.

So now we have an isomorphism (actually, an order isomorphism since the 
shortlex ordering of the set of binary strings is retained by the usual 
inequality relation between natural numbers) between the natural numbers
and binary strings.

So if we now take the sets $\Delta, \Theta$ in the definition of the 
*effectively compuitable function* to be subsets of $\mathbb{N}$, we have 
established a connection with the computational perspective in which we viewed
(oversimplifying things enormously) the TMs as just some strings processors - 
in the case at hand: processors familiar binary strings.

#### 3.3 Effective Decidability


#### 3.4. Effectively Axiomatized Formal Theory
The investigations in *ITGT* revolve around the notion of 
*effectively axiomatized formal theory* (abbreviated henceforth: *EAFT*). 

I will not be discussing the nuts and bolts of the idea behind *EAFT*, 
but for the purpose of the later discussion we are going to need to state its
definition. Hence (cf. *ITGT*, p. 31):

**Definition (Effectively Axiomatized Formal Theory)** $T$ is an (interpreted)
*effectively axiomatized formal theory* if:
1. $T$ is couched in (interpreted) formalized language $(\mathcal{L}, \mathcal{I})$
such that it is *effectively decidable* what is a wff/sentence of $\mathcal{L}$, 
and what the truth-condition of any sentence is, etc.
2. it is *effectively decidable* which $\mathcal{L}$-wffs are axioms of $T$
3. $T$ has a proof system sich that it is *effectively decidable* whether an 
array of $\mathcal{L}$-wffs conforms to the proof-building rules
4. it is *effectively decidable* whether an array of $\mathcal{L}$-wffs
constitutes a proof from $T$'s axioms.

Note that *effective decidability* is present in every of the four points of 
the conditions. Let's briefly note that 

#### 3.5. Cornucopia of Properties (of an *EAFT*)


### 5. Reconciled Terminology


<a id="reference"></a>
## References
1. John E. Hopcroft, Rajeev Motwani, Jeffrey D. Ullman, 
*Introduction to Automata Theory, Languages and Computation, 3rd Ed.*, 
Pearson
2. Peter Smith, *An Introduction to Godel's Theorems, 2nd Ed.*, Logic Matters
