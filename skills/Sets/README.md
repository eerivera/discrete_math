# Overview of Sets

<!-- Practice reference: Sets_and_Functions.tex in the COSI29A/Overleaf project, F12 P1-P5, F13 P1-P5, and F14 P1-P5. Practice uses new data and conditions; source solutions were checked rather than copied. -->

Sets describe collections of objects. These skills develop the notation for those objects, the algebra of membership conditions, and the construction and counting of more complex sets.

## Skills in this unit

| Skill | Focus | Related course notes |
| --- | --- | --- |
| [F12](F12.md) | Comprehensions; listing numbers, tuples, and subsets; membership versus inclusion | [Sets](../../notes/math_data_types/sets.md) |
| [F13](F13.md) | Union, intersection, difference, complement; algebraic and membership proofs; counterexamples | [Sets and logic](../../notes/math_data_types/setsAndLogic.md) |
| [F14](F14.md) | Products, tuple powers, and power sets; element structure and cardinality | [Products and sequences](../../notes/math_data_types/sequences.md) |

Each skill page contains new practice problems modeled on the course's exam question bank, a tutorial, and explained answers. The skill tutorials incorporate the legacy definitions and explanations needed for the tested tasks so the unit can be taught directly from these pages. Further-reading links identify broader material, including real intervals, indexed set operations, longer counting proofs, and disjoint unions.

The [commonly used sets](F12.md#commonly-used-sets) are included directly in F12 as background for class examples: natural numbers, integers, rational numbers, real numbers, complex numbers, the empty set, and $F_n$, together with positive/negative notation and membership examples.

## Notation used throughout

* $\mathbb N=\{0,1,2,\ldots\}$ includes zero, and $F_n=\{0,1,\ldots,n-1\}$ has $n$ elements; $F_0=\emptyset$. The course also writes $\mathbb F_n$ or $\mathcal F_n$.
* Braces describe sets; parentheses describe tuples. Order does not matter in a set listing, but every element must appear exactly once; repeated elements make the listing invalid. Tuples preserve order and allow repeated entries.
* $x\in A$ is membership. $S\subseteq A$ is inclusion. Here $S\subset A$ means a proper subset.
* $\mathcal P(A)$, $P(A)$, and $2^A$ denote the power set. Its elements are subsets of $A$.
* $A^c$ and $\overline A$ denote complement in a stated common universe $U$.
* Quantifiers use a dot after each quantified variable. Their scope follows the [predicate-calculus convention](../../notes/predicate_calculus/overview.md#dot-notation-and-quantifier-scope).
* Products of tuples can be written in nested or flat form. [F14](F14.md#cartesian-products-and-powers) explains the correspondence; set coordinates keep their braces.

## Connections between the skills

F12 asks which objects satisfy a membership condition. F13 uses Boolean algebra to transform those conditions and prove statements for arbitrary sets. F14 asks what shape an object must have and how many choices each construction provides.

The cardinality rules for finite sets are

$$
|A\times B|=|A|\cdot|B|,\qquad
|A^n|=|A|^n,\qquad
|\mathcal P(A)|=2^{|A|}.
$$

These rules lead into [F18: Counting principles](../Combinatorics/F18.md). The [disjoint-union sum rule](../../notes/math_data_types/sequences.md#disjoint-unions-and-the-sum-rule) is additional background for this unit.

The [binary-number notes](../../notes/math_data_types/binaryNumbers.md) provide background on the bit strings used to represent subsets. [Countability](G07.md) treats infinite sets later in the course. [Functions](../Functions/F15.md) use sets as domains and codomains.
