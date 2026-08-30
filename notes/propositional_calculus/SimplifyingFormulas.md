# Simplifying Propositional Formulas

## Skill Addressed

* [F04 — Boolean Algebra](../../skills/Propositional_Calculus/F04.md)

Any formula in propositional logic can be reduced to one containing only the $\vee$ and $\wedge$ operators
and propositional symbols $P,Q,...$ and their negations $\neg P, \neg Q, ...$.

## Simplification rules
To do this, we use the Demorgan rules to push negation down to the propositionial symbols,
but first we use the following substitution rules which preserve logical equivalence to remove all operators
except disjunction and conjunction:

$E \rightarrow F \equiv (\neg E \vee F)$

$E \oplus F \equiv (E\wedge \neg F) \vee (\neg E\wedge F)$

$E \leftrightarrow F \equiv (E\wedge F) \vee ((\neg E)\wedge (\neg F))$

## Example 1
Lets show how to simplify $P \rightarrow (Q \rightarrow (R\oplus P))$

This example doesn't require any use of the DeMorgan rules.

First we remove the implications and the exclusive or using the simplication rules

$P \rightarrow (Q \rightarrow (R\oplus P)) \equiv$

$P \rightarrow (Q \rightarrow ((R\wedge \neg P) \vee (\neg R\wedge P))) \equiv$

$P \rightarrow (\neg Q \vee (R\wedge \neg P) \vee (\neg R\wedge P)) \equiv$

$\neg P \vee (\neg Q \vee (R\wedge \neg P) \vee (\neg R\wedge P)) \equiv$

$\neg P \vee \neg Q \vee (R\wedge \neg P) \vee (\neg R\wedge P)$

This is in Disjunctive Normal Form (DNF). On an exam, no further simplification
would be required. However, the absorption law can remove the redundant
conjunction $R\wedge\neg P$:

$\neg P \vee (R\wedge\neg P) \equiv \neg P$.

The result is therefore

$\neg P \vee \neg Q \vee (\neg R\wedge P)$.

Using $A\vee(\neg A\wedge B)\equiv A\vee B$, this can be simplified fully:

$\neg P \vee \neg Q \vee (\neg R\wedge P)
\equiv \neg P \vee \neg Q \vee \neg R$.

Thus, the original formula is True precisely when at least one of $P$, $Q$,
and $R$ is False.

## Example 2
Let's try another which will use DeMorgan

Simplify $(A\rightarrow B) \rightarrow \neg (B \rightarrow A)$

First we replace the implications with disjunctions:

$(A\rightarrow B) \rightarrow \neg (B \rightarrow A) \equiv$

$(\neg A\vee B) \rightarrow \neg (\neg B \vee A) \equiv$

$\neg (\neg A\vee B) \vee \neg (\neg B \vee A) \equiv$

Then we apply the DeMorgan rules:

$(\neg\neg A\wedge \neg B) \vee (\neg\neg B \wedge \neg A) \equiv$

and we remove the double negations as $\neg\neg A \equiv A$

$(A\wedge \neg B) \vee (B \wedge \neg A)$

and this says that exactly one of A and B is True, so this expressions is equivalent to $A\oplus B$
