## Inner Product
Definition of an Inner Product:
- In a Real Vector Space $V$
- An Inner Product $f: V \times V \rightarrow \mathbb{R}$  s.t. $\forall \, u,v,w \in V, k \in \mathbb{R}$  
$\textbf{Notation: } \langle u, v \rangle$ means the **Inner Product** of vectors $u$ and $v$
##### The 4 Axioms of an Inner Product: 
1. **Symmetry:** $\langle u, v \rangle = \langle v, u \rangle$
2. **Linearity (Additivity):** $\langle u+v, w \rangle = \langle u, w \rangle + \langle v, w \rangle$
3. **Homogeneity:** $\langle ku, v \rangle = k\langle u, v \rangle$
4. **Positivity:** $\langle v, v \rangle \geqslant 0$, and $\langle v, v \rangle = 0 \text{ iff } v = 0$.
	- Inner product of itself is $\geqslant 0$, and only zero, when using the zero vector

#### Proof that the dot product is an Inner Product:
- Proving that the standard **Dot Product** on $\mathbb{R}^n$ satisfies the axioms of an Inner Product.
###### 1. Symmetry Proof: 
Prove that: $\langle u, v \rangle = \langle v, u \rangle$
$$
\begin{aligned}
\text{Let } u, v &\in \mathbb{R}^n \\
\langle u, v \rangle &= u_1 v_1 + u_2 v_2 + \dots + u_n v_n && \text{(Dot Product Definition)} \\
&= v_1 u_1 + v_2 u_2 + \dots + v_n u_n && \text{(Commutativity: } ab = ba \text{)} \\
\langle u, v \rangle &= \langle v, u \rangle \quad \checkmark
\end{aligned}
$$
###### 2. Linearity (Additivity) Proof: 
Prove that: $\langle u+v, w \rangle = \langle u, w \rangle + \langle v, w \rangle$
$$
\begin{aligned}
&\text{(Start with the Dot Product definition)} \\
\langle u+v, w \rangle &=  (u_1+v_1)w_1 + (u_2+v_2)w_2 + \dots + (u_n+v_n)w_n\\ 
&= \sum_{i=1}^{n} (u_i + v_i)w_i\\
&= \sum_{i=1}^{n} (u_i w_i + v_i w_i) \\
&= \sum_{i=1}^{n} u_i w_i + \sum_{i=1}^{n} v_i w_i \\
\langle u+v, w \rangle &= \langle u, w \rangle + \langle v, w \rangle \quad \checkmark
\end{aligned}
$$
###### 3. Homogeneity Proof: 
Prove that: $\langle ku, v \rangle = k\langle u, v \rangle$
$$
\begin{aligned}
&\text{(Start with the Dot Product definition)} \\
\langle ku, v \rangle &=  k(u_1 v_1) + k(u_2 v_2) + \dots + k(u_n v_n)\\ 
&= k(u_1 v_1 + u_2 v_2 + \dots + u_n v_n) \\
\langle ku, v \rangle  &= k\langle u, v \rangle \quad \checkmark
\end{aligned}
$$
###### 4. Positivity Proof: 
Prove that: $\langle v, v \rangle \geqslant 0$, and $\langle v, v \rangle = 0 \iff  v = 0$.
- Inner product of itself is $\geqslant 0$, and only zero when $v$ is the zero vector
$$\begin{aligned} 
\text{Part A: } & \text{Show } \langle v, v \rangle \geqslant 0 \\ \langle v, v \rangle &= v_1 v_1 + v_2 v_2 + \dots + v_n v_n \\ 
&= v_1^2 + v_2^2 + \dots + v_n^2 && \text{(Sum of Squares)} \\ &\text{Since } v_i \in \mathbb{R}, \text{ then } v_i^2 \geqslant 0 && \text{(Real squares are non-negative)} \\ 
&\therefore \sum_{i=1}^{n} v_i^2 \geqslant 0 \implies \langle v, v \rangle \geqslant 0 \quad \checkmark \\[1em]
\text{Part B: } & \text{Show } \langle v, v \rangle = 0 \iff v = \mathbf{0} \\ 
\langle v, v \rangle &= 0 \\
\sum_{i=1}^{n} v_i^2 &= 0 \\ 
\implies v_i^2 &= 0 \text{ for all } i && \text{(Sum is 0 only if all terms are 0)} \\ 
\implies v_i &= 0 \text{ for all } i \\ 
\therefore v &= \mathbf{0} \quad \checkmark \\[1em]
\text{Extra: If } v &= \mathbf{0} \implies \langle v, v \rangle = 0^2 + \dots + 0^2 = 0. \quad \checkmark &&\text{(Proof of the other direction of iff)}\\
\end{aligned}$$

