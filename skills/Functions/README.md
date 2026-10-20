# Overview of Functions

Functions associate inputs with outputs. These skills develop function notation, compositions that pass outputs into other functions, and proofs about the ways functions map one set to another.

## Skills in this unit

| Skill | Focus | Related course notes |
| --- | --- | --- |
| [F15](F15.md) | Domains, codomains, range; tables, formulas, and cases; images and inverse images | [Function definitions](../../notes/math_data_types/functions.md#domains-codomains-and-partial-functions) |
| [F16](F16.md) | Composition on numbers, tuples, and finite sets; intermediate types; general formulas | [Composition](../../notes/math_data_types/functions.md#composition-of-functions) |
| [F17](F17.md) | Totality, injectivity, surjectivity, bijectivity; restrictions, definitions, and proofs | [Function properties](../../notes/math_data_types/functions.md#surjections-injections-and-bijections) |

Each skill page contains practice problems, a tutorial, and worked answers. In F15, calculate images and inverse images of finite sets. In F16, evaluate compositions and derive formulas. In F17, classify functions, state precise definitions, and prove relationships between their properties.

Use the proofs in F17 to understand how injectivity and surjectivity behave under composition and how images and inverse images are related. For further study, explore [products of functions](../../notes/math_data_types/functions.md#product-of-functions), [inverse functions](../../notes/math_data_types/functions.md#inverse-functions), and [constructing bijections](../../notes/math_data_types/functions.md#constructing-bijections-between-sets) in the additional notes. F15 also introduces functions defined by cases and calculations with real intervals.

## Notation and conventions

* $\mathbb N=\lbrace 0,1,2,\ldots\rbrace$ includes zero; $\mathbb N^+$ denotes the positive integers. $\mathcal P(A)=2^A$ is the power set, and $\mathcal P_{\mathrm{fin}}(A)$ contains just the finite subsets.
* Unless stated otherwise, functions are total. When a partial function $f:A\rightarrow B$ is explicitly given, $D_f\subseteq A$ is its set of defined inputs. Images and inverse images use only those inputs.
* A partial function may be injective or surjective on its defined values. A bijection **between the full stated sets** is total, injective, and surjective.
* The range $f(A)$ is the set of reached outputs; the codomain $B$ is the stated target set. Distinct inputs may reach the same output.
* $f(S)$ collects outputs from a subset of inputs. $f^{-1}(T)$ collects inputs reaching a subset of targets; it does not assume an inverse function exists.
* Composition runs from right to left: $(f\circ g)(a)=f(g(a))$. The intermediate output must be an allowed input for the next function.
* Every set listing contains each element once. Tuples can repeat entries. Collecting a tuple's entries into a set retains only distinct values before any subsequent aggregation.
* Quantifiers have a dot after each quantified variable, following the [predicate-calculus scope convention](../../notes/predicate_calculus/overview.md#dot-notation-and-quantifier-scope).

## Connections

[Sets](../Sets/README.md) supply the domains, codomains, products, and power sets used here. [Proof techniques](../Proof_Techniques/README.md) supply the direct arguments and counterexamples used to establish function properties. In F16, every computed composition is a sequence of correctly typed inputs and outputs; in F17, the same definitions support statements about arbitrary functions.

The [counting unit](../Combinatorics/README.md) later uses injectivity and surjectivity to compare finite set sizes. [Countability](../Sets/G07.md) uses bijections to study infinite sets.
