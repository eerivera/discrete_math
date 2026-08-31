# Parse Trees for First-Order Logic

## Skills Addressed

* [F05 — Predicate Calculus: Syntax and Semantics](../../skills/Predicate_Calculus/F05.md)

A parse tree shows how a formula is constructed and makes the scope of every quantifier visible. Quantifier nodes have one child: the formula within the quantifier’s scope. Binary-connective nodes have two children, and a negation node has one child.

In this course, do not rely on a default precedence rule to determine the scope of a quantifier or the grouping of mixed binary operators. Use parentheses to specify the intended formula.

## Example 1: A quantifier with limited scope

Consider

$$
(\forall x\,\exists y\,P(x,y))\rightarrow\exists z\,P(z,x).
$$

The main connective is $\rightarrow$. The scope of $\forall x$ is only $\exists y\,P(x,y)$, so the occurrence of $x$ in $P(z,x)$ is free.

![Parse tree with the universal quantifier limited to the antecedent](../../skills/Predicate_Calculus/images/F05/scope-example-1.svg)

## Example 2: A quantifier with wider scope

Now consider

$$
\forall x\bigl((\exists y\,P(x,y))\rightarrow\exists z\,P(z,x)\bigr).
$$

Here the implication is inside the scope of $\forall x$. Both displayed occurrences of $x$ are bound.

![Parse tree with the universal quantifier governing the implication](../../skills/Predicate_Calculus/images/F05/scope-example-2.svg)

The two formulas have different parse trees and different meanings. Parentheses are part of the mathematical content, not merely decoration.

## Practice

Draw a parse tree for each formula. Then identify every bound and free variable occurrence.

1. $(\exists y\,\forall x\,P(x,y))\rightarrow\forall x\,\exists y\,P(x,y)$
2. $\exists x\bigl(P(x)\rightarrow\forall y\,\exists z(P(y)\wedge Q(y,z))\bigr)$
3. $(\exists x\,P(x))\rightarrow\forall y\,\exists z(Q(y,z)\wedge P(y))$
4. $\forall x\,\forall y\bigl((x<y)\rightarrow\exists z((x<z)\wedge(z<y))\bigr)$
