Question 1: Natural Deduction $(\land \text{ and } \Rightarrow)$
![[Pasted image 20260210230540.png]]
1. $(a \land b) \Rightarrow c, b \Rightarrow a, b \vdash c$
	$$\begin{array}{lll}
	\text{1. } (a \land b) \Rightarrow c & && \text{Premise}\\
	\text{2. } b\Rightarrow a & && \text{Premise}\\
	\text{3. } b & && \text{Premise}\\
	\text{4. } a & && e \Rightarrow 3, 2\\
	\text{5. } a \land b & && i \land 4, 3\\
	\text{6. } c \;\; \checkmark & && e \Rightarrow 5, 1\\
	\end{array}$$
2. $p \Rightarrow (q \Rightarrow r) \vdash (p \land q) \Rightarrow r$
	$$\begin{array}{lll}
	\text{1. } p \Rightarrow (q \Rightarrow r) & && \text{Premise}\\
	\begin{array}{|lll|} \hline
	\text{2. } p \land q & && \text{Assume}\\
	\text{3. } p & && \land e_1 \; 2\\
	\text{4. } q & && \land e _2 \; 2\\
	\text{5. } q \Rightarrow r & && e \Rightarrow 3, 1\\
	\text{6. } r & && e \Rightarrow 4, 5\\
	\hline \end{array} \\
	\text{7. } (p \land q) \Rightarrow r & && \Rightarrow i \; 2 \textminus 6 \\
	\end{array}$$
3. $(A \Rightarrow B) \vdash (B \Rightarrow C) \Rightarrow (A \Rightarrow C)$
	$$\begin{array}{lll}
	\text{1. } (A \Rightarrow B) & && \text{Premise}\\
	\begin{array}{|lll|} \hline
	\text{2. } B \Rightarrow C & && \text{Assume}\\
	\begin{array}{|lll|} \hline 
	\text{3. } A & && \text{Assume}\\
	\text{4. } B & && e \Rightarrow 1, 3\\
	\text{5. } C & && e \Rightarrow 4, 2\\
	\hline \end{array} \\
	\text{6. } A \Rightarrow C & && \Rightarrow i \; 3 \textminus 5\\
	\hline \end{array} \\
	\text{7. } (B \Rightarrow C) \Rightarrow (A \Rightarrow C) & && \Rightarrow i \; 2 \textminus 6\\
	\end{array}$$
4. **The Logic:**
**Goal:** $r \Rightarrow (p \Rightarrow q)$
    - Open **Box 1**: Assume **$r$**.
    - **New Goal:** $p \Rightarrow q$
        - Open **Box 2**: Assume **$p$**.
        - **New Goal:** $q$
            - Use premises to find $q$.
        - Close Box 2.
    - Close Box 1.
$p \Rightarrow (q \land r) \vdash r \Rightarrow (p \Rightarrow q)$
$$\begin{array}{lll}
\text{1. } p \Rightarrow (q \land r) & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{2. }  r & && \text{Assume}\\
\begin{array}{|lll|} \hline
\text{3. }  p & && \text{Assume}\\
\text{4. }  q \land r & && e \Rightarrow 3, 1\\
\text{5. }  r & && \land e_2 \; 4\\
\text{6. }  q & && \land e_1 \; 4\\
\hline \end{array} \\
\text{7. }  p \Rightarrow q & && i \Rightarrow 3 \textminus 6\\
\hline \end{array} \\
\text{8. } r \Rightarrow (p \Rightarrow q)& && i \Rightarrow 2 \textminus 7
\end{array}$$
# Extra Questions
1. $p \Rightarrow q, q \Rightarrow r \vdash p \Rightarrow r$
$$\begin{array}{lll}
\text{1. } p \Rightarrow q & && \text{Premise} \\
\text{2. } q \Rightarrow r & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{3. } p & &&  \text{Assume}\\
\text{4. } q & &&  e \Rightarrow 3, 1\\
\text{5. } r & &&  e \Rightarrow 4, 2\\
\hline \end{array} \\
\text{6. } p \Rightarrow r& && i \Rightarrow 3 \textminus 5\\
\end{array}$$
2. $p \Rightarrow (q \Rightarrow r) \vdash q \Rightarrow (p \Rightarrow r)$
$$\begin{array}{lll}
\text{1. } p \Rightarrow (q \Rightarrow r) & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{2. } q & && \text{Assume}\\
\begin{array}{|lll|} \hline
\text{3. } p & && \text{Assume}\\
\text{4. } q \Rightarrow r & && e \Rightarrow 3, 1 \\
\text{5. } r & && e \Rightarrow 2, 4 \\
\hline \end{array} \\
\text{6. } p \Rightarrow r & && i \Rightarrow 3 \textminus 5\\
\hline \end{array} \\
\text{7. } q \Rightarrow (p \Rightarrow r) & && i \Rightarrow 2 \textminus 6
\end{array}$$
3. $p \vdash q \Rightarrow (p \land q)$
$$\begin{array}{lll}
\text{1. } p & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{2. } q & && \text{Assume} \\
\text{3. } p \land q & && \land i \; 1, 2\\
\hline \end{array} \\
\text{4. }q \Rightarrow (p \land q) & && i \Rightarrow 2 \textminus3
\end{array}$$
4. $(p \land q) \Rightarrow r \vdash p \Rightarrow (q \Rightarrow r)$
$$\begin{array}{lll}
\text{1. } (p \land q) \Rightarrow r & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{2. } p & && \text{Assume}\\
\begin{array}{|lll|} \hline
\text{3. } q & && \text{Assume}\\
\text{4. } p \land q & && \land i \; 2, 3\\
\text{5. } r & && e \Rightarrow 4, 1\\
\hline \end{array} \\
\text{6. } q \Rightarrow r & && i \Rightarrow 3 \textminus 5\\
\hline \end{array} \\
\text{7. } p \Rightarrow (q \Rightarrow r) & && i \Rightarrow 2 \textminus 6\\
\end{array}$$
---
### Disjunction:
1. 





$\underline{\textbf{Related Pages: }}$
- [[Logic]]
- [[Logic Practical Week 13]]
