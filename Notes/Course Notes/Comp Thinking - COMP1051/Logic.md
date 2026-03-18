### Intro to Logic
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
### Truth Tables & Semantics

| **p** | **q** | $\neg p\text{ (Not)}$ | $p \land q \text{ (And)}$ | $p \lor q \text{ (Or)}$ | $p \implies q \text{ (Implies)}$ | $p \iff q \text{ (Iff)}$ |
| ----- | ----- | --------------------- | ------------------------- | ----------------------- | -------------------------------- | ------------------------ |
| **T** | **T** | F                     | **T**                     | **T**                   | **T**                            | **T**                    |
| **T** | **F** | F                     | F                         | **T**                   | **F**                            | F                        |
| **F** | **T** | **T**                 | F                         | **T**                   | **T**                            | F                        |
| **F** | **F** | **T**                 | F                         | F                       | **T**                            | **T**                    |
###### Syntax:
- $\Rightarrow \text{ (Implies):}$ $p \Rightarrow q$  if only False when $p$ **is True and** $q$ **is False** (broken promise)
- **$\Leftrightarrow$ (Iff):** True only when $p$ and $q$ are the **same**
- **$\phi \textbf{ (phi)}, \psi \textbf{ (psi)}$:** Represent **any** complex formula (e.g. $\phi$ could be $(p \land q) \Rightarrow r$)
- letters (like $p, q, r$) are used to represent **atomic** statements
###### Tautology:
- A statement $(\phi)$ that is True for **every** truth assignment (True for every possible input)
###### Contradiction:
-  A statement $(\phi)$ that is False for **every** truth assignment (False for every possible input)
###### Satisfiable:
-  A statement $(\phi)$ that can be satisfied (There exists an input that results in $\phi$ being True)
---
### Logical Equivalence & Algebra
####  Implication Law:
- This is used to convert an implication $(\Rightarrow)$ into standard Or/Not Logic
$$p \Rightarrow q \equiv \neg p \lor q$$
###### English Example:
- Think about the promise "If it rains, I will bring an umbrella." The only time I break my promise is if "It rains" ($p=T$) **AND** "No umbrella" ($q=F$). So, as long as "It doesn't rain" ($\neg p$) **OR** "I have the umbrella" ($q$), I am safe.
##### De Morgan's Laws:
- **Negating AND:** $\neg(p \land q) \equiv \neg p \lor \neg q$.
    - _Translation:_ "Not (A and B)" is the same as "(Not A) or (Not B)"
- **Negating OR:** $\neg(p \lor q) \equiv \neg p \land \neg q$.
    - _Translation:_ "Not (A or B)" is the same as "(Not A) and (Not B)"
##### Distribution Laws:
- **Distributing OR over AND:**
    $$p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$$
    - _Note:_ The outside operator ($\lor$) goes inside the new brackets. The inside operator $(\land)$ moves to the middle.
- **Distributing AND over OR:**
    $$p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$$
---
### Functional Completeness & Parity
##### Functional Completeness:
- Set of logical operators is **Functionally Complete** if *any* possible propositional formula can be written using *only* the operators in that set
###### Examples of Functionally Complete Sets:
- $\{ \land, \lor, \neg \}$
- Even $\{ \land, \neg \}$ since $A \lor B \equiv \neg(\neg A \land \neg B)$
- $\{ \neg, \lor \}$
- $\{ \Rightarrow, \neg \}$
- $\text{NAND: }$False only if both are True
- $\text{NOR: }$True only if both are False
---
### Parity
##### Parity of a logical operator:
- If the output column of a truth table has two 'T's, it has "even parity". If it has one 'T' (like an AND gate), it has "odd parity"
###### The Effect of Parity:
- **Even Parity:** If every logical operator in a set is of **even** parity, then any combination of operators in that set will **_always_** produce a truth table that has an even number of 'True' rows ($0$, $2$, or $4$ for a two-variable table)
	- They preserve **Even Parity**
-  **Odd Parity:** A set containing operators with an **odd** parity can produce _both_ odd and even results in a truth table
$$\begin{array}{|r|} \hline
EVEN + EVEN = EVEN \\
ODD + ODD = EVEN  \\
\hline \end{array}
$$
---
### Normal Forms
#### Disjunctive Normal Form: (DNF)
###### Definition:
- A formula is in **DNF** if it is a **Disjunction of Conjunctions** (an OR of ANDs)
- **Structure:** $(A \land B) \lor (\neg A \land C) \lor \dots$
- Think of it as: "A list of ways to win" (A collection of different ways to make the formula True)
###### How to build it (Truth Table Method):
1. Look at the Truth Table
2. Identify every row where the result is **True**
3. Write a conjunction for that row $\left( \text{e.g. if } p=T, q=F \text{, write } (p \land \neg q) \right)$
4. Join each row with $\lor$
#### Conjunctive Normal Form: (CNF)
###### Definition:
- A formula is in **CNF** if it is a **Conjunction of Disjunctions** (an AND of ORs)
- **Structure:** $(A \lor B) \land (\neg A \lor C) \land \dots$
- Think of it as: "A list of requirements, all of which must be met"
###### How to build it (Truth Table Method):
1. Identify the **False** rows
2. Negate the variables in the "False" row
3. Join then with **ORs** $(\lor)$ to make a clause
	- _Example:_ If the false row is $p=T, q=F, r=T$, write $(\neg p \lor q \lor \neg r)$
4. Then join the clauses (False rows) with **ANDs** $(\land)$
###### How to build it (Syntactic Method):
1. Eliminate the arrows $(\Rightarrow, \Leftrightarrow)$
2. Push any negations inside brackets (De Morgan's)
3. **Distribute** $\lor$ over $\land$ until you have the correct shape $(p \lor (q \land r) \equiv (p \lor q) \land (p \lor r))$
---
### 1. Proof of Functional Completeness $(\land, \lor, \neg)$
##### Prove that the set $\{ \land, \lor, \neg \}$ is a Functionally Complete Set:
###### Functionally Complete Set:
- A set of logical connectives is functionally complete if and only if every possible truth function $f(p_1, p_2, \dots, p_n)$ can be expressed as a well-formed formula using only the connectives from that set 
- **Simple Definition:** Can build a formula for _any_ possible truth table using only logical connectors from the set
### Proof:
- **Plan:** Prove that we can convert **any arbitrary truth table** into a Disjunctive Normal Form (DNF) formula. Note that DNF formulae only use NOT $(\neg)$, AND $(\land)$, and OR $(\lor)$

1. Every possible truth function (or truth table) can be mapped and expressed in Disjunctive Normal Form (DNF). 
2. DNF is constructed by taking a disjunction ($\vee$) of conjunctions ($\wedge$) of literals, where each literal is either a variable or its negation ($\neg$). 
3. Because any arbitrary truth table can be perfectly translated into DNF using only these three connectives, the set $\{\neg, \vee, \wedge\}$ is functionally complete.
---
### 2. Proof: Is $\{ \neg, \rightarrow\}$ a Complete Set?
Answer: **YES**
- Because we can build the complete set $\{ \neg, \lor\}$
##### Proof:
1. **Recall Implication Law:** $A \rightarrow B \equiv \neg A \vee B$
2. **Let $A$ be its negated form $(\neg A)$:** $$\therefore \neg A \rightarrow B \equiv \neg (\neg A) \lor B \equiv A \lor B$$
3. We now have created the OR operator $(A \lor B)$, using only the formula $\neg A \rightarrow B$. Because we have $\neg$ in the given set, and can create $\lor$, we have now have the complete set $\{ \neg, \lor \}$
4. Therefore, $\{ \neg, \rightarrow \}$ is functionally complete
---
### 3. Proof: Is $\{ \neg, \leftrightarrow \}$ a Complete Set?
Answer: **NO**
- To Prove that a set **isn't** functionally complete we check the parity of its operators (counting the number of True outputs). To show that we can't build one of the fundamental operators, like AND $(\land)$.
###### Truth Tables:

| **p** | **q** | $\neg p\text{ (Not)}$ | $p \iff q \text{ (Iff)}$ |
| :---- | :---- | --------------------- | ------------------------ |
| **T** | **T** | F                     | **T**                    |
| **T** | **F** | F                     | F                        |
| **F** | **T** | **T**                 | F                        |
| **F** | **F** | **T**                 | **T**                    |
- Both $\neg$ and $\leftrightarrow$ have **Even** parity
	$\therefore$ Any formula built with only $\neg$ and $\leftrightarrow$ will always result in a truth table that has an **even** number of True rows ($0$, $2$, or $4$)

**AND:**
- Therefore we cannot build the AND operator, as it has an ODD parity ($1$ True value)
- Because $1$ is an odd number, it is mathematically impossible to generate the truth table for $p \land q$ using operations that strictly preserve an even parity of True rows
- Since we cannot build an AND gate, the set $\{ \neg, \leftrightarrow\}$ is incomplete
---
### 4. Proof: Is $\{ NOR \}$ a Complete Set?
Answer: **YES**
- To prove this we will prove that the single operator can produce a known complete set, like $\{ \neg, \lor \}$
###### Proof:
1. **Simulating NOT $(\neg)$:** $\text{A NOR A} \equiv \neg(A \lor A) \equiv \neg A$
2. **Simulating OR $(\lor)$:** $$\begin{array}{rl}
   \text{(A NOR B) NOR (A NOR B)} \equiv &\\ 
\neg(\neg(A \lor B) \lor \neg(A \lor B)) \equiv & \\
(A \lor B) \land (A \lor B) \equiv & \\
A \lor B \equiv
\end{array}$$
3. **Conclusion:** Because we have built both a NOT gate and an OR gate using only NORs, we have simulated the complete set $\{ \neg, \lor \}$
	$\therefore \{ NOR \}$ is a functionally complete set
---
$\underline{\textbf{Related Pages: }}$
- [[Natural Deduction]]
- [[Resolution]]
- [[Sat-Solvers]]
- [[First-Order Logic]]
- [[Logic Practical Week 15]]
- [[Logic Practical Week 14]]
- [[Logic Practical Week 14 (Prep)]]
- [[Logic Practical Week 13]]