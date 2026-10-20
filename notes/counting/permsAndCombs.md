# Permutations and Combinations

These notes support [F19](../../skills/Combinatorics/F19.md) and [G04](../../skills/Combinatorics/G04.md). All sets counted here are finite. A hand is an unordered set of distinct cards; a deal records their order. Draws are without replacement unless stated otherwise.

# Permutations of k elements out of n
Suppose now we want to pick a sequence $S$ of size $k$ from a set $A$ of size $n$
How many such sequences are there? Since we have $n$ choices for each of the $k$ elements
in the sequence, there are $n^k$ such sequences.

Let's do an example, let's pick 2 elements from $\lbrace 1,2,3\rbrace$
There are 9 possibilities if you allow duplicates

```
11 12 13 21 22 23 31 32 33
```
Only 6 with no repeated entries

```
12 13 21 23 31 32
```

Suppose now we want sequences with no repeated elements!
There are

* $n$ choices for the position 1,
* $n-1$ for position 2
* $n-2$ for position 3
* $\ldots$
* $n-(k-1)$ for position $k$

So the total number of such sequences is

$n * (n-1) * (n-2) * \ldots * (n-(k-1))$

which is equal to $n!/(n-k)!$

We usually use the notation $P(n,k) = n!/(n-k)!$
to denote the number of permutations of $k$ elements out of $n$.

Here $n$ and $k$ are nonnegative integers, and the factorial formula assumes $0\le k\le n$. We use $0!=1$: selecting no elements gives one empty sequence. If $k>n$, there are no selections with distinct entries, so $P(n,k)=0$.

### Applications
Suppose we have 10 people competing for the All Around Championship
and we will have 3 medals: gold, silver, bronze. How many possible outcomes
are there?

We are looking for the number of sequences of length 3 from a set of 10 elements,
so the answer is 10 * 9 * 8 = 720 as there are 10 choices for the gold medal, then 9 remaining choice
for the silver, and finally 8 for the bronze.

# Combinations
If we don't care about the order, we just want the number of subsets of size $k$ of a set $A$ of $n$ elements, then we will have overcounted each subset by a factor of $k!$ as each permutation of it is the same subset.  Hence the number of such combinations is $P(n,k)/k!$

We denote this as $C(n,k)$ or $\binom{n}{k}$ where

$C(n,k) = \binom{n}{k} = \frac{n!}{(n-k)! k!}$

and we call it "n choose k" as it is the number of ways we can choose k elements out of n,
so "from n choose k"

The factorial formula above assumes $0\le k\le n$. There is one subset of size 0, and there are no size-$k$ subsets when $k>n$. For $1\le k\le n$, calculate as follows:

* start with $n$ and divide by 1
* multiply by $n-1$ and divide by 2
* multiply by $n-2$ and divide by 3
* $\ldots$
* multiply by $n-(k-1)$ and divide by $k$

For example.

$$
\dbinom{6}{3} = \frac 61 * \frac 52 * \frac 43 = 30/2\ * \frac 43 = 15 * \frac 43 = 60/3 = 20
$$

which is easier to compute than $6!/(3!3!)$.  This works because

$$
\dbinom{n}{k} = \dbinom{n}{k-1} * \frac{n-(k-1)}{k}
$$

### Applications
How many ways are there of forming two teams, team A and team B, from a group of 4 players, with two players on each named team?

If we first choose team A, then there are $\binom{4}{2} = 4!/(2! 2!) = 24/4 = 6$ such teams:

```
team A could be one of 12, 13, 14, 23, 24, 34
```

Suppose we want all of the subsets of size 3 from $\lbrace 1,2,3,4,5,6,7,8,9,10\rbrace$.
This would be 10 choose 3 = $\binom{10}{3} = 10 * 9 * 8/ (3 * 2 * 1) = 120$ and we won't list them!

# The Generalized Multiplication Principle
Suppose we can construct the elements in a set by making a sequence of choices $c_1,c_2,\ldots,c_n$ and
for choice $c_i$ we have $r_i$ options after any valid earlier choices, and each outcome has exactly one construction.  Then the total number of elements we can construct, i.e. the size of the set of all such elements is $\prod_{i=1}^n r_i = r_1 * r_2 * \ldots * r_n$

### Applications
How many ways are there of rearranging the numbers $1,2,3,\ldots,n$?
As we've seen before, these are called the permutations of $n$.
To apply our general principle, we can create such a sequence by

* picking the first number (out of n), then
* picking the second number (out of the n-1 remaining elements), then
* picking the 3rd number (out of the n-2 remaining elements), then ...

and repeating until we have only one number, the nth, to pick and there is no choice.

Thus the total number of ways we could generate such a permutation is

$$
n * (n-1) * (n-2) * \ldots * 3 * 2 * 1
$$

and we call this n factorial and denote it as $n!$

So for n=3 there are 3 * 2 * 1 such permutations:

```
1 2 3
1 3 2
2 1 3
2 3 1
3 1 2
3 2 1
```
and for n=4 there are 24 permutations.

**License Plates 2**
Suppose a hypothetical format allows license plates with three digits and three letters,
but they can be in any position, e.g.  DDDLLL or DLDLDL or DLLLDD etc.

We can apply the generalized multiplication principle as follows:

* first chose the position of the 3 digits. there are 6 choose 3 such ways
* $\binom 6 3 = 6!/3!^2 = 6 * 5 * 4/ (3 * 2 * 1) = 20$
* next we have $10^3$ choices for the three digits and $26^3$ choices for the three letters
* so the number of license plates is $20 * 10^3 * 26^3$

# Binomials and Multinomials
The n choose k function arises in many places beside in counting. One of the best known is in the binomial formula:

**Theorem** [The Binomial Theorem]
$(x + y)^n = \sum_{k=0}^n \binom{n}{k} x^ky^{n-k}$

**Proof:** Observe that $(x+y)^n$ is a sum of monomials constructed by
selecting either x or y from each of the n factors (x+y) ... For example.
let's look at the case of $n=3$

```
(x+y)^3 =
(x+y)(x+y)*(x+y) =
xxx + xxy + xyx + xyy +
yxx + yxy + yyx + yyy
= x^3 + 3x^2y + 3xy^2 + y^3
```
The number of terms corresponding to $x^k y^{n-k}$ is precisely the number of ways
of choosing $k$ of the multiplicands to pick the "x" and then picking y for the other $n-k$ factors

Here are some examples of its use:

* $(x+y)^0 = 1 = \binom 00 x^0y^0$
* $(x+y)^1 = x+y = \binom 11 x^1y^0 + \binom 10 x^0y^1 $
*  $(x+y)^2 = x^2 +2xy +y^2  = \binom 22 x^2y^0 + \binom 21 x^1y^1 + \binom 20 x^0y^2 $
*  $(x+y)^3  = x^3 +3x^2y +3xy^2 + y^3 = \binom 33 x^3y^0 + \binom 32 x^2y^1 + \binom 31 x^1y^2 + \binom30 x^0y^3 $
*  $(x+y)^4 =  x^4 +4x^3y +6x^2y^2 + 4xy^3 + y^4 = \binom 44 x^4y^0 + \binom 43 x^3y^1 + \binom 42 x^2y^2 + \binom 41 x^1y^3 + \binom 4 0 x^0y^4 $

## Pascal's Triangle
The coefficients also can be arranged in rows to form Pascal's Triangle

```
1
1   1
1   2   1
1   3   3   1
1   4   6   4   1
1   5  10  10   5  1
1   6  15  20  15  6  1
....
```
Number rows and columns starting at 0. The entry in row $n$, column $k$ is $\binom{n}{k}$. Each interior entry adds the two entries immediately above it; the edge entries are 1.

**Theorem.** For $n\ge1$ and $1\le k\le n-1$, $\binom nk = \binom{n-1}{k-1} + \binom {n-1}k$

**Proof**
We can prove this by observing that
there are two ways to choose $k$ elements out of $\lbrace 1,\ldots,n\rbrace$

* choose $k$ elements from the first $n-1$ in $\binom {n-1}k$ ways
* choose $k-1$ elements from the first $n-1$ and then add $n$ in $\binom {n-1}{k-1}$

The first is $\binom {n-1}k$ and the second is $\binom {n-1}{k-1}$ and their sum
is $\binom nk$ which proves the Theorem.
**QED**

## Multinomial Theorem
We can think of the n choose k operation as counting the number of subsets of size k in a set of size n, but we can also think of it as the number of ways partitioning a set of size n into two subsets, one of size k and one of size n-k.

For nonnegative integers $k_1,\ldots,k_r$ with $n=k_1+\cdots+k_r$, the multinomial coefficient counts partitions into **named** groups of these sizes. It is defined as follows:

$$
\dbinom{k_1+k_2+\ldots+k_r}{k_1,k_2,\ldots,k_r} = \frac{n!}{k_1! k_2! \ldots k_r!}
$$

and it can be computed more effectively as

$$
\dbinom{n}{k_1} * \dbinom{n-k_1}{k_2} * ... * \dbinom{n-(k_1+\ldots+k_{r-1})}{k_r}
$$

e.g.

$$
\dbinom{10}{2,2,6}=
\dbinom{10}{2} * \dbinom{8}{2} * \dbinom{6}{6} =
  \frac{10 * 9}{1 * 2} * \frac{8 * 7 }{1 * 2} * \frac{6}{6}
  = 45 * 28 * 1 = 1260
$$

which is the number of ways of choosing sets (A,B,C) of sizes 2,2,6 from {1,...,10}
whose union is the original ten-element set and which are pairwise disjoint.

We can see how this works with the generalized multiplication rule. First choose the subset A which is 10 choose 2. Then there are 8 left, so choose the next subset of 2, which is 8 choose 2, then the third subset is all that is left, that is 6 choose 6.

For groups of sizes 2, 3, and 5 instead, the count is

$$
\binom{10}{2,3,5}=\binom{10}{2}\binom{8}{3}\binom{5}{5}
=45\cdot56=2520.
$$

Here the three named groups have sizes 2, 3, and 5 throughout the construction.

So we can get the same result as the multinomial formula but by using the generalize multiplication rule and the binomial formula.

We also have the Multinomial theorem which says these values are the coefficients of $(x_1+\ldots+x_r)^n$

$$
(x_1+\ldots+x_r)^n =
\sum_{\substack{k_1+\cdots+k_r=n\\k_1,\ldots,k_r\ge0}}
\dbinom{n}{k_1,k_2,\ldots,k_r}
x_1^{k_1}\ldots x_r^{k_r}
$$

The proof is the same as for the binomial theorem. The coefficient of $x_1^{k_1}\ldots x_r^{k_r}$
is the number of ways of choosing $x_1$ $k_1$ times, and $x_2$ $k_2$ times, etc when multiplying out that product.

### Applications
Find the number of ways we can form 3 teams A,B,C of two each out of 6 people.

To do this we use the multinomial

* $\binom{6}{2,2,2} = \binom 62 * \binom 42 * \binom 22 = 15*6 = 90$

For three named teams A, B, C of four people each from 12 people, the same method gives $\binom{12}{4}\binom{8}{4}\binom{4}{4}=495\cdot70=34,650$. If the three teams were unnamed, each partition would be counted $3!$ times, giving $34,650/6=5,775$.

# Counting Cards

A card is a rank-suit pair. Let

$$
R=\lbrace 2,3,4,5,6,7,8,9,10,J,Q,K,A\rbrace,\qquad
S=\lbrace \mathrm{hearts},\mathrm{diamonds},\mathrm{clubs},\mathrm{spades}\rbrace.
$$

The deck is $D=R\times S$, with exactly one copy of each rank-suit card: $13\cdot4=52$ distinct cards. Draw cards without replacement. A **hand** records an unordered set of distinct cards; a **deal** records their order. Two cards can have the same rank and different suits. A pair, triple, or four of a kind groups two, three, or four cards of the same rank.

The [list of poker hands](https://en.wikipedia.org/wiki/List_of_poker_hands) gives context for these names; the counting conditions are stated below so no prior knowledge of poker is required.

### Total number of hands as a sequence
There are 52 choices for the first card, 51 for the next, 50 for the third, 49 for the fourth and 48 for the fifth,
so the total number of hands is

$P(52,5) = 52 * 51 * 50 * 49 * 48 = 311,875,200$

### Total number of hands as a set
We can also not worry about the order of the cards and count the number of sets of 5 cards chosen from a deck of 52.
This is $\binom{52}{5} = 2,598,960$

### Four of a kind as a set
Using the Generalized Multiplication rule, we must look at the steps we would take to create a 4 of a kind hand:

* pick the rank of the 4 of a kind card (13 choices)
* pick the rank and suit of the other card (12*4=48 choice)

So the number would be $13 * 48=624$

### Four of a kind as a sequence
First pick the rank (13 choices),
then pick the positions in the sequence (5 choose 4 = 5), then the order of the four suits ($4!$) and the rank and suit of the other card ($12\cdot4$). This gives

$13*24*5*12*4 = 74880$

A **straight** has five consecutive ranks, a **flush** has all five cards in one suit, and a **straight flush** satisfies both conditions. For consecutive ranks use the order 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K, A, and also allow the low-ace sequence A2345. The ace is low in A2345 or high in 10JQKA, with no other wraparound. A **full house** has three cards of one rank and two of a different rank; the multiplicities below describe how many cards share each rank.

For more practice, count the following unordered five-card hands in the full 52-card deck: a full house (3+2), exactly three of a kind (3+1+1), exactly two pairs (2+2+1), a straight flush, and a flush excluding straight flushes.

The counts are, respectively, $13\binom{4}{3}\cdot12\binom{4}{2}=3744$; $13\binom{4}{3}\binom{12}{2}4^2=54,912$; $\binom{13}{2}\binom{4}{2}^2\cdot11\cdot4=123,552$; $10\cdot4=40$; and $4\binom{13}{5}-40=5108$. Choose the repeated ranks and their suits first; the singleton ranks must be distinct and different from repeated ranks. For two pairs choose their ranks as an unordered pair. There are ten possible straight rank sequences, and each has four all-one-suit choices.

# More Problems
 Discrete Math: An Open Introduction by Oscar Levin has many good problems (worked out)
 [at the end of Chapter 1.3](https://discrete.openmathbooks.org/dmoi3/sec_counting-combperm.html)

Return to the [Combinatorics unit](../../skills/Combinatorics/README.md) or explore [multisets and stars and bars](multisets.md).

## Distinct ranks in a reduced deck

Let $R_0=\lbrace 2,3,4,5,6,7,8,9,10\rbrace$ and $S=\lbrace \mathrm{hearts},\mathrm{diamonds},\mathrm{clubs},\mathrm{spades}\rbrace$. The reduced deck $D_0=R_0\times S$ has 36 distinct cards. How many unordered five-card hands have no repeated rank? Consecutive ranks and all-one-suit hands are allowed.

Choose five of the nine ranks and one suit at each selected rank:

$$
\binom{9}{5}4^5=126\cdot1024=129,024.
$$

Each hand specifies its set of ranks and suit at each rank uniquely.

## All-one-suit hands

In the full deck $D=R\times S$ defined above (13 ranks and four suits), how many unordered five-card hands have all cards in the same suit? Such a hand is called a **flush** here, and hands whose ranks are also consecutive are included.

Choose the common suit, then choose five of its 13 rank-suit cards:

$$
4\binom{13}{5}=5148.
$$

The suit is unique in every hand, so the four suit cases are disjoint.
