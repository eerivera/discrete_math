# Propositional Calculus Parse Trees

## Skill Addressed

* [F01 — Syntax and Semantics](../../skills/Propositional_Calculus/F01.md)

For large sentences in the propositional calculus, also known as boolean formulas, it can sometimes be easier to
represent the formula in a graphical form as a "tree".  This is particularly useful if you want to evaluate a formula
on a particular assignment of truth values to the variables of the formula.

## Example

Below is an example of a parse tree for the formula
$((P \rightarrow R) \wedge (Q\rightarrow R)) \leftrightarrow ((P\vee Q) \rightarrow R)$.

![Parse tree for the formula](../../skills/Propositional_Calculus/images/F01/parse-tree.svg)

Observe that you don't need paretheses in a parse tree as it is completely clear which subexpressions correspond to which operators.

## Evaluating a formula with a parse tree

Below is an example showing how to use a parse tree to find the value of a boolean expression
for a particular assignment of truth values to the variables.

The first step is to write down the truth values for each proposition.

Next you write down the truth values for each subexpression as you work your way toward the root of the tree.

The value at the root of the tree is the value of the expression for that assigment of truth values.

![Evaluation using a parse tree](../../skills/Propositional_Calculus/images/F01/parse-tree-evaluation.svg)

Parse Trees for Expressions are an important concept in Computer Science, and we'll return to them
we look at Graph Theory toward the end of this class.
