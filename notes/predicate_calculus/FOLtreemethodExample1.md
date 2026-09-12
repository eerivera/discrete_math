# A Translation and Truth-Tree Example

## Skills Addressed

* [F06 — Predicate Calculus: Translation to/from English](../../skills/Predicate_Calculus/F06.md)
* [G02 — Predicate Calculus: Inference](../../skills/Predicate_Calculus/G02.md)

Consider this argument:

* Whenever one person has another as a close contact, the second has the first as a close contact.
* Every close contact of someone who tests positive is quarantined.
* Everyone has a close contact who is a soccer player.
* No soccer player is quarantined.
* Therefore, no one has tested positive.

We will translate the argument and prove it valid.

## 1. Choose a language

Let the domain be people, with:

* $C(x,y)$: $x$ has $y$ as a close contact;
* $P(x)$: $x$ tests positive;
* $S(x)$: $x$ is a soccer player; and
* $Q(x)$: $x$ is quarantined.

## 2. Translate the argument

* p1: $\forall x\,\forall y(C(x,y)\rightarrow C(y,x))$
* p2: $\forall x\,\forall y((P(x)\wedge C(x,y))\rightarrow Q(y))$
* p3: $\forall x\,\exists y(C(x,y)\wedge S(y))$
* p4: $\forall x(S(x)\rightarrow\neg Q(x))$
* conclusion: $\neg\exists x\,P(x)$

The formulas use parentheses to make every quantifier scope and mixed connective grouping explicit.

## 3. Simplify and Skolemize

The premises become:

* p1: $\forall x\,\forall y(\neg C(x,y)\vee C(y,x))$
* p2: $\forall x\,\forall y(\neg P(x)\vee\neg C(x,y)\vee Q(y))$
* p3: $\forall x(C(x,f(x))\wedge S(f(x)))$, where $f$ is fresh
* p4: $\forall x(\neg S(x)\vee\neg Q(x))$

Negate the conclusion:

$$
\neg\neg\exists x\,P(x)
\equiv
\exists x\,P(x)
\leadsto
P(a),
$$

where $a$ is a fresh constant.

The $\leadsto$ symbol marks Skolemization rather than logical equivalence.

## 4. Close the tree

Start with $P(a)$. Instantiate p3 at $x=a$ to get $C(a,f(a))$ and $S(f(a))$.

Instantiate p4 at $x=f(a)$. Its $\neg S(f(a))$ branch closes against $S(f(a))$. On the $\neg Q(f(a))$ branch, instantiate p2 with $x=a$ and $y=f(a)$. Its three alternatives contradict $P(a)$, $C(a,f(a))$, and $\neg Q(f(a))$, respectively.

![Closed truth tree for the close-contact argument](../../skills/Predicate_Calculus/images/G02/soccer-tree.svg)

Every branch closes, so the argument is valid.

Premise p1 is not needed for this proof. That is not an error: a valid argument may contain a redundant premise. Removing p1 leaves a valid argument.
