# Overview of Combinatorics

Counting identifies how many outcomes satisfy a set of conditions. Start by deciding what an outcome records: positions in a string, membership in a subset, repeated ranks in a hand, or the output of a function. Then choose rules that count each outcome exactly once.

## Skills in this unit

| Skill | Focus | Related course notes |
| --- | --- | --- |
| [F18](F18.md) | Disjoint cases, products, repeated choices, and strings | [Basic counting](../../notes/counting/basicCounting.md) |
| [F19](F19.md) | Permutations, combinations, positions, and grouped selections | [Permutations and combinations](../../notes/counting/permsAndCombs.md) |
| [F20](F20.md) | Overlaps, constrained tuples, ranges, and inclusion and exclusion | [Divisibility and complements](../../notes/counting/basicCounting.md#principle-of-inclusion-and-exclusion) |
| [F21](F21.md) | Finite cardinality proofs, subset sums, and pigeonhole bounds | [Pigeonhole principle](../../notes/counting/pigeonhole.md) |
| [G04](G04.md) | Combined methods, exact rank patterns, labeled positions, and exclusions | [Card counting](../../notes/counting/permsAndCombs.md#counting-cards) |

Each skill page has two or three sample sets, a tutorial, and worked answers. Show the reasoning behind a product, sum, or subtraction. Give an exact expression when allowed and calculate a number or polynomial when the question requests one.

Use the samples to practice defining an outcome, choosing a representation, and explaining why a construction is complete and counts each outcome once. Try changing a condition and deciding how the method must change. Recognizing a familiar context is a starting point; the justification depends on the precise rules.

The [Sets unit](../Sets/README.md) supplies products and power sets. The [Functions unit](../Functions/README.md) supplies injections, surjections, and bijections, which F21 uses to prove that collisions are unavoidable. Use the [additional counting notes](../../notes/counting/overview.md) for more examples, algebraic identities, and stars and bars.

## Choosing a counting model

All sets in these formulas are finite. Let $A$ have $n$ elements. An order on $A$ lets us represent a subset or multiset by its unique sorted sequence.

| Outcome | What distinguishes it | Count |
| --- | --- | --- |
| Length-$k$ sequence | Positions matter; repetition allowed | $n^k$ |
| Length-$k$ permutation | Positions matter; entries distinct | $P(n,k)=n!/(n-k)!$ for $0\le k\le n$ |
| Size-$k$ subset | Membership matters; entries distinct | $\binom{n}{k}=n!/(k!(n-k)!)$ for $0\le k\le n$ |
| Size-$k$ multiset | Multiplicities matter; use one nondecreasing representative | $\binom{n+k-1}{k}$ for $n\ge1$, $k\ge0$ |

There is one empty sequence, empty subset, or empty multiset. If $k>n$, there are no permutations or subsets of size $k$. If $n=0$, there are no positive-length sequences or positive-size multisets; the multiset formula above assumes $n\ge1$. A multiset is not an ordinary set listing with repeated elements. See the [multiset notes](../../notes/counting/multisets.md) for the stars-and-bars proof, cookie distributions, and nondecreasing digit strings.

## Disjoint addition principle

For pairwise disjoint finite sets,

$$
\left|\bigcup_{i=1}^m A_i\right|=\sum_{i=1}^m|A_i|.
$$

Each element occurs in exactly one case. Different lengths are disjoint; overlapping conditions need inclusion and exclusion.

## Subtraction principle

For finite $A$ and $B$,

$$
|A\setminus B|=|A|-|A\cap B|.
$$

If $B\subseteq A$, this is $|A|-|B|$. To count allowed outcomes by subtraction, start with a universe and remove its forbidden subset.

## Multiplication principle

For finite sets $A_i$ and a finite index set $I$,

$$
\left|\prod_{i\in I}A_i\right|=\prod_{i\in I}|A_i|.
$$

In particular, $|A^k|=|A|^k$. The product over no coordinates contains the one empty tuple.

## Generalized multiplication principle

If outcomes are constructed by choices $c_1,\ldots,c_r$, and each valid prefix has exactly $n_i$ extensions at step $i$, then the number of construction paths is $n_1\cdots n_r$. It counts outcomes when each outcome has exactly one construction. If the number of extensions depends on the earlier choices, split into cases instead of multiplying fixed counts.

## Bijection principle

A bijection $A\rightarrow B$ pairs every element of one finite set with exactly one of the other, so $|A|=|B|$.

## Injection, surjection, and pigeonhole principles

For a total function $f:A\rightarrow B$ between finite sets:

* An injection requires $|A|\le|B|$.
* A surjection requires $|A|\ge|B|$.
* If $|A|>|B|$, $f$ cannot be injective: two distinct inputs share an output.
* If $|A|<|B|$, $f$ cannot be surjective.

For an integer $t\ge1$, $|A|>(t-1)|B|$ guarantees an output with at least $t$ inputs. If $B$ is nonempty, some output has at least $\lceil|A|/|B|\rceil$ inputs.

## Counting through equal-size fibers

If $f:A\rightarrow B$ is a total surjection and every fiber $f^{-1}(\lbrace b\rbrace)$ has the same positive size $k$, then

$$
|B|=\frac{|A|}{k}.
$$

**Proof.** The fibers partition $A$, and each of the $|B|$ fibers contains $k$ inputs. Thus $|A|=k|B|$, proving the formula. **Q.E.D.**

For example, mapping an ordered selection of $k$ distinct elements to its underlying subset counts each subset $k!$ times. Dividing by that constant factor gives the combination formula. Dividing by an overcount factor requires that every outcome have the same number of representations.

## Principle of inclusion and exclusion

For two or three finite sets,

$$
|A\cup B|=|A|+|B|-|A\cap B|,
$$

$$
\begin{aligned}
|A\cup B\cup C|={}&|A|+|B|+|C|\\
&-|A\cap B|-|A\cap C|-|B\cap C|+|A\cap B\cap C|.
\end{aligned}
$$

For a finite index set $I$,

$$
\left|\bigcup_{i\in I}S_i\right|
=\sum_{\emptyset\ne J\subseteq I}(-1)^{|J|+1}\left|\bigcap_{j\in J}S_j\right|.
$$

Only **nonempty** index subsets occur. Alternate signs by intersection size. An element belonging to $r\ge1$ sets receives weight $\sum_{j=1}^r(-1)^{j+1}\binom{r}{j}=1$ by the binomial theorem.
