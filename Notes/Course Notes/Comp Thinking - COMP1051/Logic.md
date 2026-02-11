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
    - _Note:_ The outside operator ($\lor$) goes inside the new brackets. The inside operator ($\land$) moves to the middle.
- **Distributing AND over OR:**
    $$p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$$
---
### Normal Forms & Completeness
##### Functional Completeness:
- Set of logical operators is **Functionally Complete** if *any* possible propositional formula can be written using *only* the operators in that set
###### Examples of Functionally Complete Sets:
- $\{ \land, \lor, \neg \}$
- Even $\{ \land, \neg \}$ since $A \lor B \equiv \neg(\neg A \land \neg B)$
- $\{ \Rightarrow, \neg \}$
- $\text{NAND: }$False only if both are True
- $\text{NOR: }$True only if both are False
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
# Natural Deduction
###### The Sequent:
$$\phi_1, \phi_2 \vdash \psi$$
- **Left side** $(\phi_1, \phi_2)$: The **Premises** (What you are given/allowed to assume is true)
- **Symbol** $(\vdash)$: Pronounced "turnstile". It means "provably entails"
- **Right side ($\psi$):** The **Conclusion** (What you are trying to reach)
- **English:** "Given that $\phi_1$ and $\phi_2$ are True, prove that $\psi$ is also True"
###### Rules:
1. Lines $1 \text{ to } n$ are the **Premises** (state what we have been given at the start)
2. Every line after that must be justified by a **Rule** applied to previous line(s) 
3. The final line must be the **Conclusion** $(\psi)$
_**Important:**_ *Note that every line evaluates to True*
##### Conjunction $(\land)$ and Double Negation $(\neg\neg)$:
1. **And-Introduction** $(\land i)$
	- **Effect:** If you have two lines $x(A)$ and $y(B)$, you can write $A \land B$
	- **Notation:** $\land i \; x, y$
	- Where $x$ and $y$ are the line numbers and $A$ and $B$ are previously stated propositions
	- **Example:**
		$$\frac{\frac{\phi_1}{\phi_2}}{\phi_1 \land \phi_2}(\land i\; 1, 2)$$
2. **And-Elimination** $(\land e)$
	- **Rule:** If you have $A \land B$, you can extract just $A$ (or just $B$)
	- **Notation:** $\land e \; 1 \; (or \land e \; 2 \text{ for B})$
	- **Example:**
		$$\frac{\phi \land \psi}{\phi} \ (\land e1) \quad \text{or} \quad \frac{\phi \land \psi}{\psi} \ (\land e2)$$
3. **Double Negation $(\neg \neg$ or $\neg e)$**
	- **Rule:** $\neg \neg A$ is the same as $A$, so you can remove the double negative
	- **Notation:** $\neg \neg e \; x$
###### Example:
- Prove $p, \neg \neg(q \land r) \vdash p \land r$
$$\begin{aligned}
\text{1.} \; \; & p && \text{Premise} \\
\text{2.} \; \; & \neg \neg(q \land r) && \text{Premise} \\
\text{3.} \; \; & q \land r && \neg e \;2 \\
\text{4.} \; \; & r && \land e \;2 \; \;3 \; \longleftarrow \text{(Take the } 2^{\text{nd}} \text{ part of the } 3^{\text{rd}} \text{ line)}\\
\text{5.} \; \; & p \land r \; \; \checkmark && \land i \; 1, 4\; \;\longleftarrow \text{(AND the } 1^{\text{st}} \text{ line and the } 4^{\text{th}} \text{ line)}
\end{aligned}$$
---
### Implication & The Boxes
- To prove an "If... then..." statement $(\Rightarrow)$, you have to build a **simulation**
###### 1. Implication Introduction $(\Rightarrow i)$
- To prove $A \Rightarrow B$, you start a sub-proof where you **assume** $A$ to be True, then use that to reach $B$
###### Boxes (Sub-Proof):
1. **Top of Box:** You **Assume** the left side $(A)$ to be True
2. **Bottom of Box:** You end with $B$ (proven from $A$)
3. **Exit:** Close the box and write $A \Rightarrow B$  so you can use it from now on 

_**Important:**_ *Note that you __cannot__ use __any__ statements from the sub-proof outside of the box*
###### Example:
$$\begin{array}{lll} 
\text{1. } \dots & & \text{(some previous work)} \\ 
\begin{array}{|lll|} \hline 
\text{2. } A & & \text{assumption} \\ 
\vdots & & \\ \text{5. } B & & \text{(proven from A)} \\ 
\hline \end{array} \\ 
\text{6. } A \Rightarrow B & & \Rightarrow i \ 2\textminus 5 
\end{array}$$
###### 2. Implication Elimination $(\Rightarrow e)$
*Also known as Modus Ponens*
###### Rule: 
- If you know **"If A then B"** $(A\Rightarrow B)$ is true...
- And you know **"A"** is true...
- Then you can smash them together to get **"B"**
###### Example:
- Prove $A, A\Rightarrow B \vdash B$
$$\begin{aligned}
\text{1.} \;\; & A && \text{Premise}\\
\text{2.} \;\; & A \Rightarrow B&& \text{Premise}\\
\text{3.} \;\; & B && \Rightarrow e \; 1, 2
\end{aligned}$$
---
### Disjunction & Negation
###### 1. Disjunction Introduction $(\lor i)$
- If a statement is True, then you can **OR** any other statement to it, and the whole thing remains True
###### Example:
$$\frac{\phi}{\phi \land \psi} \ (\lor i_1) \quad \text{or} \quad \frac{\psi}{\phi \land \psi} \ (\lor i_2)$$
- **Syntax:** Use $\lor i_1$ (if adding to the right) or  $\lor i_2$ (if adding to the left) + line number
###### 2. Disjunction Elimination $(\lor e)$
- If you know $A \lor B$ is True, but you don't know *which* one is True. So, to prove a conclusion $C$, you must prove it works in **both scenarios**
**The Structure (Two Boxes):**
1. **Box 1:** Assume $A$ is true $\rightarrow$ Prove $C$
2. **Box 2:** Assume $B$ is true $\rightarrow$ Prove $C$
3. **Conclusion:** Since you get $C$ in _either_ case, $C$ is definitely True
###### Structure: (Proof by Cases)
$$\begin{array}{lll} 
\text{1. } A \lor B & && \text{Premise} \\ 
\begin{array}{|lll|} \hline 
\text{2. } A & && \text{Assumption} \quad \leftarrow \text{(Case 1)} \\ 
\vdots & && \\ 
\text{4. } C & && \text{(Result)} \\ 
\hline \end{array} & && \\ 
\begin{array}{|lll|} \hline 
\text{5. } B & && \text{Assumption} \quad \leftarrow \text{(Case 2)} \\ 
\vdots & && \\ 
\text{7. } C & && \text{(Result MUST be same)} \\ 
\hline \end{array} & && \\ 
\text{8. } C & && \lor e \ 1, 2 \textminus 4, 5 \textminus 7 
\end{array}$$
- **Syntax:** Use $\lor e$ + Line of OR + Range of Box 1 + Range of Box 2
##### Example: $(p \lor q \vdash q \lor p)$
- Proof that $\lor$ is Commutative
- **Plan:**
	1. **Start:** You have $p \lor q$. You need to use **$\lor e$** (Proof by Cases)
	2. **Case 1 (Box 1):** Assume $p$. Use **$\lor i$** to turn it into $q \lor p$
	3. **Case 2 (Box 2):** Assume $q$. Use **$\lor i$** to turn it into $q \lor p$
	4. **Finish:** Cite the rule `ve` to conclude $q \lor p$
**Sequent:** $p \lor q \vdash q \lor p$
$$\begin{array}{lll}
\text{1. } p \lor q & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{2. } p & && \text{Assume} \\
\text{3. } p \lor q & && \lor i_1 \; 2 \\
\hline \end{array} \\
\begin{array}{|lll|} \hline
\text{4. } q & && \text{Assume} \\
\text{5. } p \lor q & && \lor i_1 \; 4 \\
\hline \end{array} \\
\text{6. } q \lor p & && \lor e \; 1, 2 \textminus 3, 4 \textminus 5\\
\end{array}$$
