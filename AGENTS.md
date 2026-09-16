# Repository conventions

For all future skills and course-note edits, use dot notation for universal and existential quantifiers: `\forall x . F` and `\exists x . F`. Put a dot after each quantified variable in a chain, for example `\forall x . \exists y . Q(x,y)`. Standalone quantifier symbols or parse-tree node labels such as `\forall x` do not need a dot.

A quantifier's scope extends from the dot to the end of the formula unless a closing parenthesis enclosing the quantifier ends it sooner. Parentheses around a subexpression after the dot do not end that scope. Preserve intended bindings when editing: `\forall x . P(x)\rightarrow Q(x)` governs the whole implication, while `(\forall x . P(x))\rightarrow Q(x)` leaves the final `x` free. In equivalence rules, delimit quantified operands so scope does not spill into the other side. In aligned derivations, each step is a separate formula.

Keep explanations, exercises, answers, and formula labels in diagrams consistent with this convention. The student-facing explanation is in `notes/predicate_calculus/overview.md`, under “Dot notation and quantifier scope.”

Keep Markdown display-math delimiters (`$$`) on their own unindented lines, with blank lines around the block, including formulas between numbered exercises.
