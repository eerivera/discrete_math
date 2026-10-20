# The Pigeon Hole Principle

Use [F21](../../skills/Combinatorics/F21.md) for proof practice and worked answers. All sets in the cardinality arguments below are finite, and all functions are total.

If 11 pigeons occupy 10 holes, some hole contains at least two pigeons. For $f:A\rightarrow B$, the inputs are the pigeons, the possible outputs are the holes, and $f$ assigns each input to a hole.

**Theorem.** If $|A|>|B|$, then $f:A\rightarrow B$ is not injective: two distinct inputs have the same output.

**Proof.** If $f$ were injective, it would be a bijection from $A$ to $f(A)\subseteq B$. Then $|A|=|f(A)|\le|B|$, contrary to the hypothesis. **Q.E.D.**

Similarly, if $|A|<|B|$, the function cannot be surjective, since $|f(A)|\le|A|<|B|$.

## Fibers and the generalized principle

For $b\in B$, write $f^{-1}(\lbrace b\rbrace)=\lbrace a\in A:f(a)=b\rbrace$ for the **fiber** over $b$. This is an inverse image of a singleton, with no assumption that $f$ has an inverse function. The fibers partition the domain:

$$
A=\bigcup_{b\in B}f^{-1}(\lbrace b\rbrace),\qquad
|A|=\sum_{b\in B}|f^{-1}(\lbrace b\rbrace)|.
$$

Thus $|A|>|B|$ guarantees a fiber of size at least 2. More generally, for an integer $k\ge0$, if $|A|>k|B|$, some fiber has at least $k+1$ elements.

**Proof.** If every fiber had at most $k$ elements, their disjoint union would have at most $k|B|$ elements, contradicting $|A|>k|B|$. **Q.E.D.**

If $|B|>0$, some fiber has size at least $\lceil|A|/|B|\rceil$. For a positive threshold $t$, it suffices that $|A|>(t-1)|B|$ to guarantee a fiber of size at least $t$. Equality does not suffice: exactly $t-1$ elements could occupy each hole.

# Applications

## Subset sums

**Theorem.** Every set $S$ of 20 positive integers less than 10,000 has two distinct subsets with the same sum.

**Proof.** Let $U\subseteq S$. Its sum is a nonnegative integer at most $20\cdot9999=199,980$. This includes the empty subset, whose sum is 0. Define

$$
h:\mathcal P(S)\rightarrow\lbrace 0,1,\ldots,199980\rbrace,
\qquad h(U)=\sum_{u\in U}u.
$$

There are $2^{20}=1,048,576$ subsets and only 199,981 possible outputs in the chosen codomain. By the pigeonhole principle, $h$ is not injective, so distinct subsets have equal sums. **Q.E.D.**

Here is one such set:

$$
\begin{aligned}
S=\lbrace{}&104,1077,1724,2236,2543,3354,3791,4192,4437,4980,\\
&5887,6520,7335,7611,8925,8977,9191,9384,9752,9753\rbrace.
\end{aligned}
$$

The proof guarantees a collision without finding one. To find witnesses by a program, enumerate subsets and store the first subset found for each sum in a dictionary. Encountering that sum again gives a distinct subset with the same sum. A search gives the two subsets $\lbrace 104,2236,3354,9384\rbrace$ and $\lbrace 5887,9191\rbrace$, both with sum 15,078. Adding an element of $S$ outside their union to both subsets gives another pair of distinct subsets with the same sum.

The subsets need not be disjoint. Removing their common elements gives disjoint subsets with equal sums; positivity ensures neither resulting subset is empty.

Return to [F21](../../skills/Combinatorics/F21.md) for fixed-size subset sums, power-set comparisons, and other proof patterns, or the [counting overview](overview.md).

## A set and its square

Let $S$ be a finite set with $n=|S|\ge2$. Prove that no total function $S\rightarrow S\times S$ is surjective and no total function $S\times S\rightarrow S$ is injective.

Since $|S\times S|=n^2>n$, surjectivity in the first direction would require $n\ge n^2$, and injectivity in the second direction would require $n^2\le n$. Both are impossible. **Q.E.D.**

The assumption $n\ge2$ matters: when $n=0$ or $n=1$, $n^2=n$ and the size obstruction disappears.
