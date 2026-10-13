# Sets

For focused tutorials and worked practice, see [F12: Set notation](../../skills/Sets/F12.md), [F13: Set algebra](../../skills/Sets/F13.md), and [F14: Constructed sets](../../skills/Sets/F14.md).

A set is a collection of distinct elements. List its elements inside braces: $\{a,b,c\}$. Order and repetition do not change a set, so $\{a,b\}=\{b,a\}=\{a,a,b\}$.

The predicate $x\in A$ says that $x$ is an element of $A$, while $x\notin A$ says that it is not. For a finite set, $|A|$ denotes the number of distinct elements.

## Common sets

* $\emptyset=\{\}$ is the empty set.
* $\mathbb N=\{0,1,2,\ldots\}$ is the set of natural numbers.
* $\mathbb Z=\{\ldots,-2,-1,0,1,2,\ldots\}$ is the set of integers.
* $\mathbb Q$ is the set of rational numbers.
* $\mathbb R$ is the set of real numbers.
* $\mathbb C$ is the set of complex numbers.
* $F_n=\{0,1,\ldots,n-1\}$ is the set of the first $n$ natural numbers, with $F_0=\emptyset$. The course also uses $\mathbb F_n$ and $\mathcal F_n$ for this set.

Superscripts $+$ and $-$ indicate positive and negative elements, respectively; for example, $\mathbb Z^+$ contains the positive integers and $\mathbb R^-$ contains the negative reals. Zero belongs to neither.

## Set comprehensions

A comprehension describes elements of a domain that satisfy a condition:

$$
\{x\in S: P(x)\}\qquad\text{or}\qquad\{x\in S\mid P(x)\}.
$$

Read the colon or vertical bar as “such that.” For example, the odd integers can be written in two ways:

$$
\{x\in\mathbb Z: \exists k\in\mathbb Z . x=2k+1\}
=\{2k+1: k\in\mathbb Z\}.
$$

The expression before the colon determines the elements to list. Thus $\{x^2:x\in\mathbb Z\wedge -2\le x\le2\}=\{0,1,4\}$: the elements are the outputs, with duplicates removed, rather than the five inputs.

## Intervals

By default, intervals here are sets of real numbers:

$$
[a,b]=\{x\in\mathbb R:a\le x\le b\},
$$

$$
[a,b)=\{x\in\mathbb R:a\le x<b\},
$$

$$
(a,b]=\{x\in\mathbb R:a<x\le b\},
$$

$$
(a,b)=\{x\in\mathbb R:a<x<b\}.
$$

A bracket includes its endpoint; a parenthesis excludes it. Specify the discrete domain when listing integers or natural numbers:

$$
\mathbb Z\cap[2,5]=\{2,3,4,5\},\qquad
\mathbb N\cap[0,7)=\{0,1,2,3,4,5,6\}.
$$

In particular, $F_n=\mathbb N\cap[0,n)$. The real interval $[2,5]$ also contains $2.5$ and infinitely many other real numbers.

## Subsets and equality

$A\subseteq B$ means every element of $A$ belongs to $B$:

$$
(A\subseteq B)\leftrightarrow(\forall x . (x\in A)\rightarrow(x\in B)).
$$

We use $A\subset B$ to mean a **proper** subset: $A\subseteq B$ and $A\ne B$. Equality means having exactly the same elements:

$$
(A=B)\leftrightarrow(\forall x . (x\in A)\leftrightarrow(x\in B)).
$$

Membership and inclusion are different. If $A=\{0,1\}$, then $0\in A$ and $\{0\}\subseteq A$, but $\{0\}\notin A$. The empty set is a subset of every set, but it is an element only of sets that contain it explicitly. For example, $\emptyset\in\{\emptyset\}$, and $|\{\emptyset\}|=1$ while $|\emptyset|=0$.

## Set operations

Fix a universe $U$ containing all the sets under discussion.

| Operation | Definition |
| --- | --- |
| Union | $A\cup B=\{x\in U:(x\in A)\vee(x\in B)\}$ |
| Intersection | $A\cap B=\{x\in U:(x\in A)\wedge(x\in B)\}$ |
| Difference | $A-B=\{x\in U:(x\in A)\wedge\neg(x\in B)\}=A\cap B^c$ |
| Complement | $A^c=\overline A=U-A$ |

Union uses inclusive “or.” A complement depends on its universe: the complement of $\{0\}$ in $\{0,1\}$ is $\{1\}$, but its complement in $\{0,1,2\}$ is $\{1,2\}$.

## Indexed unions and intersections

For a finite collection of sets,

$$
\bigcup_{i=1}^n S_i=S_1\cup\cdots\cup S_n,\qquad
\bigcap_{i=1}^n S_i=S_1\cap\cdots\cap S_n.
$$

Membership in an indexed union means membership in at least one input set; membership in an indexed intersection means membership in every input set:

$$
x\in\bigcup_{i=1}^n S_i
\leftrightarrow(\exists i\in\{1,\ldots,n\} . x\in S_i),
$$

$$
x\in\bigcap_{i=1}^n S_i
\leftrightarrow(\forall i\in\{1,\ldots,n\} . x\in S_i).
$$

For example, with $S_1=\{0,1\}$, $S_2=\{1,2\}$, and $S_3=\{1,3\}$, their union is $\{0,1,2,3\}$ and their intersection is $\{1\}$.

See [Sets and logic](setsAndLogic.md) for the Boolean algebra laws governing these operations.

## Products and power sets

$A\times B$ is the set of ordered pairs $(a,b)$ with $a\in A$ and $b\in B$. Use parentheses for pairs and braces for sets.

The **power set** $\mathcal P(A)$, also written $P(A)$ or $2^A$, is the set of all subsets of $A$:

$$
S\in\mathcal P(A)\leftrightarrow S\subseteq A.
$$

For example,

$$
\mathcal P(\{a,b\})=\{\emptyset,\{a\},\{b\},\{a,b\}\}.
$$

It includes $\emptyset$ and $A$ itself. For finite $A$, $|\mathcal P(A)|=2^{|A|}$. See [Products and sequences](sequences.md) for the counting proofs and [F14](../../skills/Sets/F14.md) for nested constructions.

## Exercise 1

Let $A=\{1,2,3,4,5,6\}$, $B=\{5,6,7,8,9,0\}$, $C=\{1,3,5,7,9\}$, and $U=\{0,1,2,3,4,5,6,7,8,9\}$.

List the elements of each set:

1. $A\cup B$
2. $A\cap B$
3. $\overline C$
4. $A\cap C$
5. $\overline{A\cap B}$
6. $C\cap(A\cup B)$
7. $C\cup(A\cap B)$

## Exercise 2

Describe these sets in English and list a few elements if they are nonempty:

1. $A=\{x\in\mathbb Z:\exists y\in\mathbb Z . x=y^2\}$.
2. $B=\{x\in\mathbb Z:x\ge0\wedge\sqrt{x}\in\mathbb Q\}$, where $\sqrt{x}$ is the nonnegative real square root.
3. $C=\{x\in\mathbb R:x^2<9\}$.
4. $D=\{x\in\mathbb N:10-x\in\mathbb N\}$.

Then answer the following:

5. Is $A\subseteq B$?
6. What would $A=B$ mean? Is it true?
7. What is $C^c\cap D$, with the complement taken in $U=\mathbb R$?
8. List the elements of $\mathcal P(\{0,1,2\})$.
