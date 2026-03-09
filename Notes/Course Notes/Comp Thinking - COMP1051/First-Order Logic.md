#### Predicate (or Relation Symbol):
- A relationship that applies to $r$ elements 
- **Example:** A predicate symbol $P$ of arity $r$ is $P(x_1, x_2, ..., x_r)$
##### Arity:
- The number of variables that a predicate symbol takes
- **Unary (Arity 1):** A property containing a single object $(\text{e.g. } Q(x))$
-  **Binary (Arity 2):** A relationship containing two variables, like an edge $(E(x, y))$
- **Ternary (Arity 3):** A relationship containing 3 variables. 
	- For example, a predicate symbol $T$ of arity 3 might form the atomic formula $T(x,y,z)$
---
#### Atomic Formulae:
- Variables within an atomic formula don't have to be distinct (e.g. a ternary relation $T$ could form the atomic formula $T(x, y, z))$
- **Equality:** Equality statements like $x = y$ are valid atomic formulae
- **Truth Evaluation:** On its own, an atomic formula like $E(x,y)$ is neither true nor false. 
	- You need a domain (graph) and specific values for $x$ and $y$
---
### Free & Bound Variables
- **Quantifier-free Formulae:** Formulae that can be built by using only logical connectives on atomic formulae
#### Free Variable Occurrence
- An occurrence of a variable in a Quantifier-free formula (A formula that isn't bound by $\forall \text{ or } \exists$)
- Free variables must be explicitly given a value to be able to determine if a formula is True
#### Bound Variable Occurrence
- An occurrence of a variable $x$ that is used in a quantifier $\forall{x} \text{ or } \exists{x}$

_**Note:** We use "Occurrences" because the same variable could be bound in one formula, and free in a separate part of the same formula_
#### Sentence:
- A formula that has no free variables. Therefore a sentence can be evaluated as entirely true or false on a given graph
#### Example: (Free & Bound Occurrences)
- For the formula: $$\forall x(\forall y(P(x,y)\Leftrightarrow\neg Q(x,y))) \wedge \exists z(P(z,x)\wedge\neg Q(x,C))$$
- The variable $x$ is bound in the first half of the formula, and free in the second half
---
#### Nesting & Order of Quantifiers
- Note that swapping the order of a $\forall$ and $\exists$ in a sentence, changes the meaning of the sentence
**Example:**
Let the relation $P(x, y)$ be interpreted as "$x \gt y$" over the domain of integers $(\mathbb{Z})$
- $\forall{x}\exists{y} \; P(x, y):$ For _every_ integer $x$, _there exists_ an integer $y$ such that $x > y$. This is **True** as for any integer $x$, if we take $y = x - 1$, it satisfies the formula
- $\exists{y}\forall{x} \; P(x, y):$ For _there exists_ an integer $y$ such that _for all_ integers $x$, $x > y$. This is **False** as no matter which integer $y$ we choose, the integer $x,$ where $x = y - 1$ results in $x \le y$
---
## Truth Evaluations (Semantics)
#### Interpretations & Models:
An **Interpretation** (or structure) gives meaning to the logical formulae. For a first-order formula $\phi,$ an interpretation consists of: 
###### • Domain of Discourse $(D)$:
- The set of all possible objects involved in the formula (like the edges on a graph)
###### • Relations:
- A mathematical relation over the domain $D$ for every relation symbol involved in the formula $\phi$. (E.g. the edge relation $E(x, y)$ for directly connected vertices)
###### • Constants & Free Variables:
- A specific assigned value from the domain $D$ for every constant symbol and free variable involved in the formula $\phi$
##### • Models:
- If an interpretation of a formula evaluates to true, then that specific interpretation is a **model** of the formula. Models are denoted with the $\models$ symbol, for example: $(\mathbb{N}, P, Q, 0) \models \phi$
---
### Steps to Evaluate a Sentence
###### 1. Interpret Atoms:
- Treat the smallest atomic formulae as simple true or false propositions. (E.g. Check if an edge actually exists for a given edge relation)
###### 2. Process Connectives: 
- Evaluate the logical connectives $(\land, \lor, \neg)$ like standard propositional logic
###### 3. Evaluate Existential Quantifies $(\exists)$:
- For a statement like $\exists{x} \; \phi,$ search for _at least **one_** value $x$ in the domain that makes $\phi$ true (E.g. True for at least one vertex in the graph)
###### 4. Evaluate Universal Quantifiers $(\forall)$:
- For a statement like $\forall{x} \; \phi,$ verify that the condition holds true for _all_ possible values of $x$ (E.g. every vertex in a graph)
---
