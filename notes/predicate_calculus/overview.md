# Overview of the Predicate Calculus

## Skills Addressed

* [F05 — Predicate Calculus: Syntax and Semantics](../../skills/Predicate_Calculus/F05.md)
* [F06 — Predicate Calculus: Translation to/from English](../../skills/Predicate_Calculus/F06.md)

First-order logic, also called the predicate calculus, extends propositional logic with objects, predicates, functions, variables, and quantifiers. It is expressive enough to formalize a large portion of ordinary mathematics.

## First-order languages

A first-order language specifies:

* predicate symbols with fixed arities, such as unary $P$ or binary $Q$;
* function symbols with fixed arities, such as unary $f$ or binary $+$;
* constant symbols, such as $a$ or $0$;
* variables, such as $x,y,z$;
* the connectives $\neg,\wedge,\vee,\rightarrow,\leftrightarrow,\oplus$; and
* the quantifiers $\forall$ and $\exists$.

Variables and constants are **terms**. If $f$ is a unary function symbol and $t$ is a term, then $f(t)$ is also a term. If $Q$ is a binary predicate symbol and $s,t$ are terms, then $Q(s,t)$ is an atomic formula.

Larger formulas are built from atomic formulas with connectives and quantifiers. In this course, parenthesize formulas so the grouping of mixed binary operators and the scope of each quantifier are explicit.

## Interpretations

The symbols of a first-order language have no fixed meaning until an **interpretation** supplies:

* a nonempty domain $D$;
* an element of $D$ for each constant symbol;
* a function on $D$ of the correct arity for each function symbol; and
* a relation on $D$ of the correct arity for each predicate symbol.

For example, in an interpretation of integer arithmetic:

* $D=\mathbb Z$;
* $0$ denotes the integer zero;
* $+$ denotes integer addition; and
* $<$ denotes the usual less-than relation on integers.

Under that interpretation, $\forall x\,(x<x+1)$ is True, while $\exists x\,\forall y\,(y<x)$ is False because the integers have no largest element.

An interpretation is a **model** of a sentence, or a set of sentences, when it makes every sentence True.

## Bound and free variables

In

$$
\forall x\bigl(P(x)\rightarrow Q(x,y)\bigr),
$$

the occurrences of $x$ are bound by $\forall x$, but the occurrence of $y$ is free. A formula with no free variables is a **sentence**. An interpretation determines the truth value of a sentence. A formula with free variables also needs values assigned to those variables.

## Quantifier order

The formulas

$$
\forall x\,\exists y\,Q(x,y)
$$

and

$$
\exists y\,\forall x\,Q(x,y)
$$

generally mean different things. In the first, the witness for $y$ may depend on $x$. In the second, one value of $y$ must work for every $x$.

For example, over the integers, $\forall x\,\exists y\,(x<y)$ is True: choose $y=x+1$. But $\exists y\,\forall x\,(x<y)$ is False: no integer is larger than every integer.

## Mathematical translations

Over the integers, “$d$ divides $n$” can be written as

$$
\exists k\,(n=d k).
$$

“Every two distinct integers are comparable” can be written as

$$
\forall x\,\forall y\bigl((x\ne y)\rightarrow((x<y)\vee(y<x))\bigr).
$$

“There is an integer larger than every integer” can be written as

$$
\exists x\,\forall y\,(y<x).
$$

This last expression is a well-formed sentence even though it is False in the usual interpretation of integer arithmetic. Syntax asks whether an expression is a formula; semantics asks what that formula means and whether it is True in an interpretation.
