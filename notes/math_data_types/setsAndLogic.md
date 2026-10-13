# Sets and Logic

This page connects set operations with predicate and propositional calculus. See [F13](../../skills/Sets/F13.md) for the set-algebra law table, simplification examples, proofs, and counterexamples.

## Correspondences of logic and set operations

Let $U$ be a universe and consider subsets $A,B,\ldots$ of $U$. For each $A$, define the membership predicate $P_A$ on $U$ by

$$
\forall x\in U . P_A(x)\leftrightarrow(x\in A).
$$

Its truth value records whether $x$ belongs to $A$.

**Theorem.** For $A,B\subseteq U$,

$$
\forall x\in U . P_{A\cap B}(x)\leftrightarrow(P_A(x)\wedge P_B(x)),
$$

$$
\forall x\in U . P_{A\cup B}(x)\leftrightarrow(P_A(x)\vee P_B(x)),
$$

$$
\forall x\in U . P_{A^c}(x)\leftrightarrow\neg P_A(x).
$$

**Proof.** Fix an arbitrary $x\in U$. By definition, $x\in A\cap B$ exactly when $x\in A$ and $x\in B$, giving the first equivalence. The definitions of union and complement give the other two. **Q.E.D.**

Thus union corresponds to $\vee$, intersection to $\wedge$, and complement to $\neg$. Membership in $U$ is always true, and membership in $\emptyset$ is always false. Difference satisfies $A-B=A\cap B^c$, so its membership condition is $(x\in A)\wedge\neg(x\in B)$.

## From logical laws to set identities

Two sets are equal exactly when their membership conditions agree for every element of $U$:

$$
(A=B)\leftrightarrow(\forall x\in U . (x\in A)\leftrightarrow(x\in B)).
$$

**Corollary.** For $A,B,C\subseteq U$,

* $(A\cap B)^c=A^c\cup B^c$;
* $(A\cup B)^c=A^c\cap B^c$;
* $(A^c)^c=A$;
* $A\cup(B\cap C)=(A\cup B)\cap(A\cup C)$; and
* $A\cap(B\cup C)=(A\cap B)\cup(A\cap C)$.

**Proof of the first identity.** Fix an arbitrary $x\in U$. Then

$$
\begin{aligned}
x\in(A\cap B)^c
&\leftrightarrow\neg((x\in A)\wedge(x\in B))\\
&\leftrightarrow(\neg(x\in A)\vee\neg(x\in B))\\
&\leftrightarrow((x\in A^c)\vee(x\in B^c))\\
&\leftrightarrow x\in A^c\cup B^c.
\end{aligned}
$$

The first and last transformations use membership definitions, and the middle transformation uses De Morgan's law in logic. Both sets have exactly the same elements. The remaining identities follow from the corresponding logical equivalences in the same way. **Q.E.D.**

## Algebraic proofs

Once the laws have been established, we can use them directly. For example,

$$
\begin{aligned}
(A\cup B)^c\cup A
&=(A^c\cap B^c)\cup A &&\text{De Morgan}\\
&=(A^c\cup A)\cap(B^c\cup A) &&\text{distributive}\\
&=U\cap(B^c\cup A) &&\text{complement}\\
&=B^c\cup A &&\text{identity}.
\end{aligned}
$$

Both membership proofs and algebraic derivations can establish identities for arbitrary sets. Name the laws used in an algebraic proof, or explain the equivalences in a membership proof.

## Inclusions and counterexamples

For subsets of $U$,

$$
(A\subseteq B)\leftrightarrow(\forall x\in U . (x\in A)\rightarrow(x\in B)).
$$

To prove an inclusion, start with an arbitrary element of the left side and show it belongs to the right side. To prove equality by inclusions, prove both directions.

To refute an identity, specify sets and show that an element belongs to one side but not the other. To refute an inference, satisfy all its premises while making its conclusion false. [F13](../../skills/Sets/F13.md#subset-inferences-and-counterexamples) gives worked examples.
