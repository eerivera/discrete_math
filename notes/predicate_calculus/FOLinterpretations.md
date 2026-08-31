# Interpretations in First-Order Logic

## Skills Addressed

* [F05 — Predicate Calculus: Syntax and Semantics](../../skills/Predicate_Calculus/F05.md)

An interpretation for a first-order language specifies:

* a nonempty domain $D$;
* an element of $D$ for each constant symbol;
* a function on $D$ of the correct arity for each function symbol; and
* a relation on $D$ of the correct arity for each predicate symbol.

Once these meanings are fixed, we can evaluate every sentence in the language.

## Example 1: A sentence without quantifiers

Use the usual interpretation of integer arithmetic, extended by $a=4$, $b=7$, and $c=0$. Evaluate

$$
(a+b<c)\wedge((b\le c)\rightarrow(a>c)).
$$

Substitute the values of the constants:

$$
(4+7<0)\wedge((7\le0)\rightarrow(4>0)).
$$

The atomic formulas have values False, False, and True, respectively. Therefore,

$$
\text{False}\wedge(\text{False}\rightarrow\text{True})
\equiv
\text{False}\wedge\text{True}
\equiv
\text{False}.
$$

## Example 2: Quantifiers over a finite domain

Let $D=\{1,2,3,4\}$ and interpret $Q(x,y)$ by this table:

| $Q(x,y)$ | $y=1$ | $y=2$ | $y=3$ | $y=4$ |
|:---:|:---:|:---:|:---:|:---:|
| $x=1$ | F | F | T | F |
| $x=2$ | F | T | T | T |
| $x=3$ | T | T | T | T |
| $x=4$ | F | T | F | T |

1. $\forall x\,\exists y\,Q(x,y)$ is **True** because every row contains a `T`.
2. $\exists y\,\forall x\,Q(x,y)$ is **False** because no column contains only `T` values.
3. $\forall y\,\exists x\,Q(x,y)$ is **True** because every column contains a `T`.
4. $\exists x\,\forall y\,Q(x,y)$ is **True** because row $x=3$ contains only `T` values.
5. $\forall x\,\forall y\,\neg Q(x,y)$ is **False**; for example, $Q(1,3)$ is True.
6. $\forall x\,\neg\forall y\,Q(x,y)$ is **False** because $Q(3,y)$ is True for every $y$.
7. $\neg\forall x\,\forall y\,Q(x,y)$ is **True**; for example, $Q(1,1)$ is False.

Rows are useful for formulas beginning with a quantifier over $x$, while columns are useful for formulas beginning with a quantifier over $y$.

## Example 3: Functions and predicates

Use the usual interpretation of integer arithmetic, and let:

* $f(x)=x+1$ and $g(x)=x+1$;
* $a=10$ and $b=20$; and
* $P(x,y)$ mean $x<y$.

Evaluate

$$
\neg P(g(a),a)\wedge P(a,f(a)).
$$

Substitution gives

$$
\neg(11<10)\wedge(10<11),
$$

which is True.

The sentence

$$
\forall x\bigl(\neg P(g(x),x)\wedge P(x,f(x))\bigr)
$$

is also True because, for every integer $x$, $x+1<x$ is False and $x<x+1$ is True.

## More practice with answers

Under the same interpretation:

1. $P(a,b)\rightarrow P(g(a),f(b))$ is **True**: $10<20$ and $11<21$.
2. $\exists x(P(a,x)\wedge P(x,a))$ is **False**: no integer is both greater than and less than $10$.
3. $\forall x\,\exists y\,P(x,y)$ is **True**: choose $y=x+1$.
4. $\exists x\,\forall y\,P(x,y)$ is **False**: taking $y=x$ would require $x<x$.
5. $\forall x\,\forall y((P(x,y)\vee P(y,x))\rightarrow(P(x,y)\oplus P(y,x)))$ is **True**. When $x\ne y$, exactly one of $x<y$ and $y<x$ holds; when $x=y$, the implication’s antecedent is False.
