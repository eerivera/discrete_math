# Overview of Propositional Calculus

## Skills Addressed

* [F01 — Syntax and Semantics](../../skills/Propositional_Calculus/F01.md)
* [F02 — Truth Tables and Satisfiability](../../skills/Propositional_Calculus/F02.md)

The Propositional Calculus is a formal language for expressing logical concepts.

The primitives are propositions (typically named P, Q, R, ...) which are assumed to be either True or False.
These are connected to form sentences using the logical connectors: and, or, not, and others. 

## Propositional Sentences
Sentences in the Propositional calculus are formed by primitives called propositions (typically named P, Q, R, ...)
joined together with logical operators (and, or, not, and others) to form sentences, which likewise are either True or False
(depending on the values of the primitive propositions).

The operators are usually written with special symbols (where P and Q are propositional sentences)


| Math | Text | Meaning |
| --- | ----  | --- |
| $\neg P$ |  not(P) |  This is the negation of P and is True precisely when P is False.|
| $P \wedge Q$ |  P AND Q | This is the conjunction of P and Q and is True precisely when both P and Q are True.|
| $P \vee Q$ | P OR Q |This is the disjunction of P and Q and is True if P or Q or both are True.|
| $P \rightarrow Q$  | P IMPLIES Q <br>  P ONLYIF Q | This is the implication, if P then Q, and it is True when P is False or Q is True.|
| $P \leftarrow Q$  | P IF Q | This is the implication, Q implies P, if Q then P, and it is True when Q is False or P is True.|
| $P \leftrightarrow Q$ | P IFF Q | This is True when P and Q have the same truth value, i.e. P is True IF AND ONLY IF Q is True.|
| $P \oplus Q$ |  P XOR Q | This is True if exactly one of P and Q is True; it is called the exclusive OR.|


This language is also called Boolean Algebra and the sentences are formulas in Boolean algebra. 
Many of the familiar properties of high school algebra also hold true in Boolean Algebra.

Each sentence has a truth value (True or False) which can be obtained from the truth values of the propositions using a truth table.

 
## Definitions of some terms related to Propositional Calculus
An assignment of truth values $\{T,F\}$ to a set of variables is called an __interpretation__, e.g.

$P\mapsto F$<br>
$Q\mapsto T$<br>
$R\mapsto F$<br>

A formula which is True for all interpretations is called a __tautology__.

The formula  $P \vee \neg P$ is a tautology.

A more complex tautology is $((P \rightarrow R) \wedge (Q\rightarrow R)) \leftrightarrow ((P\vee Q) \rightarrow R)$.

A formula is __satisfiable__ if there is at least one interpretation which makes it True.

If $\neg E$ is not satisfiable, then E is a tautology.

The formula  $\neg (P \wedge Q)$ is satisfiable, but is not a tautology.

The formula $P \wedge \neg P$ is not satisfiable.

How long does it take to test if a formula with N variables is a tautology using a truth table?



# Readings
Here are some chapters in free online textbooks covering these concepts
* DM-AOI Ch 0.2 http://discrete.openmathbooks.org/dmoi3/sec_intro-statements.html
* DM-AOI Ch 3.1 http://discrete.openmathbooks.org/dmoi3/sec_propositional.html
* MfCS Ch3-1-3.5 in  https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-042j-mathematics-for-computer-science-spring-2015/readings/MIT6_042JS15_textbook.pdf
