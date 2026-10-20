# Functions

The [Functions unit](../../skills/Functions/README.md) provides tutorials, exam-style practice, and worked answers for [F15](../../skills/Functions/F15.md), [F16](../../skills/Functions/F16.md), and [F17](../../skills/Functions/F17.md). These notes collect the definitions and additional constructions, including products of functions, inverse functions, and bijections between sets.

## Domains, codomains, and partial functions

A total function $f:A\rightarrow B$ assigns exactly one value $f(a)\in B$ to each input $a\in A$. The set $A$ is the **domain**, and $B$ is the **codomain**. Distinct inputs may have the same output.

A partial function may leave some inputs without a value. Let $D_f\subseteq A$ be its set of defined inputs; it is total precisely when $D_f=A$. This course sometimes uses $f:A\rightarrow B$ for partial functions when explicitly stated. Otherwise assume functions are total.

For example, $r(x)=\sqrt{x}$ with stated domain and codomain $\mathbb R$ is partial, with $D_r=[0,\infty)$. It becomes total when its domain is restricted to $[0,\infty)$. A formula must also respect its codomain: $x\mapsto x-1$ is total on $\mathbb Z$, but does not give a total function $\mathbb N\rightarrow\mathbb N$ when $0\in\mathbb N$.

## Ways to define functions

Functions can be defined by a table of values, an algebraic formula, a verbal rule such as “the $n$th prime” for $n\geq1$, or cases. For example, absolute value on $\mathbb R$ is

$$
a(x)=\begin{cases}
x &\text{if }x\geq0,\\
-x &\text{if }x<0.
\end{cases}
$$

Evaluate the condition before using a branch. For totality, every input needs a value; for a valid function, overlapping branches must agree wherever they both apply. A complete partial table leaves unlisted inputs undefined.

Two other examples illustrate tables and formulas. The total function $b:\lbrace \mathrm{True},\mathrm{False}\rbrace\rightarrow\lbrace 0,1\rbrace$ is given by $b(\mathrm{True})=1$ and $b(\mathrm{False})=0$. The formula $q(x)=x+1/x$ with stated domain and codomain $\mathbb R$ is partial, defined exactly when $x\ne0$. Both examples require the stated input and output sets as well as the rule.

## Surjections, injections, and bijections

A function is **injective** or **one-to-one** when equal defined outputs imply equal inputs:

$$
\forall a_1\in D_f . \forall a_2\in D_f . (f(a_1)=f(a_2)\rightarrow a_1=a_2).
$$

A function is **surjective** or **onto** when every codomain element is reached:

$$
\forall b\in B . \exists a\in D_f . f(a)=b.
$$

For total functions, replace $D_f$ with $A$. We sometimes write $f:A\hookrightarrow B$ for an injection and $f:A\twoheadrightarrow B$ for a surjection.

Following the exam convention, partial functions may be injective or surjective on their defined values. A **bijection between $A$ and $B$** is total, injective, and surjective: it gives a one-to-one correspondence between the entire sets. A partial injective surjection instead gives a bijection from $D_f$ to $B$.

To disprove injectivity, give two distinct defined inputs with the same output. To disprove surjectivity, give a target with no preimage. To prove injectivity, start with equality of outputs and deduce equality of inputs. To prove surjectivity, take an arbitrary target and construct an allowed input mapping to it. [F17](../../skills/Functions/F17.md) develops these proofs and explains restrictions of domains and changes of codomains.

### Exercise 1

Classify these rules with stated domain and codomain $\mathbb R$: $f(x)=x^2$, $g(x)=x^3$, and the partial function $h(x)=\sqrt{x}$ defined for $x\geq0$.

**Answers.** The square function is total, but not injective ($f(-1)=f(1)$) or surjective (it misses $-1$). The cube function is total, injective (equality of cubes implies equality of real inputs), and surjective (a target $y$ has preimage $\sqrt[3]y$). The square-root rule is partial, injective on its defined inputs, and not surjective onto $\mathbb R$, since it misses all negative targets.

## Functions on subsets of a domain

For $S\subseteq A$, the **image** of $S$ under a total function is

$$
f(S)=\lbrace f(x)\mid x\in S\rbrace.
$$

For a partial function, use $S\cap D_f$ instead of $S$. Undefined inputs contribute no values. List each output exactly once, even if several inputs produce it. The **range** is $f(A)$; it may be smaller than the codomain.

The induced image map can be written

$$
f_*:\mathcal P(A)\rightarrow\mathcal P(B),\qquad f_*(S)=f(S).
$$

Here $\mathcal P(A)=2^A$ is the power set. When a function itself has sets as inputs, check the types to distinguish its value at a set from its image of a collection of inputs.

For example, let $E$ and $O$ be the even and odd integers. For $f(n)=n+1$ and $g(n)=2n$, both from $\mathbb Z$ to $\mathbb Z$, we have $g(\mathbb Z)=E$, $f(E)=O$, and $f(O)=E$.

## Inverse images

For $T\subseteq B$, the **inverse image** or **preimage** is

$$
f^{-1}(T)=\lbrace a\in D_f\mid f(a)\in T\rbrace.
$$

Thus the inverse-image map, unlike the image map, goes backward between power sets:

$$
f^{-1}:\mathcal P(B)\rightarrow\mathcal P(A).
$$

Every function has inverse images of subsets; it need not have an inverse function. To ask for all inputs mapping to a single target $b$, write $f^{-1}(\lbrace b\rbrace)$.

### Exercise 2

Let $f(x)=2x+1$.

1. Find the range when the domain and codomain are $\mathbb Z$.
2. Find the range when the domain and codomain are $\mathbb R$.
3. On $\mathbb R$, find $f([2,4])$ and $f^{-1}([2,4])$.

**Answers.** On $\mathbb Z$, the range is $\lbrace 2n+1\mid n\in\mathbb Z\rbrace$, the odd integers. On $\mathbb R$, the range is $\mathbb R$, because a target $y$ has preimage $(y-1)/2$. The interval image is $[5,9]$, and solving $2\leq2x+1\leq4$ gives the inverse image $[1/2,3/2]$.

## Composition of functions

For total $g:A\rightarrow B$ and $f:B\rightarrow C$,

$$
f\circ g:A\rightarrow C,\qquad (f\circ g)(a)=f(g(a)).
$$

Apply $g$ first, then $f$. The output of the inner function must be an allowed input to the outer function. For partial functions, the composition is defined exactly at inputs where both successive steps are defined.

Composition is associative: both $(f\circ g)\circ h$ and $f\circ(g\circ h)$ send $x$ to $f(g(h(x)))$. It is not generally commutative. The identity function $\operatorname{id}_A(a)=a$ satisfies $f\circ\operatorname{id}_A=f$ and $\operatorname{id}_B\circ f=f$ for $f:A\rightarrow B$.

For set aggregation, use finite subsets when a sum or product over all members is intended. Write $\mathcal P_{\mathrm{fin}}(A)$ for those subsets. The empty sum is 0; the empty product is 1. Restrict positive-divisor aggregation to positive integer inputs, since every positive integer divides 0. See [F16](../../skills/Functions/F16.md) for tuple, divisor, and filtering compositions.

### Exercise 3

Let $f:\mathbb R\rightarrow\mathbb R$ be $f(x)=x^2+2$, $g:\mathbb R^2\rightarrow\mathbb R$ be $g(a,b)=a+b$, and $h:\mathbb R\rightarrow\mathbb R^2$ be $h(x)=(x^2+1,2x)$. Find $g\circ h$, $h\circ f$, and $g\circ h\circ f$.

**Answers.**

$$
\begin{aligned}
(g\circ h)(x)&=x^2+1+2x=(x+1)^2,\\
(h\circ f)(x)&=((x^2+2)^2+1,2(x^2+2)),\\
(g\circ h\circ f)(x)&=(x^2+2)^2+1+2(x^2+2)=x^4+6x^2+9.
\end{aligned}
$$

In the other direction, $f\circ g:\mathbb R^2\rightarrow\mathbb R$ sends $(a,b)$ to $(a+b)^2+2=a^2+2ab+b^2+2$. The domain and output type help distinguish this composition from $g\circ h$.

## Images and inverse images of compositions

For total $g:A\rightarrow B$, $f:B\rightarrow C$, $S\subseteq A$, and $T\subseteq C$,

$$
(f\circ g)(S)=f(g(S)),\qquad
(f\circ g)^{-1}(T)=g^{-1}(f^{-1}(T)).
$$

The first equality follows because both sides collect outputs $f(g(s))$ for $s\in S$. For the second, an input $a$ is on the left exactly when $f(g(a))\in T$, equivalently $g(a)\in f^{-1}(T)$, equivalently $a\in g^{-1}(f^{-1}(T))$. These rules also hold for partial functions when only defined values are used.

## Product of functions

Let $f:A\rightarrow C$ and $g:B\rightarrow D$ be total. Their **product function** acts independently on two coordinates:

$$
f\times g:A\times B\rightarrow C\times D,\qquad
(f\times g)(a,b)=(f(a),g(b)).
$$

The result is a pair, rather than a numerical product. With partial functions, both coordinate values must be defined.

### Exercise 4

Let $j,k:\mathbb N\rightarrow\mathbb N$ be $j(x)=2x$ and $k(y)=y^2+1$. Let $s:\mathbb N^2\rightarrow\mathbb N$ be $s(u,v)=u+v$. Find $j\times k$ and $s\circ(j\times k)$.

**Answers.** The product $j\times k:\mathbb N^2\rightarrow\mathbb N^2$ sends $(x,y)$ to $(2x,y^2+1)$. The composition $s\circ(j\times k):\mathbb N^2\rightarrow\mathbb N$ sends $(x,y)$ to $2x+y^2+1$. The coordinates $x$ and $y$ are independent inputs.

## More worked finite examples

### Exercise 5: Images and inverse images

Let $g:\lbrace a,b,c,d\rbrace\rightarrow\lbrace 1,2,3,4,5\rbrace$ have values $g(a)=2$, $g(b)=5$, $g(c)=2$, and $g(d)=4$. Find $g(\lbrace a,b,c\rbrace)$ and $g^{-1}(\lbrace 1,2,3\rbrace)$.

**Answers.** The outputs at $a,b,c$ are $2,5,2$, so the image is $\lbrace 2,5\rbrace$. Both $a$ and $c$ map to 2, and no input maps to 1 or 3. Thus the inverse image is $\lbrace a,c\rbrace$.

### Exercise 6: Partial functions and restrictions

Let $f:\lbrace 0,1,2,3,4,5\rbrace\rightarrow\lbrace a,b,c,d,e\rbrace$ have exactly the defined values $f(0)=b$, $f(2)=c$, $f(3)=d$, $f(4)=c$, and $f(5)=e$. Classify $f$ and these restrictions as total, surjective, and injective:

1. $g:\lbrace 0,2,4\rbrace\rightarrow\lbrace b,c\rbrace$.
2. $h:\lbrace 1,3,5\rbrace\rightarrow\lbrace d,e\rbrace$.

**Answers.** The original $f$ is not total because it is undefined at 1, not surjective because it misses $a$, and not injective because $f(2)=f(4)=c$. The restriction $g$ is total and surjective but not injective: all three inputs have values, its range is $\lbrace b,c\rbrace$, and $g(2)=g(4)$. The restriction $h$ is not total because it is still undefined at 1. Its defined values $h(3)=d$ and $h(5)=e$ reach its whole codomain and are distinct, so it is surjective and injective on its defined inputs.

## Inverse functions

A total function $f:A\rightarrow B$ has a two-sided **inverse function** $f^{-1}:B\rightarrow A$ exactly when $f$ is bijective. For each $b\in B$, surjectivity supplies a preimage and injectivity makes it unique. The two identities are

$$
f^{-1}\circ f=\operatorname{id}_A,\qquad
f\circ f^{-1}=\operatorname{id}_B.
$$

Conversely, these identities force injectivity and surjectivity. If $f(a_1)=f(a_2)$, applying $f^{-1}$ gives $a_1=a_2$. Every $b\in B$ is reached at $f^{-1}(b)$ because $f(f^{-1}(b))=b$.

Inverse-function notation takes a single target to a single input. Inverse-image notation takes a subset to a subset and is available even without bijectivity. If $f$ is bijective, the two uses agree in the sense that the inverse image of $T$ is the image of $T$ under the inverse function.

For bijective $g:A\rightarrow B$ and $f:B\rightarrow C$,

$$
(f\circ g)^{-1}=g^{-1}\circ f^{-1}.
$$

**Proof.** Put $k=g^{-1}\circ f^{-1}$. Associativity and the inverse identities give

$$
\begin{aligned}
k\circ(f\circ g)&=g^{-1}\circ(f^{-1}\circ f)\circ g
=g^{-1}\circ g=\operatorname{id}_A,\\
(f\circ g)\circ k&=f\circ(g\circ g^{-1})\circ f^{-1}
=f\circ f^{-1}=\operatorname{id}_C.
\end{aligned}
$$

Thus $k$ is the inverse of $f\circ g$. **Q.E.D.** The order reverses because undoing a sequence starts with its last operation.

## Constructing bijections between sets

To construct a bijection, specify its domain, codomain, and rule, then prove totality, injectivity, and surjectivity. An explicit inverse can establish the last two properties.

For example, let $O=\lbrace 2n+1\mid n\in\mathbb Z\rbrace$ be the odd integers. The function $b:\mathbb Z\rightarrow O$ defined by $b(n)=2n+1$ is total. If $b(n)=b(m)$, then $2n+1=2m+1$, so $n=m$. Every $y\in O$ has the integer preimage $(y-1)/2$. Hence $b$ is a bijection, with inverse $b^{-1}(y)=(y-1)/2$.

We sometimes call sets with a bijection **isomorphic as sets**. In structures such as ordered sets or graphs, an isomorphism must also preserve the relevant structure. Infinite examples lead into [G07: Countability](../../skills/Sets/G07.md).

## Further proof practice

[F17](../../skills/Functions/F17.md#further-practice) gives proofs about injectivity and surjectivity under composition and about images and inverse images. In particular, for total $f:A\rightarrow B$,

$$
f(f^{-1}(T))=T\cap f(A)\quad(T\subseteq B).
$$

Thus $f(f^{-1}(T))=T$ holds for every subset of the codomain exactly when $f$ is surjective. Without that condition, the equality can fail: a target outside the range has empty inverse image. This statement concerns inverse images of sets, so it does not require an inverse function.

## Readings

* [Introduction to functions, in Discrete Mathematics: An Open Introduction](https://discrete.openmathbooks.org/dmoi3/sec_intro-functions.html)
* [Chapter 4.3: Functions, in Mathematics for Computer Science](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-spring-2015/mit6_042js15_textbook.pdf)
