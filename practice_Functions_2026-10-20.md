# Functions practice — October 20, 2026

Additional practice for F15 and F17. Explain your reasoning and list each element of a set exactly once. For partial functions, form images and inverse images using only defined values. Worked answers follow the questions.

## Problem 1: Domain, codomain, and range

Let $A=\lbrace r,s,t,u,v\rbrace$, $B=\lbrace 0,1,2,3,4,5\rbrace$, and $f:A\rightarrow B$ be given by

| $x$ | $r$ | $s$ | $t$ | $u$ | $v$ |
| --- | --- | --- | --- | --- | --- |
| $f(x)$ | 4 | 1 | 4 | 0 | 3 |

State the domain, codomain, and range of $f$. Which codomain elements are never reached?

## Problem 2: Empty images and inverse images

Let $C=\lbrace a,b,c,d,e,f\rbrace$ and $D=\lbrace p,q,r,s,t\rbrace$. A partial function $g:C\rightarrow D$ has exactly these defined values:

$$
g(a)=q,\quad g(c)=s,\quad g(d)=q,\quad g(f)=p.
$$

Find $g(\lbrace b,e\rbrace)$ and $g^{-1}(\lbrace r,t\rbrace)$. Explain why each result is empty.

## Problem 3: Evaluating a finite formula

Let $E=\lbrace -2,-1,0,1,2\rbrace$, $F=\lbrace 0,1,2,4,6,9\rbrace$, and $h:E\rightarrow F$ be $h(x)=(x+1)^2$.

Make a table of values and find $h(\lbrace -1,0,2\rbrace)$.

## Problem 4: Comparing domains and codomains

Classify each function as total, surjective, and injective. Which are bijections?

1. $f:\mathbb R\rightarrow\mathbb R$, $f(x)=(x-2)^2$.
2. $g:\mathbb R\rightarrow[0,\infty)$, $g(x)=(x-2)^2$.
3. $h:[2,\infty)\rightarrow[0,\infty)$, $h(x)=(x-2)^2$.
4. $j:\mathbb R\rightarrow\mathbb R$, given by $j(x)=\sqrt{x+1}$ exactly when $x\geq-1$, and undefined otherwise.
5. $k:\mathbb Q^+\rightarrow\mathbb Q^+$, $k(x)=x^2/2$, where $\mathbb Q^+$ is the set of positive rational numbers.
6. $\ell:\mathbb R\rightarrow\mathbb R$, $\ell(x)=(x+1)^3-4$.
7. $r:\mathbb N\rightarrow\mathbb N$, $r(n)=n(n+1)$, with $\mathbb N=\lbrace 0,1,2,\ldots\rbrace$.

---

# Worked answers

## Problem 1

The domain is $A$, the codomain is $B$, and the range is $\lbrace 0,1,3,4\rbrace$. The codomain also contains 2 and 5, which are never reached.

## Problem 2

Both sets are $\emptyset$. Neither $b$ nor $e$ has a value, so no output is contributed to the image. None of the defined outputs is $r$ or $t$, so the inverse image contains no inputs.

## Problem 3

| $x$ | $-2$ | $-1$ | $0$ | $1$ | $2$ |
| --- | --- | --- | --- | --- | --- |
| $h(x)$ | 1 | 0 | 1 | 4 | 9 |

The outputs at $-1,0,2$ are $0,1,9$, respectively. Thus $h(\lbrace -1,0,2\rbrace)=\lbrace 0,1,9\rbrace$.

## Problem 4

| Function | Total? | Surjective? | Injective? | Bijection? |
| --- | --- | --- | --- | --- |
| $f:\mathbb R\rightarrow\mathbb R$ | Yes | No | No | No |
| $g:\mathbb R\rightarrow[0,\infty)$ | Yes | Yes | No | No |
| $h:[2,\infty)\rightarrow[0,\infty)$ | Yes | Yes | Yes | Yes |
| Partial $j:\mathbb R\rightarrow\mathbb R$ | No | No | Yes | No |
| $k:\mathbb Q^+\rightarrow\mathbb Q^+$ | Yes | No | Yes | No |
| $\ell:\mathbb R\rightarrow\mathbb R$ | Yes | Yes | Yes | Yes |
| $r:\mathbb N\rightarrow\mathbb N$ | Yes | No | Yes | No |

1. The square is defined and real for every real input. Negative targets such as $-1$ are missed. There is a collision $f(1)=f(3)=1$.
2. The same formula is still total and still has the collision at 1 and 3. For every target $y\geq0$, the real input $x=2+\sqrt y$ gives $g(x)=y$, so it is onto its smaller codomain.
3. For every target $y\geq0$, $x=2+\sqrt y$ lies in $[2,\infty)$ and maps to $y$. If $(x_1-2)^2=(x_2-2)^2$, both $x_i-2$ are nonnegative, so taking nonnegative square roots gives $x_1=x_2$. The rule is defined throughout its domain.
4. There is no value at $-2$, so $j$ is not total. Its range is $[0,\infty)$, which misses $-1$ in the codomain. If two defined outputs are equal, squaring gives $x_1+1=x_2+1$, hence $x_1=x_2$.
5. Squaring a positive rational and dividing by 2 gives a positive rational, so $k$ is total. If $x_1^2/2=x_2^2/2$, then $x_1^2=x_2^2$ and positivity forces $x_1=x_2$, proving injectivity. The target 1 would require $x=\sqrt2$, which is not rational, so $k$ is not onto. The [irrationality proof in F09](skills/Proof_Techniques/F09.md#interesting-application) justifies that missing preimage.
6. The formula is real and defined for every real input. If $(x_1+1)^3-4=(x_2+1)^3-4$, taking real cube roots gives $x_1=x_2$. Every real target $y$ has real preimage $x=\sqrt[3]{y+4}-1$, since $(x+1)^3-4=y$. Thus $\ell$ is total, injective, and surjective.
7. The product $n(n+1)$ is a natural number for every $n\in\mathbb N$, so $r$ is total. If $n(n+1)=m(m+1)$, then $(n-m)(n+m+1)=0$. Since $n+m+1>0$, this forces $n=m$, proving injectivity. The target 1 is missed: $r(0)=0$, and for $n\geq1$ we have $r(n)\geq2$.
