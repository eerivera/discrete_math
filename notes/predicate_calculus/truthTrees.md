# The Truth-Tree Method for First-Order Logic

## Skills Addressed

* [G02 — Predicate Calculus: Inference](../../skills/Predicate_Calculus/G02.md)

To test whether premises $E_1,\ldots,E_n$ imply a conclusion $C$, construct a tree for

$$
E_1,\ldots,E_n,\neg C.
$$

If every branch closes, no interpretation makes all the premises True and the conclusion False, so the argument is valid.

## Preparation

Before applying tree rules:

1. rename bound variables so different quantifiers use different names;
2. eliminate $\rightarrow$, $\leftrightarrow$, and $\oplus$;
3. move negations inward;
4. Skolemize existential quantifiers with fresh symbols; and
5. move remaining universal quantifiers when useful.

After Skolemization, the formulas contain only universal quantifiers, $\wedge$, $\vee$, and literals.

## Ground terms and instantiation

A **ground term** is a term containing no variables. If the language contains constants $a,b$ and function symbols $f$ and $g$, then examples include

$$
a,\quad b,\quad f(a),\quad g(b),\quad f(g(a)),\ldots
$$

If a Skolemized problem has no constant symbols, introduce one fresh constant to represent an element of the nonempty domain.

The first-order tree method adds an instantiation rule:

> From $\forall x\,F(x)$, infer $F(t)$ for any ground term $t$.

A universal formula may be instantiated repeatedly with different ground terms. Choose instances that interact with literals already on the branch.

## Example: A valid argument

Use the premise

$$
\exists x\,\forall y\,P(x,y)
$$

and conclusion

$$
\forall y\,\exists x\,P(x,y).
$$

Skolemize the premise with a fresh constant $a$:

$$
\forall y\,P(a,y).
$$

Negate and simplify the conclusion:

$$
\begin{aligned}
\neg\forall y\,\exists x\,P(x,y)
&\equiv\exists y\,\forall x\,\neg P(x,y)\\
&\leadsto\forall x\,\neg P(x,b),
\end{aligned}
$$

where $b$ is another fresh constant. Instantiate the first formula with $y=b$ and the second with $x=a$. This gives both $P(a,b)$ and $\neg P(a,b)$, closing the only branch.

![Closed first-order truth tree](../../skills/Predicate_Calculus/images/G02/quantifier-valid.svg)

## Why invalid searches may continue

For the converse argument, the premise $\forall y\,\exists x\,P(x,y)$ Skolemizes to $\forall y\,P(f(y),y)$. The negation of $\exists x\,\forall y\,P(x,y)$ introduces another function and can generate endlessly nested ground terms. A blind instantiation search may therefore continue without closing.

The converse is invalid. A two-element countermodel is simpler: let $D=\{0,1\}$ and let $P(x,y)$ mean $x=y$. Each $y$ has a matching $x$, but no one $x$ matches every $y$.

## Reading a completed tree

* A branch closes only when it contains a literal and its exact negation, such as $P(a,f(a))$ and $\neg P(a,f(a))$.
* Similar-looking formulas with different terms do not form a contradiction.
* Every branch must close to prove validity.
* An open branch suggests a countermodel, but the proposed interpretation must still be checked against every premise and the negation of the conclusion.
