![[Pasted image 20260213141159.png]]
###### 1. $p \lor (q \land r) \vdash p \lor q$
$$\begin{array}{lll}
\text{1. } p \lor (q \land r) & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{2. } p & && \text{Assume}\\
\text{3. } p \lor q & && \lor i_1 \; 2 \\
\hline \end{array} \\
\begin{array}{|lll|} \hline
\text{4. } q \land r & && \text{Assume}\\
\text{5. } q & && \land e_1 \; 4\\
\text{6. } p \lor q & && \lor i_2 \; 5 \\
\hline \end{array} \\
\text{7. } p \lor q & && \lor e \; 1, 2 \textminus 3, 4 \textminus 6
\end{array}$$
###### 2. $p \Rightarrow r, q \Rightarrow s, p \lor q \vdash r \lor s$
$$\begin{array}{lll}
\text{1. } p \Rightarrow r & && \text{Premise} \\
\text{2. } q \Rightarrow s & && \text{Premise} \\
\text{3. } p \lor q & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{4. } p & && \text{Assume} \\
\text{5. } r & && \Rightarrow e \; 4, 1 \\
\text{6. } r \lor s & && \lor e_1 \; 5 \\
\hline \end{array} \\
\begin{array}{|lll|} \hline
\text{7. } q & && \text{Assume} \\
\text{8. } s & && \Rightarrow e \; 7, 2\\
\text{9. } r \lor s & && \lor e_2 \; 8 \\
\hline \end{array} \\
\text{10. } r \lor s & && \lor e \; 3, 4 \textminus 6, 7 \textminus 9
\end{array}$$
###### 3. $p \land (q \lor r) \vdash (p \land q) \lor (p \land r)$
$$\begin{array}{lll}
\text{1. } p \land (q \lor r) & && \text{Premise}\\
\text{2. } p & && \land e \; 1 \\ 
\text{3. } q \lor r & && \land e \; 1 \\
\begin{array}{|lll|} \hline
\text{4. } q & && \text{Assume} \\ 
\text{5. } p \land q & && \land i \; 2, 4 \\
\text{6. } (p \land q) \lor (p \land r) & && \lor i_1 \; 5 \\
\hline \end{array} \\
\begin{array}{|lll|} \hline
\text{7. } r & && \text{Assume} \\ 
\text{8. } p \land r & && \land i \; 2,7 \\
\text{9. } (p \land q) \lor (p \land r) & && \lor i_2 \; 8 \\
\hline \end{array} \\
\text{10. } (p \land q) \lor (p \land r) & && \lor e \;  3, 4 \textminus6, 7 \textminus 9
\end{array}$$
###### ![[Pasted image 20260213153750.png]]
###### 1. $\neg (r \lor t) \vdash \neg r \land \neg t$
$$\begin{array}{lll}
\text{1. } \neg (r \lor t) & && \text{Premise} \\
\begin{array}{|lll|} \hline 
\text{2. } r & && \text{Assume} \\
\text{3. } r \lor t & && \lor i_1 \; 2 \\
\text{4. } \bot & && \bot i \;1, 3 \\
\hline \end{array} \\
\text{5. } \neg r & && \neg i \; 2 \textminus 4\\
\begin{array}{|lll|} \hline 
\text{6. } t & && \text{Assume} \\
\text{7. } r \lor t & && \lor i_2 \; 2 \\
\text{8. } \bot & && \bot i \;1, 7 \\
\hline \end{array} \\
\text{9. } \neg t & && \neg i \; 6 \textminus 8\\
\text{10. } \neg r \land \neg t & && \land i \; 5, 9\\
\end{array}$$
###### 2. $p \Rightarrow (q \lor r), \neg q, \neg r \vdash \neg p$
$$\begin{array}{lll}
\text{1. } p \Rightarrow (q \lor r) & && \text{Premise} \\
\text{2. } \neg q & && \text{Premise} \\
\text{3. } \neg r & && \text{Premise} \\
\begin{array}{|lll|} \hline
\text{4. } p & && \text{Assume} \\
\text{5. } q \lor r & && \Rightarrow e\; 4, 1\\
\text{6. } q & && \lor e_1 \; 6 \\
\text{7. } \bot & && \bot i \;  \\
\hline \end{array} \\
\text{8. } \neg p & && \neg i \; 4 \textminus 7 \\
\end{array}$$
###### 4. 