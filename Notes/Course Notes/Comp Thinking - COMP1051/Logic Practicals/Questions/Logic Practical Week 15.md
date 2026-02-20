# Question 1: Resolve to determine if a set of clauses have a satisfying Truth assignment
---
1. $p \lor q \quad \neg p \lor r \quad \neg p \lor \neg r \quad p \lor \neg q$
$$\begin{array}{lll}
\text{Clause 2 and 3: (Resolve on $r$)} \\
\neg p \lor r \quad \neg p \lor \neg r \longrightarrow \neg p \lor \neg p \longrightarrow \neg p \\
\text{Clause 1 and 4: (resolve on $p$)} \\
p \lor q \quad p \lor \neg q \longrightarrow p \lor p \longrightarrow p \\
\text{Both inferred Clauses: (Resolve on $p$)} \\
p \; \text{ and } \;  \neg p \longrightarrow \emptyset \\
\therefore \text{The set is a Contradiction} \\
\therefore \text{The set is unsatisfiable} \\ 
\quad \text{and does not have a satisfying truth assignment}
\end{array}$$
We chose the clauses 2 and 3 because they both had a common literal that would be left after the resolution
2. $p \lor q \lor \neg r \lor s \quad \neg p \lor r \lor s \quad \neg q \lor \neg r \quad p \lor \neg s \quad \neg p \lor \neg r \quad r$
$$\begin{array}{lll}
\text{Clauses 5 and 6: (Revolve on $r$)} \\
p \lor \neg r \quad r \longrightarrow p \\
\text{Newest Clause and 5: (Revolve on $p$)} \\
p \quad \neg p \lor \neg r \longrightarrow \neg r \\
\text{Newest Clause and 6: (Revolve on $r$)} \\
r \quad \neg r \longrightarrow \emptyset \\
\therefore \text{The set is a Contradiction} \\
\therefore \text{The set is unsatisfiable} \\ 
\quad \text{and does not have a satisfying truth assignment}
\end{array}$$
# Question 2: Applying Resolution
---
1. Use Resolution to decide if $((p \lor q) \land (p \Rightarrow r)) \Rightarrow (p \Rightarrow r)$ is a Theorem
$$\begin{array}{lll}
\text{Negate $\phi$: } \\
\text{1. } \neg(((p \lor q) \land (p \Rightarrow r)) \Rightarrow (p \Rightarrow r)) & && \text{Implication Law}\\
\text{2. } \neg(\neg((p \lor q) \land (p \Rightarrow r)) \lor (p \Rightarrow r))  & && \text{Implication Law} \\
\text{3. } \neg(\neg((p \lor q) \land (\neg p \lor r)) \lor (\neg p \lor r)) & && \text{De Morgan's Law}\\
\text{4. } \neg(\neg(p \lor q) \lor \neg(\neg p \lor r) \lor (\neg p \lor r)) & &&  \text{De Morgan's Law} \\
\text{5. } \neg(\neg(p \lor q) \lor \neg(\neg p \lor r) \lor (\neg p \lor r)) & &&  \text{De Morgan's Law} \\
\text{6. } \neg((\neg p \land \neg q) \lor ( p \land \neg r) \lor (\neg p \lor r)) & &&  \text{De Morgan's Law} \\
\text{7. } \neg (\neg p \land \neg q) \land \neg ( p \land \neg r) \land \neg (\neg p \lor r) & &&  \text{De Morgan's Law} \\
\text{8. } (p \lor q) \land (\neg p \lor r) \land (p \land \neg r) & &&  \text{De Morgan's Law} \\ \\
\text{Clauses: } (p \lor q) \quad (\neg p \lor r) \quad p \quad \neg r \\
\text{Clauses 2 and 3: (Resolve on $p$)} \\
(\neg p \lor r) \quad p \longrightarrow r \\
\text{Inferred Clause and 4: (Resolve on $r$)} \\
r \quad \neg r \longrightarrow \emptyset \\
\text{$\therefore$ The Negated statement is a Contradiction} \\
\text{$\therefore \phi$ is a Theorem}
\end{array}$$
---
$$\begin{array}{lll} 
\text{SHORTCUT: (c.n.f)} \\
\text{As the Formula } A \Rightarrow B \equiv \neg A \lor B \\
\text{The negation of our Formula is: } \\
A \land \neg B \\ \\
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
---
2. There are three suspects for the murder of Peter: Hajo, Nick, and Liz. Hajo says: ‘I didn’t do it. Peter was an old acquaintance of Nick’s. But Liz hated him.’ Nick states: ‘I didn’t do it. I didn’t know Peter. Besides, I was away all week.’ Liz says ‘I didn’t do it. I saw both Hajo and Nick in town with Peter that day; one of them must have done it.’ Assume that the two innocent people are telling the truth, but that the guilty person might not be. Write out the facts using formulae of propositional logic and use Resolution to solve the crime.
$$\begin{array}{lll}
\text{Let $h, n, l$ be Hajo, Nick, and Liz telling the Truth (respectively)} \\
\text{Scenarios: \{h,n,l\}, \{\=h,n,l\},\{h,\=n,l\},\{h,n,\=l\}} \\
\text{• $h$ and $n$ can't be True at once} \\
\text{• $n$ and $l$ can't be True at once} \\
\text{Scenarios: \{h,\=n,l\}} \\
\text{$\therefore$ Nick is lying, so he must be the killer}
\end{array}$$

# Question 3: Operations on Sets
---
1. For sets $X_0, X_1, X_2, \dots$, we write $\bigcap_{i=0}^{\infty} X_i$ to denote the intersection of all these sets ; that is, the set of elements that lie in every one of the sets. Define sets $X_0, X_1, X_2, \dots$ so that 
	- **(a)** For every $X_i$ and every $X_j$ such that $i \neq j$, we have that $X_i \cap X_j \neq \emptyset$ but that $\bigcap_{i=0}^{\infty} X_i = \emptyset$ 
	- **(b)** For any finite subset $S \subset \mathbb{N}$, we have that $\bigcap_{i \in S} X_i$ is infinite but that $\bigcap_{i=0}^{\infty} X_i = \emptyset$

Each set $X_i$ contains all the integers $\gt i$ 
- $X_0 = \{1, 2, 3, 4, 5, \dots\}$
- $X_1 = \{2, 3, 4, 5, 6, \dots\}$
- $X_2 = \{3, 4, 5, 6, 7, \dots\}$

No two sets are the same. Since they are infinite, each set has a common value with at least one other set. Since they are infinite, $\bigcap_{i \in S} X_i$ for a finite subset of set is also infinite. 
But since the sets start on increasingly higher values, there is no single value that is in all sets. 

$\underline{\textbf{Related Pages: }}$
- [[Logic]]
- [[Resolution]]
- [[Logic Practical Week 13]]
- [[Logic Practical Week 14 (Prep)]]
- [[Logic Practical Week 14]]
