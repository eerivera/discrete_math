# Applied Translation Examples

## Skills Addressed

* [F06 — Predicate Calculus: Translation to/from English](../../skills/Predicate_Calculus/F06.md)

Let the domain $D$ be a group of people, with:

* $S(x)$: $x$ has COVID;
* $F(x)$: $x$ has a fever;
* $C(x,y)$: $x$ is a close contact of $y$;
* $R(x,y)$: $x$ and $y$ are roommates;
* $V(x)$: $x$ is vaccinated; and
* $I(x)$: $x$ has influenza.

The order of the arguments in $C(x,y)$ matters. A close contact of $x$ is represented by $C(y,x)$.

## English to first-order logic

### Everyone with a fever has COVID or influenza, or both

$$
\forall x\bigl(F(x)\rightarrow(S(x)\vee I(x))\bigr).
$$

The implication restricts the claim to people with a fever. The inclusive disjunction permits a person to have both illnesses.

### Roommates are close contacts

$$
\forall x\,\forall y\bigl(R(x,y)\rightarrow C(x,y)\bigr).
$$

### Some close contacts are not roommates

$$
\exists x\,\exists y\bigl(C(x,y)\wedge\neg R(x,y)\bigr).
$$

### Everyone with COVID has a close contact with COVID

$$
\forall x\bigl(S(x)\rightarrow\exists y(C(y,x)\wedge S(y))\bigr).
$$

The existential witness may be different for different values of $x$.

### Anyone who has a roommate with COVID and does not have COVID is vaccinated

$$
\forall x\bigl(((\exists y(R(x,y)\wedge S(y)))\wedge\neg S(x))\rightarrow V(x)\bigr).
$$

### If everyone is vaccinated, then no one has COVID

$$
(\forall x\,V(x))\rightarrow(\forall y\,\neg S(y)).
$$

This is one implication between two complete sentences. It does not claim that everyone is vaccinated.

### Every unvaccinated close contact of an infected person is infected

$$
\forall x\bigl(S(x)\rightarrow\forall y((C(y,x)\wedge\neg V(y))\rightarrow S(y))\bigr).
$$

## First-order logic to English

* $\forall x((F(x)\wedge V(x))\rightarrow I(x))$: everyone who has a fever and is vaccinated has influenza.
* $S(a)\wedge R(a,b)\wedge\neg V(b)\wedge F(b)$: person $a$ has COVID and is a roommate of person $b$, while $b$ is unvaccinated and has a fever.
* $\forall x\,\exists y\,C(x,y)$: everyone is a close contact of someone.
* $\exists y\,\forall x\,C(x,y)$: there is a person of whom everyone is a close contact.
* $\forall x\,\forall y(C(x,y)\rightarrow C(y,x))$: being a close contact is symmetric.

The two middle formulas show why quantifier order matters: the first allows a different $y$ for each $x$, while the second requires one $y$ that works for every $x$.
