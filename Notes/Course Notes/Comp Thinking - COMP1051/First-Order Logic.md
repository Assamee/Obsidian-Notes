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
## Logical Equivalence
- Things you can do with two logically equivalent formula $(\phi \equiv\ \psi)$
##### Substitution:
- If a sub-formula is logically equivalent to another formula, you can swap them out without changing the overall semantics of the larger sentence
##### Renaming Variables:
- You can change the name of a quantified variable (e.g. replacing $x$ with $y$) without changing the semantics. For example, $\forall x\phi(x)\equiv\forall y\phi(y)$ 
- This applies to both universal ($\forall$) and existential ($\exists$) quantifiers
- Obviously don't rename to a variable that is already used in the formula
---
#### Quantifier Negation:
Negations can be "pushed through" quantifiers by flipping the quantifier to its opposite
###### Universal to Existential $(\forall \rightarrow \exists)$:
- Pushing a negation through a "For All" turns it into an "Exists" $\left( \text{e.g. } \neg\forall x\phi\equiv\exists x\neg\phi \right)$
###### Existential to Universal $(\exists \rightarrow \forall)$:
- Pushing a negation through an "Exists" turns it into a "For All". $\left(  \text{e.g. } \neg\exists x\phi\equiv\forall x\neg\phi \right)$
---
#### Manipulating Quantifiers:
Quantifiers can be extracted from inside logical connectives ($\wedge$ or $\vee$) to the very front of the formula
##### Extraction Example:
$$\forall x\phi\wedge\exists y\psi\equiv\forall x\exists y(\phi\wedge\psi)$$
##### Variable Clashes:
- You can only pull out quantifiers if the quantified variables don't clash with each other. If you have two separate sub-formulae that both use $x$, you _must_ rename one of them (e.g. to $z$)
- Have to ensure that they have "nothing to do with each other" before pulling the quantifiers to the front
##### Order Matters:
- Swapping the order of quantifiers changes the meaning of a formula
- **Example:** 
$$\forall x\exists yE(x,y) \not\equiv \exists x\forall yE(x,y)$$
##### Implication example of swapping the order:
- If there _exists_ an $x$ for all $y$, then for all $y$ there _exists_ an $x$ 
$$\left( \exists x \forall y \, E(x, y) \right) \rightarrow \left( \forall y \exists x \, E(x, y) \right)$$
- If one $x$ works for everyone, then for anyone you can find that specific $x$ to satisfy the relation
---
#### An Example of why Order Matters:
- Suppose we have a simple directed graph, with a domain of four vertices: $\{1, 2, 3, 4\}$. Where the set of edges are $E = \{(1,2), (2,3), (3,4), (4,1)\}$
###### Diagram:
``` Plaintext
(1) ---> (2)
 ^        |
 |        v
(4) <--- (3)
```
###### For All $x$, there Exists a $y$:
- **$\forall x\exists y \; E(x,y)$ is True:** Every single vertex ($x$) has at least one outgoing arrow to another vertex ($y$)
###### There Exists an $x$ For Each $y$:
- **$\exists x\forall yE(x,y)$ is False:** There is no single "super-vertex" ($x$) that has an outgoing arrow pointing to every other vertex in the entire graph
---
## Prenex Normal Form
- A first-order formula is in prenex normal form (PNF) if all of its quantifiers are clustered at the front, and the rest of the formula contains no quantifiers
##### Structure:
$$Q_{1}x_{1}Q_{2}x_{2}...Q_{k}x_{k}\phi$$
- **Notation:** Each $Q$ is a quantifier ($\forall$ or $\exists$), each $x$ is a variable, and $\phi$ is a strictly quantifier-free formula (often called the matrix)
- **Usage:** 
---
### Parse Trees (Converting to PNF)
- To convert a complex formula into PNF, we use its parse tree to systematically push quantifiers outwards
##### 1. Start at the Leaves:
- Begin at the bottom of the parse tree with the smallest atomic sub-formulae
- Since they contain no quantifiers, they are trivially already in PNF
##### 2. Work Upwards (AND / ORs):
When you move up to an $\land \text{ or } \lor$ node, you combine its two child sub-trees
- First, rename any bound variables so that the two sub-trees share absolutely no variables names
- Then, pull all quantifiers from both sub-trees to the very front
##### 3. Work Upwards (NOT):
- When you move up to a $\neg$ node, you must apply the quantifier negation rules
- Push the negation _through_ the prefix of quantifiers, flipping each quantifier until the negation rests directly next to the quantifier-free matrix
##### 4. Work Upwards (Quantifiers):
- When you move up to a $\forall$ or $\exists$ node, add the quantifier to the front of the growing formula
---
### Example of Converting to PNF (Parse Trees)
- **Question:** Convert this formula into PNF $$\neg \forall (P(x) \land \exists y \, Q(x, y))$$
##### Parse Tree:
``` Plaintext
        (¬)
         |
       (∀x)
         |
        (∧)
       /   \
    P(x)  (∃y)
            |
         Q(x,y)
```
##### Step 1: Evaluate the Leaves
- The atomic formulae $P(x)$ and $Q(x, y)$ have no quantifiers, so they are trivially in prenex normal form
##### Step 2: Evaluate the $\exists y$ Sub-tree
- We move up to the $\exists y$ node, and add it to the front of $Q(x, y)$
$$\textbf{Resolves to: } \exists y \, Q(x,y)$$
##### Step 3: Evaluate the $\land$ Sub-tree
- We move up to the $\land$ node, and combine its left and right children, pulling any quantifiers to the front. Because $y$ doesn't appear in $P(x)$, we don't need to rename any variables
$$\textbf{Resolves to: } \exists y(P(x)\wedge Q(x,y))$$
##### Step 4: Evaluate the $\exists x$ Sub-tree
- We move up to the $\forall x$ node, and add it to the front of the formula
$$\textbf{Resolves to: } \forall x\exists y(P(x)\wedge Q(x,y))$$
##### Step 5: Evaluate the $\neg$ Sub-tree (The root node)
- We move up to the $\neg$ node, and push the negation _through_ the prefix, flipping any quantifiers we pass through
- The $\forall x$ flips to $\exists x$, and the $\exists y$ flips to $\forall y$
$$\textbf{Resolves to: } \exists x\forall y \; \neg(P(x)\wedge Q(x,y))$$
---
$\underline{\textbf{Related Pages: }}$
- [[Logic]]
- [[Natural Deduction]]
- [[Resolution]]
- [[Sat-Solvers]]
- [[First-Order Logic]]