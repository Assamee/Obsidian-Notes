### Intro to Logic:
- Logic provides a formal language to avoid the ambiguity of natural languages (e.g. English)
###### 3 Components of Logic:
- **Syntax:** The grammatical rules of a language (so we know if a statement is 'valid')
- **Semantics:** The meaning of the syntax (to determine the truth or falsity of a statement)
- **Proof System:** A rigorous method for manipulating formulae to construct proofs
###### Desirable properties of a logical system:
- **Completeness:** Every statement that is true (according to semantics) can be proven (using the proof system)
- **Soundness:** The proof system only derives true conclusions from statements that are both valid and true
##### Propositions:
- A declarative 'statement of fact' that can either be true or false, but not both (Questions, Commands and gibberish are _not_ propositions)
- We can use **propositional variables** to represent propositions, and they can take the **truth values** $T$ (True) or $F$ (False)
---
### Truth Tables & Semantics:

| **p** | **q** | $p \: \neg \: q \text{ (Not)}$ | $p \land q \text{ (And)}$ | $p \lor q \text{ (Or)}$ | $p \implies q \text{ (Implies)}$ | $p \iff q \text{ (Iff)}$ |
| ----- | ----- | ------------------------------ | ------------------------- | ----------------------- | -------------------------------- | ------------------------ |
| **T** | **T** | F                              | **T**                     | **T**                   | **T**                            | **T**                    |
| **T** | **F** | F                              | F                         | **T**                   | **F**                            | F                        |
| **F** | **T** | **T**                          | F                         | **T**                   | **T**                            | F                        |
| **F** | **F** | **T**                          | F                         | F                       | **T**                            | **T**                    |
###### Syntax:
- $\Rightarrow \text{ (Implies):}$ $p \Rightarrow q$  if only False when $p$ **is True and** $q$ **is False** (broken promise)
- **$\Leftrightarrow$ (Iff):** True only when $p$ and $q$ are the **same**
- **$\phi \textbf{ (phi)}, \psi \textbf{ (psi)}$:** Represent **any** complex formula (e.g. $\phi$ could be $(p \land q) \Rightarrow r$)
- letters (like $p, q, r$) are used to represent **atomic** statements
###### Tautology:
- A statement $(\phi)$ that is True for **every** truth assignment (True for every possible input)
###### Contradiction:
-  A statement $(\phi)$ that is False for **every** truth assignment (False for every possible input)
