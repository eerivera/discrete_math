# Simplification of Predicate Calculus Formulas

## Skills Addressed

* [F07 — Predicate Calculus: Simplification Rules](../../skills/Predicate_Calculus/F07.md)

The truth-tree method is easiest to apply after formulas have been placed in negation normal form and existential quantifiers have been Skolemized. Most simplification steps preserve logical equivalence. Skolemization has a different guarantee: it preserves satisfiability while introducing new symbols.

## Rename bound variables first

Give different quantifiers different variable names. For example,

$$
\forall x\,\forall y\bigl(P(x,y)\rightarrow\exists x\,Q(x,y)\bigr)
$$

is clearer after renaming the existentially bound variable:

$$
\forall x\,\forall y\bigl(P(x,y)\rightarrow\exists z\,Q(z,y)\bigr).
$$

This is an **alpha-renaming**: it changes no free occurrences and preserves meaning.

## Eliminate derived connectives

Use the propositional equivalences

$$
A\rightarrow B\equiv\neg A\vee B,
$$

$$
A\oplus B\equiv(A\wedge\neg B)\vee(\neg A\wedge B),
$$

and

$$
A\leftrightarrow B\equiv(A\wedge B)\vee(\neg A\wedge\neg B).
$$

The parentheses are essential because these replacements contain mixed binary operators.

## Move negations inward

Use the propositional De Morgan laws and double-negation rule together with

$$
\neg\forall x\,F(x)\equiv\exists x\,\neg F(x)
$$

and

$$
\neg\exists x\,F(x)\equiv\forall x\,\neg F(x).
$$

For a finite domain $D=\{a,b,c\}$, the first rule mirrors ordinary De Morgan reasoning:

$$
\begin{aligned}
\neg\forall x\,F(x)
&\equiv\neg(F(a)\wedge F(b)\wedge F(c))\\
&\equiv\neg F(a)\vee\neg F(b)\vee\neg F(c)\\
&\equiv\exists x\,\neg F(x).
\end{aligned}
$$

A formula is in **negation normal form** when its only connectives are $\wedge$, $\vee$, and $\neg$, and every $\neg$ applies directly to an atomic formula.

## Move quantifiers only when permitted

If $x$ is not free in $B$, then each of the following is valid:

$$
(\exists x\,A(x))\vee B\equiv\exists x(A(x)\vee B),
$$

$$
(\forall x\,A(x))\wedge B\equiv\forall x(A(x)\wedge B).
$$

Related movement rules hold for the other connective/quantifier combinations over the nonempty domains used in this course. Always check that moving a quantifier will not capture a free variable.

A formula in **prenex form** has all quantifiers at the front. Prenex form can clarify dependencies, although a truth tree may be easier to read when some universal quantifiers remain near the formulas they govern.

## Skolemization

After moving negations inward, replace each existential variable with a fresh symbol:

* use a fresh constant if the existential quantifier has no universal-quantifier ancestors; and
* use a fresh function of the universally quantified variables on which the witness may depend otherwise.

For example,

$$
\exists x\,P(x)
$$

Skolemizes to $P(a)$ for a new constant $a$, while

$$
\forall x\,\exists y\,P(x,y)
$$

Skolemizes to

$$
\forall x\,P(x,f(x))
$$

for a new function $f$.

Use a different fresh symbol for each existential quantifier. Do not write $\equiv$ for a Skolemization step. The original and Skolemized formulas are in different languages and are not generally logically equivalent. They are **equisatisfiable**: the original formula has a model exactly when the Skolemized formula has a model in the expanded language.

## Complete example

Simplify

$$
\forall x\bigl((\forall y\,P(x,y))\rightarrow\exists z\,Q(x,z)\bigr).
$$

Eliminate the implication:

$$
\forall x\bigl(\neg\forall y\,P(x,y)\vee\exists z\,Q(x,z)\bigr).
$$

Move the negation inward:

$$
\forall x\bigl((\exists y\,\neg P(x,y))\vee\exists z\,Q(x,z)\bigr).
$$

Move the existential quantifiers outward. Neither variable occurs free in the other disjunct:

$$
\forall x\,\exists y\,\exists z\bigl(\neg P(x,y)\vee Q(x,z)\bigr).
$$

These steps are logical equivalences. Now Skolemize $y$ and $z$ with two fresh functions of $x$:

$$
\forall x\bigl(\neg P(x,f(x))\vee Q(x,g(x))\bigr).
$$

The last formula is equisatisfiable with the original.

## A second example

Simplify and Skolemize

$$
\neg\forall x\,\exists y\,R(x,y).
$$

First move the negation inward:

$$
\exists x\,\forall y\,\neg R(x,y).
$$

The existential quantifier has no universal ancestor, so use a fresh constant $a$:

$$
\forall y\,\neg R(a,y).
$$

The constant does not depend on $y$ because the choice of $x$ occurs before the universally quantified $y$.
