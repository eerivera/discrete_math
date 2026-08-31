# The Peano Axioms

## Skills Addressed

* [F05 — Predicate Calculus: Syntax and Semantics](../../skills/Predicate_Calculus/F05.md)
* [G02 — Predicate Calculus: Inference](../../skills/Predicate_Calculus/G02.md)

First-order Peano arithmetic describes the natural numbers

$$
\mathbb N=\{0,1,2,\ldots\}
$$

in a language containing equality, the constant $0$, the successor function $s$, addition, and multiplication.

With equality treated as logical equality, the non-induction axioms may be written as follows:

1. $\forall x\,(s(x)\ne0)$
2. $\forall x\,\forall y(s(x)=s(y)\rightarrow x=y)$
3. $\forall x\,(x+0=x)$
4. $\forall x\,\forall y(x+s(y)=s(x+y))$
5. $\forall x\,(x\cdot0=0)$
6. $\forall x\,\forall y(x\cdot s(y)=(x\cdot y)+x)$

The theory also includes an **induction schema**. For every first-order formula $\varphi(x)$ in the language, it has an axiom of the form

$$
\bigl(\varphi(0)\wedge\forall x(\varphi(x)\rightarrow\varphi(s(x)))\bigr)
\rightarrow
\forall x\,\varphi(x).
$$

It is a schema rather than one first-order sentence because there is one induction axiom for each suitable formula $\varphi$.

## A small derivation

Define $1=s(0)$ and $2=s(s(0))$. We can derive $1+1=2$ from the recursive addition axioms:

1. $s(0)+0=s(0)$ by axiom 3 with $x=s(0)$.
2. $s(0)+s(0)=s(s(0)+0)$ by axiom 4 with $x=s(0)$ and $y=0$.
3. Therefore $s(0)+s(0)=s(s(0))$ by substituting the equality from step 1 into step 2.

Thus $1+1=2$.

## A model-theoretic caution

The usual natural numbers form a model of these axioms, but first-order Peano arithmetic also has nonstandard models. This illustrates an important distinction: axioms constrain their models, but first-order sentences do not necessarily characterize one intended infinite structure up to isomorphism.
