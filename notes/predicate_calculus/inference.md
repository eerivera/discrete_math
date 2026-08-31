# Inference and Validity of Arguments

## Skills Addressed

* [G02 — Predicate Calculus: Inference](../../skills/Predicate_Calculus/G02.md)

An **argument** consists of premises $E_1,\ldots,E_n$ and a conclusion $C$. We use sentences—formulas with no free variables—so their truth values are determined by an interpretation.

The argument is **valid** when every interpretation that makes all the premises True also makes the conclusion True. The domain and the meanings of the nonlogical symbols may vary from one interpretation to another.

Equivalently, the argument is valid exactly when

$$
E_1\wedge\cdots\wedge E_n\wedge\neg C
$$

is unsatisfiable. This equivalence is the basis of the truth-tree method: put the premises and the negation of the conclusion on the tree and try to close every branch.

## Countermodels

An invalid argument has a **countermodel**: a particular nonempty domain and interpretations of its symbols that make every premise True and the conclusion False.

Showing one interpretation in which the premises and conclusion are all True does not prove validity. Validity is a statement about every interpretation. By contrast, a single verified countermodel is enough to prove invalidity.

## Example: A valid quantifier inference

Consider

$$
\exists x\,\forall y\,P(x,y)
$$

as a premise and

$$
\forall y\,\exists x\,P(x,y)
$$

as the conclusion. If one element $a$ satisfies $P(a,y)$ for every $y$, then for each $y$ there certainly exists an $x$ satisfying $P(x,y)$—namely $a$. The argument is valid.

## The converse is invalid

The converse would use $\forall y\,\exists x\,P(x,y)$ as its premise and $\exists x\,\forall y\,P(x,y)$ as its conclusion.

Take the domain $D=\{0,1\}$ and interpret $P(x,y)$ as $x=y$. For every $y$, choosing $x=y$ makes $P(x,y)$ True, so the premise is True. But no single $x$ equals both $0$ and $1$, so the conclusion is False. This is a countermodel, and the converse is invalid.

## Termination

First-order validity is not decidable by an algorithm that always terminates with a yes-or-no answer. A complete, fair proof search will eventually find a finite proof when an argument is valid, but a search for an invalid argument may continue indefinitely. When a tree does not close quickly, finding and verifying a countermodel can establish invalidity directly.

For more examples, see [The Logic Notes exercises](https://users.cecs.anu.edu.au/~jks/LogicNotes/exercises3.html).
