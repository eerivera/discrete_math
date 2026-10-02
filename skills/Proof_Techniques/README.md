# Overview of Proofs

In this unit we discuss different proof techniques
and practice using these techniques to create clear and convincing arguments
of the truth of mathematical statements. These are fundamental skills for
Computer Scientists as there are many cases where we want to clearly explain why
our algorithms and programs are correct and efficient, and the best way to do that is with a
well-designed proof.

## Skills in this unit

| Skill | Focus |
| --- | --- |
| [F08](F08.md) | Direct proofs, contrapositives, and both directions of an iff statement |
| [F09](F09.md) | Contradiction and irrationality proofs |
| [F10](F10.md) | Exhaustive cases |
| [F11](F11.md) | Ordinary and strong induction |
| [G03](G03.md) | Combining methods, including well-ordering |

Each skill page contains practice problems, a tutorial, worked answers, and readings. In a complete proof, state the domain and assumptions, explain why each step follows, and end with the claimed conclusion. Numerical examples can suggest a theorem but do not prove a universal claim over an infinite domain. See [Features of a Good Proof](../../notes/proofs/goodProofFeatures.md) for guidance on writing.

## Nomenclature
We often label the results that we prove as one of the following kinds of statements:
* **Theorem** - this is a major result which is interesting in its own right
* **Proposition** - this is a true fact which is somewhat interesting, but mainly because it is used to prove a theorem
* **Lemma** - this is a true result, which is only interesting because it is used to prove other more interesting things.

* **Corollary** - a result that follows readily from a theorem already proved.

These labels describe how results are used; all require justification.

There are usually many different ways we prove that an argument is valid.
We have seen that there are formal methods for proving validity, but these quickly
become too messy and complex when trying to prove interesting propositions, so we
will focus on "informal" proofs.

We will learn how to use the following proof techniques:
* **direct proof** - show that the conclusion follows from the premises by direct application of the premises
* **contrapositive proof** - to show that $A\rightarrow B$, prove the equivalent $\neg B \rightarrow \neg A$
    <br> $(A\rightarrow B) \equiv (\neg A \vee B) \equiv (\neg\neg B \vee \neg A) \equiv (\neg B \rightarrow \neg A)$
* **proofs of iff statements** - to prove $A\leftrightarrow B$ we must prove $A\rightarrow B$ and $A\leftarrow B$
  to show that $A$ and $B$ are either both True or both False.
* **proof by contradiction** - assuming that the conclusion is False and using  the premises to generate a contradiction, which shows the conclusion can not be False
    <br> $((P\wedge \neg C)\rightarrow \mathrm{False}) \equiv \neg (P \wedge \neg C) \equiv (\neg P \vee C) \equiv (P \rightarrow C)$
* **proof by cases** - showing that $a_1\rightarrow c$ and  $a_2\rightarrow c$ and $\ldots$ and $a_n\rightarrow c$ and at least one of $a_1,a_2,\ldots,a_n$ must be True, so $c$ must be True.
   <br> $(A_1\vee A_2\vee\ldots\vee A_n)$  <br>$(A_1\rightarrow C)$<br>$(A_2\rightarrow C)$
  <br>$\ldots$<br>$(A_n \rightarrow C)$<br>----------------------<br> $C$
* **proof by induction** - showing that some statement P(n) is True for every $n\ge 0$ (with $n$ ranging over the natural numbers) by showing it is True for $n=0$ and
  showing that $\forall n . (P(n) \rightarrow P(n+1))$, hence $P(0)$ is True and so is $P(1)$ and $P(2)$ and $P(3)$ etc....

  $P(0)$<br>
  $\forall n . (P(n) \rightarrow P(n+1))$
  <br>----------------------<br>
  $\forall n . P(n)$

Ideally we want to find the simplest, clearest, most convincing argument that something is true, and we may need to
try different proof techniques to find the best one.

Let's look at some examples, and have you try to create your own proofs...

## Proofs by cases
This is a very common approach. Suppose we want to prove that some statement $C$ is True.
If we can find statements $A$ and $B$ such that at least one of them is True, and we can show that each implies $C$
(i.e. we show $C$ is True in each of these two cases), then we know $C$ must always be True.
* $((A\vee B) \wedge (A\rightarrow C) \wedge (B\rightarrow C)) \rightarrow C$

Let's use this to prove that $n^2 + n$ is always even, by looking at the two cases $n$ is even and $n$ is odd.

__Theorem.__ for any integer $n$, the value $n^2+n$ is even.

__Proof:__
We will prove this by considering two cases: $n$ is even or $n$ is odd.

* case 1: assume $n$ is even, then $n=2k$ so $n^2+n = (2k)^2 + 2k = 4k^2+2k = 2(2k^2+k)$ is a multiple of 2, hence even.
* case 2: assume $n$ is odd, then $n=2k+1$ so $n^2 +n = 4k^2 + 4k + 1 + 2k +1 = 4k^2 + 6k + 2 = 2(2k^2+3k+1)$ is a multiple of 2, hence even.

Since $n$ must either be even or odd, and in both cases $n^2+n$ is even, we see that $n^2+n$ is even for all $n$. __Q.E.D.__

Note: we could prove this directly by noting that $n^2+n = n(n+1)$ and since either $n$ or $n+1$ must be even, so must their product!

Here is another example of a proof by cases.

__Theorem__  Assume we paint a square 1x1 panel with 2 colors (say black and white), including its boundary, then there must be 2 points of the same color which are exactly 1 unit apart.

Here is an example of such a panel:

![2 color painting](https://nukeart.com/cdn/shop/files/abstract-painting-bound-by-opposites-484947.jpg?v=1724032326&width=100)

__Proof__ pick two adjacent corners of the square.
* Case 1. The colors of the two corners are the same.  In this case we are done as they are 1 unit apart.
* Case 2. The colors are different.  In this case there is a point P inside the square which makes an equilateral triangle with the two corners. Since the two corners have different colors, one is black and the other is white. So we again have two cases, depending on the color of the point P.
   *  if the point P is black, then it is 1 unit away from the black corner, and
   *  if it is white, then it is one unit away from the white corner,
so in either case there are two points of the same color exactly 1 unit apart.

We have shown in both cases that there are two points with the same color exactly one unit apart, so the Theorem is true. __Q.E.D.__

## Proof by contradiction
This is the method we've been using in our formal proofs. To prove that $A \rightarrow B$, assume $A$ is True but $B$ is False and show this generates a contradiction and hence can't be True.  Thus whenever $A$ is True, $B$ can't be False, so $B$ must also be True.

Let's use this to prove that $n^2$ is odd implies $n$ is odd.

**Proof:**
Suppose that $n^2$ is odd, but $n$ is not odd. Then $n$ must be even.
<br>
So $n=2k$ for some integer $k$, so $n^2 = (2k)^2 = 2(2k^2)$ is a multiple of 2 and hence is even.
<br>
This contradicts our premise that $n^2$ is odd, so $n$ can not be even, so it must be odd.
<br>
**QED**

## Interesting Application.
Let's use these techniques to prove something more interesting, that the square root of 2 is irrational, that is, can't be expressed as a fraction $a/b$ where $a$ and $b$ are integers.

**Theorem**  $\sqrt{2}$ is an irrational number.

**Proof**
We will prove this by contradiction. Assume $\sqrt{2} = a/b$ for positive integers $a$ and $b$, with $b\ne 0$.

Divide $a$ and $b$ by their greatest common divisor to put the fraction in lowest terms. This preserves its value and makes $\gcd(a,b)=1$.

Thus they cannot both be even, since otherwise 2 would be a common divisor.

so $\sqrt{2}=a/b$ iff $2 = (a/b)^2$ iff $2=a^2/b^2$ iff $2b^2 = a^2$. So $a^2$ is even, and hence $a$ must be even by the square-parity result proved in [F08](F08.md): an integer has an even square if and only if it is even.

Hence $a=2k$ for some integer $k$.

Thus $2b^2=a^2$ iff $2b^2=(2k)^2$ iff $2b^2 = 4k^2$ iff $b^2=2k^2$ by factoring 2 out of both sides.

So $b^2$ is even, hence by our results above $b$ must be even.

But we chose $a$, $b$ so that $a/b$ was in lowest terms and hence they can't both be divisible by $2$.

This contradiction shows that $\sqrt{2}$ can not be a rational number, hence it is irrational.

**QED**

## Further practice

The examples above introduce cases and contradiction. Continue with [F08](F08.md) for direct and contrapositive proofs, [F11](F11.md) for the sum, recurrence, parse-tree, and chocolate-bar induction examples, and [G03](G03.md) for combined proofs and least counterexamples.
