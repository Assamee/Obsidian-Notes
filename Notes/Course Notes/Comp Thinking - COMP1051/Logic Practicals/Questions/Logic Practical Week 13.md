Question 3: 
![[Pasted image 20260210191515.png]]1. (¬q ∧ (p ⇒ q)) ⇒ ¬q
$$\begin{aligned} 
(\neg q \land (p \Rightarrow q)) &\Rightarrow \neg q  &&\text{(Implication Law)}\\
(\neg q \land (\neg p \lor q))& &&\text{(Distribution Law)}  \\
(\neg q \land \neg p) \lor (\neg q \land q)& &&\text{(De Morgan's)}\\
\neg(q \lor p) &\Rightarrow \neg q &&\text{(Implication Law)}\\
(q \lor p) \lor \neg q\\
1 &\;\;\checkmark
\end{aligned}$$2. ((p ∨ q) ∧ ¬p) ⇒ q
$$\begin{aligned} 
((p \lor q) \land \neg p)& \Rightarrow q &&\text{(Distribution Law)} \\
(\neg p \land p) \lor (\neg p \land q) \\ 
(\neg p \land q)& \Rightarrow q &&\text{(Implication Law)}\\
\neg(\neg p \land q)& \lor q &&\text{(De Morgan's Law)}\\
(p \lor \neg q)& \lor q \\
1 &\;\;\checkmark
\end{aligned}$$
Question 4:
![[Pasted image 20260210191535.png]]
$$\begin{aligned}
\textbf{Equation 1: }& \\
(a \lor c) \land (b \Rightarrow c) \land (c \Rightarrow a)& &&\text{(Implication Law)}\\
(a \lor c) \land (\neg b \lor c) \land (\neg c \lor a)& &&\text{(Commutativity)}\\
(a \lor c) \land (a \lor \neg c) \land (\neg b \lor c)& &&\text{(Distribution Law)}\\
(a \lor (c \land \neg c))\land (\neg b \lor c)& \\
a \land (\neg b \lor c)& \\[1em]
\textbf{Equation 2: }& \\
(b \Rightarrow c) \land a & &&\text{(Implication Law)}\\
(\neg b \lor c) \land a & &&\text{(Commutative Law)}\\
a \land (\neg b \lor c) \\[1em]
\therefore \textbf{Equation 1 } \equiv \textbf{Equation 2} 
\end{aligned}$$
Question 9: Conjunctive Normal Form
![[Pasted image 20260210180008.png]]1. ((p ∧ ¬q) ∨ r) ⇒ (¬p ∧ ¬r)
	$$\begin{aligned}
	((p \land \neg q) \lor r) \Rightarrow (\neg p \land \neg r)& && \text{(Implication Law)}\\
	\neg((p \land \neg q) \lor r) \lor  (\neg p \land \neg r)& && \text{(De Morgan's)}\\
	(\neg(p \land \neg q) \land \neg r) \lor (\neg p \land \neg r) & && \text{(Distribution Law)}\\
	\neg r \land (\neg p \lor (\neg (p \land \neg q))) & && \text{(De Morgan's)}\\
	\neg r \land (\neg p \lor (\neg p \lor q))\\
	\neg r \land (\neg p \lor q)& \; \checkmark\\
	\end{aligned}$$2. (p ∧ (q ⇒ r)) ⇒ s
	$$\begin{aligned}
	(p \land (q \Rightarrow r)) \Rightarrow s & && \text{(Implication Law)} \\
	\neg(p \land (q \Rightarrow r))\lor s & && \text{(Implication Law)} \\
	\neg(p \land (\neg q \lor r))\lor s & && \text{(De Morgan's)} \\
	(\neg p \lor \neg(\neg q \lor r))\lor s & && \text{(De Morgan's)} \\
	(\neg p \lor (q \land \neg r))\lor s & && \text{(Distribution Law)} \\
	((\neg p \lor q) \land (\neg p \lor \neg r)) \lor s \\[1em]
	\text{General Formula: (Distribution Law)}& \\
	(A \land B) \lor C) \equiv(C \lor A) \land (C \lor B) \\[0.1em]
	\text{Where } A = (\neg p \lor q),  B = (\neg p \lor \neg r), C = s \\[1em]
	\text{Applying the General Formula:} \\
	((\neg p \lor q) \land (\neg p \lor \neg r)) \lor s \\
	(s \lor (\neg p \lor q)) \land (s \lor (\neg p \lor \neg r)) \\
	(s \lor \neg p \lor q) \land (s \lor \neg p \lor \neg r)& \;\checkmark
	\end{aligned}$$

$\underline{\textbf{Related Pages: }}$
- [[Logic]]
- [[Logic Practical Week 14 (Prep)]]
