# Sequences

These notes support [F14: Constructed sets](../../skills/Sets/F14.md), including products, tuple powers, and power sets.

A sequence is a list of elements from a set.
We will write them inside parentheses, separated by commas, as so

* (2,7,1,8,2,8)  is a sequence of six digits
* (apple, cherry, banana) is a sequence of 3 strings of characters (or three fruits)
* $(1,3,5,7,9,11,13,\ldots)$  = the infinite sequence of odd numbers
* $(1,4,1,4,2,\ldots)$ = the infinite sequence of digits of the square root of 2

## Products of Sets
The product of sets $S_1,\ldots,S_n$ is written
* $S_1\times S_2 \times \ldots \times S_n$

and is defined as the set of all length n sequences $(s_1,s_2,\ldots,s_n)$ with $s_i\in S_i$ for each $i$.

The product of $S$ with itself $n$ times is written $S^n$, for a positive integer $n$. Order and repetitions matter in a tuple: $(0,1)\ne(1,0)$, and $(0,0)$ has two entries.

Products of tuples may be written in nested or flat form in this course. For example, $((a,b),(c,d,e))$ in $A^2\times B^3$ corresponds to $(a,b,c,d,e)$, whose first two entries belong to $A$ and last three to $B$. Both forms are accepted; formally, flattening is a one-to-one correspondence between the two representations. Subset coordinates retain their braces.

For example if $A=\{0,1\}$ then the elements of $A^2$ are
* $\{(0,0),(0,1),(1,0),(1,1)\}$

if $B=\{T,F\}$ then the elements of $A\times B$ are
* $\{(0,F),(0,T),(1,F),(1,T)\}$

## Exercise 1
1. Describe in English the set $A = \mathbb{N}\times \{0,1\}$ and list a few members of this set
2. Let $B=\{0,1\}$, list the elements of the set $C$ defined by $C=B\times{\cal P}(B)$
    where ${\cal P}(B) = 2^B$ is the powerset of B.
3. List the elements of the set $D = \{(a,s)\in C | a \in s\}$

## Sizes of product sets
We will use the following notation to represent the size of a set $S$, i.e. the number of elements it contains:
* $\vert S \vert$

---

**Theorem.** Let $A$ and $B$ be any finite sets, then
* $\vert A\times B\vert = \vert A \vert * \vert B \vert$

**Proof:** To see that  $\vert A\times B\vert = \vert A \vert * \vert B \vert$, we can
create a table of size $\vert A \vert * \vert B \vert$ whose elements are precisely the
elements of $A\times B$. Let the rows be indexed by $A$ and the columns by $B$, and the
entries in row "a" and column "b", be $(a,b)$.

| | $b_1$ | $b_2$ | $\ldots$ | $b_s$ |
|--- | ---  | --- | --- | --- |
| $a_1$ | $(a_1,b_1)$ | $(a_1,b_2)$ | $\ldots$ | $(a_1,b_s)$ |
| $a_2$ | $(a_2,b_1)$ | $(a_2,b_2)$ | $\ldots$ | $(a_2,b_s)$ |
| $\vdots$ | $\vdots$ | $\vdots$ | $\ddots$ | $\vdots$ |
| $a_r$ | $(a_r,b_1)$ | $(a_r,b_2)$ | $\ldots$ | $(a_r,b_s)$ |


This table will contain all elements of $A\times B$
and since a table with $n$ rows and $m$ columns has $n * m$ entries. Q.E.D

---
**Corollary.** Let $A_1,A_2,\ldots,A_n$ be finite sets, then

$\vert A_1\times\ldots\times A_n\vert = \prod_{i=1}^n\vert A_i \vert$

**Proof (induction on $n$).** For $n=1$, the formula is $|A_1|=|A_1|$. Assume the count holds for products of $n-1$ sets. An $n$-tuple is formed by extending an $(n-1)$-tuple with a final element of $A_n$. Each prefix has $|A_n|$ extensions, so

$$
|A_1\times\cdots\times A_n|
=\left(\prod_{i=1}^{n-1}|A_i|\right)|A_n|
=\prod_{i=1}^n|A_i|.
$$

This proves the formula for every positive integer $n$. **Q.E.D.**

In particular, $|A^n|=|A|^n$. If any factor is empty, no tuple can be formed, so the product is empty.

---

## Power-set counting proof

**Theorem.** Let $A$ be a finite set and let ${\cal P}(A)$ be the power set of $A$, i.e. the set of all subsets of $A$, then
* $\vert {\cal P}(A)\vert = 2^{\vert A \vert }$

**Proof:** We will show that there is a one-to-one correspondence $b \leftrightarrow S_b$
between bit strings of length $n$ and subsets of $A$, where $n$ is the size of $A$.
Let $a_1,\ldots,a_n$ be the elements of $A$ and let $b$ be a bit string of length $n$,
then $b$ is a sequence of $n$ bits $(b_1,b_2,\ldots,b_n)$ where each $b_i \in B=\{0,1\}$.
Let $S_b$ be the set
* $S_b = \{a_i | 1\le i\le n \wedge b_i=1\}$.
Likewise if $S$ is a subset of $A$ we can define
* $b_S = (b_1,b_2,\ldots,b_n)$ where $b_i=1 \leftrightarrow a_i\in S$

For example let $A=\{a_1,a_2,a_3\}$, then here is the correspondence

| Bit string $b$ | Subset $S_b$ |
| --- | --- |
| 000 | $\emptyset$ |
| 001 | $\{a_3\}$ |
| 010 | $\{a_2\}$ |
| 011 | $\{a_2,a_3\}$ |
| 100 | $\{a_1\}$ |
| 101 | $\{a_1,a_3\}$ |
| 110 | $\{a_1,a_2\}$ |
| 111 | $\{a_1,a_2,a_3\}$ |


This shows that each bit string $b$ can be associated to a unique subset $S_b$
and each subset $S$ is $S_b$ for some bit string $b$. So the number of subsets of $A$
is equal to the number of bit strings of length $n$ which is $2^n$.
QED.

---

**Exercise 2**
Recall that ${\cal F}_n = \{0,1,\ldots,n-1\}$. So

$F_2 = \{0,1\}$

$F_3 = \{0,1,2\}$

$F_4 = \{0,1,2,3\}$

and $\vert F_n \vert = n$

Calculate the sizes of the following sets, and write down a few of their elements.
1. ${\cal F}_2^3$
2. ${\cal F}_3 \times {\cal F}_5$
3. ${\cal P}({\cal F}_3)$
4. ${\cal F}_3\times {\cal P}({\cal F}_2)$
5. ${\cal P}({\cal F}_3)^2$
6. ${\cal P}({\cal P}({\cal F}_2))$

## Disjoint unions and the sum rule

If $A\cap B=\emptyset$, every element of $A\cup B$ comes from exactly one input, so

$$
|A\cup B|=|A|+|B|.
$$

When the sets overlap, adding their sizes counts common elements twice. See the [addition principle](../counting/basicCounting.md#the-addition-principle) and [F18](../../skills/Combinatorics/F18.md#the-addition-principle) for examples.

## Further practice

[F14](../../skills/Sets/F14.md#sample-problems) combines these rules in nested products and power sets, with example elements and explained cardinalities.

