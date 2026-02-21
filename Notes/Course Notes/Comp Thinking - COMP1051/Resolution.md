# Resolution
#### Resolution Rule:
$$\frac{p \vee q \quad \neg p \vee r}{q \vee r}$$
###### Concept:
- If you have a long clause containing $x$, and another long clause containing $\neg x$, you can remove the $x \text{ and } \neg x$, and join all the remaining literals with ORs $(\lor)$
#### Clause:
- A clause $(C_i)$ is a disjunction of literals (a sequence of literals joined by ORs, $\lor$) of literals
For conjunctive normal form $\left( C_1 \wedge C_2 \wedge \dots \wedge C_m \right)$ each $C$ is a collection of literals joined with ORs $\lor$.
---
#### Soundness & Completeness
Resolution is both sound and complete
- **Soundness:** If Resolution announces that $\phi$ is a theorem, then $\phi$ is a tautology
- **Completeness:** If $\phi$ is a tautology, then Resolution announces that $\phi$ is a theorem

_**Note:**_ In the worst case, Resolution involves an exponential number of applications
#### Satisfiability & Tautologies
- **Sat-Solvers:** Checks if a given formula of propositional logic is satisfiable
- **Proof Systems:** Systems like Resolution aim to prove theorems
- **Link:** A formula $\phi$ is satisfiable if, and only if, its negation $\neg \phi$ is not a tautology
	- If $\phi$ is satisfiable, there exists a truth assignment making $\phi$ true
	- This means there exists a truth assignment making $\neg \phi$ false,  meaning that $\neg \phi$ is not a tautology
---
#### The Resolution Algorithm
- Natural Deduction tries to prove theorems from scratch, but Resolution takes a different approach by taking a given formula and working with it to decide if it is a theorem
##### Method:
1. Start with a given formula $\phi$
2. Negate it (because Resolution works be showing the negation is unsatisfiable)
3. Convert the negated formula to C.N.F $\left( C_1 \wedge C_2 \wedge \dots \wedge C_m \right)$
4. Extract the individual Clauses $C_1, C_2, \dots, C_m$
5. Repeatedly resolve each clause
##### Halting Conditions:
- **Proving a Theorem:** If we ever infer the empty clause $\emptyset$, then we halt and output that $\phi$ is a theorem
- **Disproving a Theorem:** If we get to the point where we have not inferred the empty clause and we cannot infer any new clauses, then we halt and output that $\phi$ is not a theorem
##### Extra Rule:
- **Deleting Literals:** When resolving, we are also allowed to delete repeated literals in any clause
---
### Example:
- **Question:** Let $\phi$ be the formula $\neg((p \vee q) \wedge (\neg p \vee q) \wedge (p \vee \neg q) \wedge (\neg p \vee \neg q))$. Is $\phi$ a theorem?
$$\begin{array}{lll} \begin{array}{|lll|} \hline
\text{Negate the Formula: }
(p \vee q) \wedge (\neg p \vee q) \wedge (p \vee \neg q) \wedge (\neg p \vee \neg q) \\
\text{- The Formula is already in Conjunctive Normal Form}  \\
\text{List the Clauses: } \\
\quad \text{Clause 1: } p \lor q \\
\quad \text{Clause 2: } \neg p \lor q \\
\quad \text{Clause 3: } p \lor \neg q \\ 
\quad \text{Clause 4: } \neg p \lor \neg q \\
\text{Resolution Rule: Combine the clauses with clashing literals } \\
\text{Clause 1 and 2:  (The $p$ and $\neg p$ clash)} \\
\quad \quad (p \lor q) \quad (\neg p \lor q) \longrightarrow q \lor q \longrightarrow q \\
\text{Clause 3 and 4:  (The $p$ and $\neg p$ clash)} \\
\quad \quad  (p \lor \neg q) \quad (\neg p \lor \neg q) \longrightarrow \neg q \lor \neg q \longrightarrow \neg q \\
\text{Now the Clauses $p$ and $\neg p$ clash, leaving nothing left $(\emptyset)$} \\ \hline \end{array} \\
\text{Since we have inferred the Empty Clause, it means $\neg \phi$ is a contradition} \\
\text{$\therefore$ $\phi$ is a Theorem}
\end{array}$$
###### Diagram: 
``` Plaintext
(p ∨ q)      (¬p ∨ q)         (p ∨ ¬q)     (¬p ∨ ¬q)
     \           /                  \           /
      \         /                    \         /
       \       /                      \       /
        ---(q)---                      -(¬q)--
            \                            /
             \                          /
              \                        /
               \                      /
                ---- Empty Clause ----
                         (∅)
```

---
### Shortcut when converting to c.n.f. $(\neg(A \Rightarrow B) \equiv A \land \neg B)$
- Used when Implications are involved $(\Rightarrow)$
$$\begin{array}{lll} 
\text{The negation of } A \Rightarrow B \text{ is equivalent to } A \land \neg B \\ \\
\text{Proof: } \\
\text{Start with the Negation: }& \\
\neg(A \Rightarrow B) & \text{Implication Law} \\
\neg(\neg A \lor B) & \text{De Morgan's} \\
(A \land \neg B) \\
\end{array}$$
Truth Table:
``` Plaintext
 A | B || A ⇒ B | ¬(A ⇒ B) || ¬B | A ∧ ¬B
---|---||-------|----------||----|--------
 T | T ||   T   |    F     || F  |   F
 T | F ||   F   |    T     || T  |   T
 F | T ||   T   |    F     || F  |   F
 F | F ||   T   |    F     || T  |   F
```

$\underline{\textbf{Related Pages: }}$
- [[Logic]]
- [[Sat-Solvers]]
- [[Logic Practical Week 15]]