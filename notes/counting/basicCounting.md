# Basic Counting Techniques
These notes support [F18](../../skills/Combinatorics/F18.md), [F20](../../skills/Combinatorics/F20.md), and [F21](../../skills/Combinatorics/F21.md). All sets being counted here are finite.

Recall that if $A$ is a finite set then we use the notation $\vert A \vert$ to denote the size
of the set.

---

# The Multiplication Principle:
_The size of a product of sets, is the product of their sizes_

Suppose $A$ and $B$ are sets, then

* $\vert A \times B \vert = \vert A \vert\ *\  \vert B \vert$

and

* $\vert A^n \vert \ = \ \vert A\vert^n$

and more generally, if $\lbrace A_i | 1\le i\le n\rbrace$ is a finite collection of sets, then

* $\vert \prod_{i=1}^n A_i\vert \ = \ \prod_{i=1}^n \vert A_i\vert$

### Applications

**How many binary sequences of length $n$ are there?**

If we let $B=\lbrace 0,1\rbrace$ be the set of two bits, then $B^n$ is the set of binary sequences of length $n$,
and by the multiplication principle, $\vert B^n\vert \  = \ \vert B\vert^n \  = \ 2^n$. So there are $2^n$
binary sequences of length $n$

**License Plates**
Consider hypothetical license plates with the form D LLL DD
where D is one of 10 digits and L is one of 26 letters. Repetition and an initial zero are allowed. How many different license plates can there be?

If we let $L$ be set of 26 letters and $D$ be the set of 10 digits, then each license plate
is an element of $D\times L^3\times D^2$ and the size of this set is

$\vert D\times L^3\times D^2\vert = \vert D \vert^3 * \vert L \vert^3 = 1000*26^3 = 17,576,000$

---

# The Addition Principle
_The size of a disjoint unions of sets is the sum of their sizes_

Suppose $A$ and $B$ are disjoint sets, then

* $\vert A \cup B \vert = \vert A \vert\ +\  \vert B \vert$

and if $A_i$ are disjoint sets, then

* $\vert \bigcup_{i=1}^n A_i\vert \ = \ \sum_{i=1}^n \vert A_i\vert$

This follows directly from what it means for two sets to be disjoint.

### Applications
**Passwords**
Suppose that on a particular system a valid password must have 6,7,or 8 symbols
and the first must be a lowercase letter while the rest can be lowercase letters or digits. What is the size
of the set $V$ of all valid passwords?

If we let $L$ be the set of 26 lowercase letters and $D$ the set of 10 digits, and $S$ the set of 36 lowercase letters or digits.
Then we can use the product rule to calculate the number of passwords of length 6 (V6), length 7 (V7) and length 8 (V8).
Since these are disjoint sets, we add their sizes to get the size of $V$.

* $\vert V6 \vert = \vert L \vert * \vert S \vert^5 = 26*36^5$
* $\vert V7 \vert = \vert L \vert * \vert S \vert^6= 26*36^6$
* $\vert V8 \vert = \vert L \vert * \vert S \vert^7= 26*36^7$
* $\vert V \vert = \vert V6\vert + \vert V7\vert + \vert V8\vert = 26 * 36^5 +26 * 36^6 +26 * 36^7$

So the total number of valid passwords is $26 * 36^5 +26 * 36^6 +26 * 36^7$.

---

# Principle of Inclusion and Exclusion
Let $A$ and $B$ be two sets which are not necessarily disjoint, then

$\vert A \cup B \vert = \vert A \vert + \vert B \vert - \vert A \cap B \vert$

To see why, observe that every element of $A \cap B$ will be counted twice, once in $\vert A\vert$ and once in $\vert B \vert$
so subtracting $\vert A \cap B \vert$ removes that double counting.

Similarly if $A,B,C$ are sets

$\vert A \cup B \cup C \vert = \vert A \vert + \vert B \vert +\vert C\vert - \vert A \cap B \vert - \vert A \cap C \vert - \vert B \cap C \vert+\vert A \cap B \cap C\vert$

### Applications

**FizzBuzz**
How many integers in the range [1,100] are divisible by 3 or by 5?

This is the basis of the FizzBuzz
challenge where you count from 1 to 100 but say fizz for numbers divisible by 3 and buzz for numbers divisible by 5, e.g. you can play this with a group of friends taking turns (but its not so fun for one person if the number of friends is 3 or 5)

1 2 fizz 4 buzz fizz 7 8 fizz buzz 11 fizz 13 14 fizzbuzz 16 17 fizz 19 buzz ...

Let $A_n$ be the set of numbers in [1,100] which are divisible by $n$.
We want to know the size of $A = A_3\cup A_5$

Observe that $\vert A_n\vert =$ 100//n  where a//b means divide a by b and throw away the remainder.
(Why?)

So $\vert A\vert = \vert A_3\vert + \vert A_5\vert - \vert A_3\cap A_5\vert$

but $A_3\cap A_5$ is the numbers divisible by 3 and 5, i.e. by 15, so

* $\vert A_3\vert =100{\text //}3 = 33$
* $\vert A_5\vert =100{\text //}5 = 20$
* $\vert A_3\cap A_5\vert = \vert A_{15}\vert = 100{\text //}15 = 6$
* $\vert A \vert = 33 + 20 - 6 = 53-6 = 47$

### FizzBuzzZapp
Now, find the number of integers in [1,100] which are not divisible by 2, 3, or 5.

To do this, we first find the number which are divisible by 2,3, or 5 and then subtract that from 100.
Using the inclusion exclusion principle, let $A= A_2$, $B=A_3$ and $C=A_5$ then

* $\vert A_2 \vert = 50$
* $\vert A_3\vert =33$
* $\vert A_5 \vert = 20$
* $\vert A_2\cap A_3 \vert = \vert A_6\vert = 16$
* $\vert A_2\cap A_5 \vert = \vert A_{10}\vert = 10$
* $\vert A_3\cap A_5 \vert = \vert A_{15}\vert = 6$
* $\vert A_2\cap A_3 \cap A_5 \vert = \vert A_{30}\vert = 3$

so

$\vert A \cup B \cup C \vert = \vert A \vert + \vert B \vert +\vert C\vert - \vert A \cap B \vert - \vert A \cap C \vert - \vert B \cap C \vert+\vert A \cap B \cap C\vert$

$= 50 +33 +20 - (16+10+6) + 3 = 103 - 32 + 3= 71+3=74$

So the number of integers in the range [1,100] which are divisible by 2,3, or 5 is 74.

So the number of integers in the interval [1,100] which are not divisible by 2,3, or 5,
is 100-74 = 26.

---

# Counting Subsets
Another useful rule is that the number of subsets $S$ of a set $A$ of size $n$ is $2^n$.
We can see this is true by associating each subset $S$ of $A= \lbrace a_1,a_2,a_3,\ldots,a_n\rbrace$ with a binary sequence $(b_1,b_2,\ldots,b_n)$ of length $n$ where

$$
b_i=
\left\lbrace
\begin{array}{ll}
1 &\text{if }a_i\in S \\
0 &\text{if }a_i\not\in S
\end{array}
\right.
$$

Since there are $2^n$ binary sequences of length $n$ there must then be $2^n$ subsets $S$ of $A$.

We are using the bijection principle here with $f$ mapping length n bit strings one-one and onto the subsets of an n element set.

---

# The Bijection principle

If $f:A\rightarrow B$ is a bijection, where $A$ and $B$ are finite sets, then $A$ and $B$ have the same size, that is $\vert A\vert = \vert B \vert$.

### Applications.
We'll show how to use the Bijection Principle to count the number of functions between two sets.

**Theorem.** Let $T_{A,B}$ be the set of total functions from $A$ to $B$,
then

* $\vert T_{A,B}\vert = \vert B \vert ^{\vert A\vert}$

**Proof:**
Let $A=\lbrace a_1,\ldots,a_r\rbrace$ be a set with $r$ elements,
and let $B=\lbrace b_1,\ldots,b_s\rbrace$ be a set with $s$ elements.
We will define a bijection

* $\phi: T_{A,B} \rightarrow B^{\vert A\vert}$

and this will prove our Theorem since the size of $B^r$ is $\vert B\vert^r$.

The correspondence $\phi$ maps a total function $g$ to its sequence of outputs $(g(a_1),\ldots,g(a_r))$. Different functions differ at some input, so these sequences differ and $\phi$ is injective. For every sequence $s=(s_1,\ldots,s_r)\in B^r$, define $f_s(a_i)=s_i$. Then $\phi(f_s)=s$, proving surjectivity. Thus $\phi$ is bijective, and the number of total functions is $|B|^r$.

The individual function $f_s$ need not be injective: the sequence may repeat entries. It is the correspondence between functions and sequences that is bijective. **Q.E.D.**

There is one total function from an empty domain to any codomain, including an empty codomain; there are no total functions from a nonempty domain to an empty codomain. The empty-choice case $0^0$ represents 1 in this counting formula.

Continue with [permutations and combinations](permsAndCombs.md), or return to the [counting overview](overview.md).

# Additional applications

## Strings and numerals

1. How many plates have the form DDDLLL, with 10 digits and 26 uppercase letters, allowing repetition and initial zeros? There are $10^3\cdot26^3$ plates: choose each coordinate independently.
2. How many usernames of length 4 through 8 can be formed from 26 lowercase letters, 10 digits, and the four symbols `.`, `-`, `*`, `_`? There are 40 choices per position. Different lengths are disjoint, giving $40^4+40^5+40^6+40^7+40^8=40^4(40^5-1)/39$.
3. How many four-character usernames start with an uppercase or lowercase letter and use letters or digits afterward? There are 52 first-character choices and 62 choices at each later position: $52\cdot62^3$.
4. How many five-digit octal numerals are there, using digits 0 through 7 and excluding an initial zero? The first position has 7 choices and the others 8 each, giving $7\cdot8^4$.
5. How many eight-character hexadecimal strings are there, allowing initial zeros? A hexadecimal digit is one of $0,1,\ldots,9,a,b,c,d,e,f$, with the letters representing 10 through 15. Each digit encodes four bits, so there are $16^8=2^{32}$ strings. For an eight-digit numeral that excludes an initial zero, the count would instead be $15\cdot16^7$.

## Card categories

A card is a pair $(r,s)$ with rank $r$ and suit $s$. In this section let

$$
R=\lbrace 2,3,4,5,6,7,8,9,10,J,Q,K,A\rbrace,\qquad
S=\lbrace \mathrm{hearts},\mathrm{diamonds},\mathrm{clubs},\mathrm{spades}\rbrace.
$$

The deck $D=R\times S$ contains one of each rank-suit pair, giving 52 distinct cards. Define the **face-card ranks for this problem** to be J, Q, K, A, explicitly including the ace. Let $H$ contain all hearts and let $F$ contain the cards of these four ranks. Find $|H\cup F|$.

There are 13 hearts, $4\cdot4=16$ specified face cards, and 4 hearts in those ranks. Inclusion and exclusion gives

$$
|H\cup F|=13+16-4=25.
$$

Return to [F18](../../skills/Combinatorics/F18.md) for constructing counts or [F20](../../skills/Combinatorics/F20.md) for overlaps.
