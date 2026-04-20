# Inner Product Spaces & Orthogonality

> [!Summary] 
**Geometry:** This file abstracts traditional geometry, exploring how we measure distance, angles, and projections across different vector spaces, including complex numbers.
**Content:** Inner Product Spaces, Norm & Distance, Orthogonal Complements, The Gram-Schmidt Process & Complex Matrices

---
## Inner Product Spaces
Definition of an Inner Product:
- In a Real Vector Space $V$
- An Inner Product $f: V \times V \rightarrow \mathbb{R}$  s.t. $\forall \, u,v,w \in V, k \in \mathbb{R}$  
$\textbf{Notation: } \langle u, v \rangle$ means the **Inner Product** of vectors $u$ and $v$
### The Four Axioms of an Inner Product
1. **Symmetry:** $\langle u, v \rangle = \langle v, u \rangle$
2. **Linearity (Additivity):** $\langle u+v, w \rangle = \langle u, w \rangle + \langle v, w \rangle$
3. **Homogeneity:** $\langle ku, v \rangle = k\langle u, v \rangle$
4. **Positivity:** $\langle v, v \rangle \geqslant 0$, and $\langle v, v \rangle = 0 \text{ iff } v = 0$.
	- Inner product of itself is $\geqslant 0$, and only zero, when using the zero vector
**_Note:** Any mathematical operation that satisfies these axioms is an inner product._
---
#### Proof that the dot product is an Inner Product:
- Proving that the standard **Dot Product** on $\mathbb{R}^n$ satisfies the axioms of an **Inner Product**.
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
---
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
---
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
---
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
---
### Norm & Distance
##### Norm:
- The norm (or length) of a vector $v$ is defined as $||v|| = \sqrt{\langle v, v \rangle}$
- The same as Pythagoras: $\sqrt{(v_1)^2 +  (v_2)^2 +  \dots +  (v_n)^2}$
##### Distance:
- The distance between two vectors $u$ and $v$ is defined as $d(u, v) = ||u - v||$
##### Key Properties:
1. $||v|| \geqslant 0$, and $||v|| = 0$ **iff** $v = 0$
2. $||kv|| = |k| \; ||v||$
3. $d(u, v) = d(v, u)$
4. $d(u, v) = 0$ **iff** $u = v$
---
### Orthogonal Complements
#### Orthogonality:
- Two vectors $u$ and $v$, in an inner product space $V$, are orthogonal if $\langle u, v \rangle = 0$
#### Orthogonal Complement:
- **Formal Definition:** Let $W$ be a subspace in an inner product space $V$. The orthogonal complement of $W$, denoted as $W^\perp$, is the set $W^\perp = \{ x \in V \; | \; \langle u, x \rangle \text{ for all } u \in W\}$
- **Simple Definition:** $W^\perp$ is the set of all vectors in $V$ that are perpendicular to **_every_** vector inside subspace $W$. Crucially, $W^\perp$ is also a subspace itself
---
#### Finding the Basis of an Orthogonal Complement $(W^\perp)$
To find $W^\perp$ given a subspace $W = \text{span} (u, v)$:
1. **Setup:** Any vector $x$ in $W^\perp$ must be orthogonal to every basis vector of $W$. So, you must satisfy $\langle u, x \rangle = 0$ and $\langle v, x \rangle = 0$
2. **Linear System:** Expand the inner product equations to form a system of homogenous linear equations $(\text{Equation }= 0)$
3. **Solve:** Find the solution space for the linear system
4. **Basis:** Finding a basis for this solution gives you the basis for $W^\perp$
---
#### Example: Finding the Orthogonal Complement $W^\perp$
**Question:** We have subspace $W = \text{span}(u, v)$ in $\mathbb{R}^4$. Our given vectors are:
$$u = \begin{bmatrix} 2 \\ -3 \\ 5 \\ 4 \end{bmatrix}, \quad 
v = \begin{bmatrix} 0 \\ 1 \\ -4 \\ 7 \end{bmatrix}$$
Find the orthogonal complement $W^\perp$
###### Step 1: Define the Orthogonality Condition
- For an arbitrary vector $x$ to exist in $W^\perp$, it must be orthogonal to every vector in $W$
	$\therefore$ It is also orthogonal to the basis vectors of $W$
	$\therefore$ We must satisfy the two conditions:
$$\langle u, x \rangle = 0 \quad \text{and} \quad \langle v, x \rangle = 0$$
---
###### Step 2: Create the Linear System (Dot Product)
- If our inner product on $\mathbb{R}^4$ is the standard dot product, $W^\perp$ is the solution space of the following linear system
$$\begin{array}{rcrcrcrcr} 2x_1 & - & 3x_2 & + & 5x_3 & + & 4x_4 & = & 0 \\ 
0x_1 & + & x_2 & - & 4x_3 & + & 7x_4 & = & 0 
\end{array}$$
**(Note: The top equation is $\langle u, x \rangle = 0$, and the bottom equation is $\langle v, x \rangle = 0$)**
---
###### Step 3: See the Impact of a Different Inner Product (Weighted)
- What if we change the inner product to a **Weighted Euclidean Inner Product** (with weights $w_1=2$, $w_2=1$, $w_3=3$, and $w_4=1)$?
- Then we multiply each term by its corresponding weight. Then $W^\perp$ becomes the solution space of an entirely different linear system:
$$\begin{array}
\text{Vectors:} \quad 
u = \begin{bmatrix} 2 \\ -3 \\ 5 \\ 4 \end{bmatrix}, \quad 
v = \begin{bmatrix} 0 \\ 1 \\ -4 \\ 7 \end{bmatrix} \\
\begin{array}{rcrcrcrcr} 
4x_1 & - & 3x_2 & + & 15x_3 & + & 4x_4 & = & 0 \\ 
0x_1 & + & x_2 & - & 12x_3 & + & 7x_4 & = & 0 
\end{array} \end{array}$$
 _(Note: For the top equation, we calculated $2(2x_1) + 1(-3x_2) + 3(5x_3) + 1(4x_4) = 0$)_. 
---
 ###### Step 4: Solve the system for the Basis
 - Remember that finding  $W^\perp$ is the same as finding a basis in the solution space of the linear system
$$\left[ \begin{array}{cccc|c} 
 2 & -3 & 5 & 4 & 0 \\ 
 0 & 1 & -4 & 7 & 0 
 \end{array} \right]$$
 - To find the actual basis vectors for $W^\perp$, you would write the system from Step 2 as an augmented matrix then use Gaussian Elimination to find the free variables and extract the resulting basis vectors
---
### Alternative Inner Product Spaces
#### Weighted Euclidean Inner Product
- **Formal Definition:** Let $w_1, \dots, w_n \in \mathbb{R}$ be arbitrary **positive** numbers, called weights. For vectors $u = (u_1, \dots, u_n)$ and $v = (v_1, \dots, v_n)$ in $\mathbb{R}^n$, the weighted Euclidean inner product is defined as:
$$\langle u, v \rangle = w_1 u_1 v_1 + w_2 u_2 v_2 + \dots + w_n u_n v_n$$
- **Simple Definition:** A dot product where some dimensions are multiplied by a specific positive weight. If all weights are 1, it simply becomes the standard dot product
---
#### Example: Calculating the Weighted Euclidean Inner Product
**The Setup:** Consider $\mathbb{R}^2$ with weights $w_1 = 3$ and $w_2 = 2$. 
- Let our vectors be $u = (1, -3)$ and $v = (2, 1)$.
##### Calculation:
$$\begin{aligned} 
\langle u, v \rangle &= w_1(u_1 v_1) + w_2(u_2 v_2) \\ 
&= 3(1 \times 2) + 2(-3 \times 1) \\ 
&= 6 - 6 \\ 
&= 0
\end{aligned}$$
_(Note: Because the result is 0, $u$ and $v$ are orthogonal under this specific weighted inner product, even though their standard dot product would be $-1$)._

---
#### Matrix Inner Product on $\mathbb{R}^n$
- **Formal Definition:** Let $A$ be an invertible  $n \times n$ matrix. Considering vectors in $\mathbb{R}^n$ as column vectors, the inner product generated by $A$ is defined as:
$$\langle u, v \rangle = Au \cdot Av \quad \text{or, equivalently,} \quad \langle u, v \rangle = (Av)^T Au = v^T A^T Au $$
- **Simple Definition:** Multiply both column vectors by matrix $A$ first, and then take the standard dot product of the resulting new vectors.
---
#### Example: Calculating the Matrix Inner Product on $\mathbb{R}^n$
**The Setup:** Let our transformation matrix $A$ and our vectors $u, v \in \mathbb{R}^2$ be:
$$A = \begin{bmatrix} 1 & 1 \\ 
0 & 2 \end{bmatrix}, 
\quad u = \begin{bmatrix} 1 \\
0 \end{bmatrix}, 
\quad v = \begin{bmatrix} 0 \\
1 \end{bmatrix}$$
**The Calculation:** First, multiply both vectors by $A$:
$$Au = \begin{bmatrix} 1 & 1 \\ 
0 & 2 \end{bmatrix} 
\begin{bmatrix} 1 \\ 
0 \end{bmatrix} = \begin{bmatrix} 1 \\ 
0 \end{bmatrix}, \quad Av = \begin{bmatrix} 1 & 1 \\ 
0 & 2 \end{bmatrix} \begin{bmatrix} 0 \\ 
1 \end{bmatrix} = \begin{bmatrix} 1 \\ 
2 \end{bmatrix}$$
Now, take the standard dot product of the resulting vectors:
$$\langle u, v \rangle = Au \cdot Av = (1 \times 1) + (0 \times 2) = 1$$
---
#### Inner Product on Polynomial $\mathbb{P}_n$
- **Formal Definition:** For vectors $p = a_0 + a_1 x + \dots + a_n x^n$ and $q = b_0 + b_1 x + \dots + b_n x^n$ in the space of polynomials $\mathbb{P}_n$, the standard inner product is defined as:
$$\langle p, q \rangle = a_0 b_0 + a_1 b_1 + \dots + a_n b_n$$
- **Simple Definition:** You pair up the matching coefficients from each polynomial and multiply them together, identical to a standard dot product in $\mathbb{R}^{n+1}$
---
#### Example: Calculating Inner Product on Polynomial $\mathbb{P}_n$
**The Setup:** Let our two polynomials in $\mathbb{P}_2$ be:
$$\begin{array}{lll}
p(x) = 2 - 3x + x^2 \\
q(x) = 4 + x - 2x^2 
\end{array}$$
**The Calculation:** Multiply the matching coefficients together and sum them:
$$\begin{aligned} 
\langle p, q \rangle &= (2 \times 4) + (-3 \times 1) + (1 \times -2) \\ 
&= 8 - 3 - 2 \\ 
&= 3 
\end{aligned}$$
---
#### Evaluating the Inner Product on $\mathbb{P}_n$
**Note:** *Same as the Standard Inner Product on $\mathbb{P}_n$ (as we saw before), but we now* **substitute in** _given values_
- **Formal Definition:** For distinct sample points $x_0, x_1, \dots, x_n \in \mathbb{R}$ and vectors $p = p(x)$ and $q = q(x)$ in $\mathbb{P}_n$, the evaluation inner product is defined as:
$$
\langle p, q \rangle = p(x_0)q(x_0) + p(x_1)q(x_1) + \dots + p(x_n)q(x_n)$$
- **Simpler Meaning:** You plug specific $x$-values (sample points) into both polynomials, find their numerical outputs, and calculate the dot product of those resulting numbers
---
#### Example: Calculating the Evaluation of the Inner Product on $\mathbb{P}_n$
**The Setup:** Let our sample points be $x_0 = -2$, $x_1 = 0$, and $x_2 = 2$. Let our polynomials be $p(x) = x^2$ and $q(x) = x + 1$. 
**The Calculation:** Evaluate both polynomials at the sample points and take the dot product of the results:
$$\begin{aligned} 
\langle p, q \rangle &= p(-2)q(-2) + p(0)q(0) + p(2)q(2) \\ 
&= (4 \times -1) + (0 \times 1) + (4 \times 3) \\ 
&= -4 + 0 + 12 \\ 
&= 8 
\end{aligned}$$
---
#### Inner Product on the Continuous Space $C[a,b]$
- **Formal Definition:** For functions $f = f(x)$ and $g = g(x)$ that are continuous and integrable on the interval $[a, b]$, the inner product is defined as:
$$\langle f, g \rangle = \int_a^b f(x)g(x) dx$$
- **Simple Definition:** Multiply the two functions together and integrate them over the given interval to find the total area
---
#### Example: Calculating the Inner Product on the Continuous Space $C[a,b]$
**The Setup:** Consider the interval $[-1, 1]$. Let our continuous functions be $f(x) = x$ and $g(x) = x^2$.
**The Calculation:** Integrate their product over the interval:
$$\begin{aligned} 
\langle f, g \rangle &= \int_{-1}^{1} (x)(x^2) dx \\ 
&= \int_{-1}^{1} x^3 dx \\ 
&= \left[ \frac{1}{4}x^4 \right]_{-1}^{1} \\ 
&= \frac{1}{4}(1)^4 - \frac{1}{4}(-1)^4 \\ 
&= 0 
\end{aligned}$$
_(Note: Because the integral evaluates to 0, the functions $f(x) = x$ and $g(x) = x^2$ are considered orthogonal on the interval_ $[-1, 1]$).

---
## The Gram-Schmidt Process
### Orthogonal & Orthonormal Sets
#### Orthogonal Set:
- A set of vectors in an inner product space is **orthogonal** if all pairs of distinct vectors in it are orthogonal
#### Orthonormal Set:
- An orthonormal set consisting exclusively of unit vectors
##### Key Property:
- If a set of non-zero vectors is orthogonal, it is guaranteed to be **linearly independent**
---
### Orthogonal & Orthonormal Bases
#### Definition:
- An orthogonal (or orthonormal) basis is a basis that is also an orthogonal (or orthonormal) set
#### Orthogonal Shortcut:
- If $S = \{v_1, \dots, v_n\}$ is an orthogonal basis, then the coordinates of any vector $u$ is:
$$u = \frac{\langle u, v_1 \rangle}{||v_1||^2} v_1 + 
\frac{\langle u, v_2 \rangle}{||v_2||^2} v_2 + \dots +
\frac{\langle u, v_n \rangle}{||v_n||^2} v_n$$
#### Orthonormal Shortcut:
- If the basis is orthonormal, all norms are $1$, so the denominators disappear entirely:
$$u = \langle u, v_1 \rangle v_1 + \langle u, v_2 \rangle v_2 + \dots + \langle u, v_n \rangle v_n$$
---
### Orthogonal Projections
#### Projection Theorem:
- If $W$ is a finite-dimension subspace of $V$, every vector $u \in V$ can be uniquely expressed as $u = w_1 + w_2$, where $w_1 \in W$ and $w_2 \in W^\perp$
- **Projection:** The vector $w_1$ is the orthogonal projection of $u$ onto $W$, denoted as $proj_{_W} u$
###### Formula:
- To project $u$ onto $W$ using an orthogonal basis $\{v_1, \dots, v_r\}$:
$$proj_{_W} u = \frac{\langle u, v_1 \rangle}{||v_1||^2} v_1 + \frac{\langle u, v_2 \rangle}{||v_2||^2} v_2 + \dots + \frac{\langle u, v_r \rangle}{||v_r||^2} v_r$$
---
### Algorithm: The Gram-Schmidt Process
##### The Setup:
We are given a standard set of three linearly independent vectors that form a basis for $\mathbb{R}^3$:
$$u_1 = \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}, \quad 
u_2 = \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix}, \quad 
u_3 = \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}$$
##### Stage 1: Finding the Orthogonal Basis (Gram-Schmidt Process)
- **Goal:** Convert our standard basis $\{u_1, u_2, u_3\}$ into an **Orthogonal Set** $\{v_1, v_2, v_3\}$
1. **Step 1:** Set the first vector
$$v_1 = u_1 = \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}$$
2. **Step 2:** Find $v_2$ by subtracting the **orthogonal projection** of $u_2$ onto $v_1$.
$$\begin{array} proj_{_{W_1}} u_2 = \frac{\langle u_2, v_1 \rangle}{||v_1||^2} v_1 = \frac{2}{3} \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix} = \begin{bmatrix} 2/3 \\ 2/3 \\ 2/3 \end{bmatrix} \\ \\
v_2 = u_2 - proj_{_{W_1}} u_2 = \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix} - \begin{bmatrix} 2/3 \\ 2/3 \\ 2/3 \end{bmatrix} = \begin{bmatrix} -2/3 \\ 1/3 \\ 1/3 \end{bmatrix} \end{array}$$
3. **Step 3:** Find $v_3$ by subtracting its projections onto both $v_1$ and $v_2$.
$$\begin{array}{c} proj_{_{W_2}} u_3 = \frac{\langle u_3, v_1 \rangle}{||v_1||^2} v_1 + \frac{\langle u_3, v_2 \rangle}{||v_2||^2} v_2 = \frac{1}{3} \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix} + \frac{1/3}{2/3} \begin{bmatrix} -2/3 \\ 1/3 \\ 1/3 \end{bmatrix} \\ \\
proj_{W_2} u_3 = \begin{bmatrix} 1/3 \\ 1/3 \\ 1/3 \end{bmatrix} + \begin{bmatrix} -1/3 \\ 1/6 \\ 1/6 \end{bmatrix} = \begin{bmatrix} 0 \\ 1/2 \\ 1/2 \end{bmatrix} \\ \\
v_3 = u_3 - proj_{_{W_2}} u_3 = \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix} - \begin{bmatrix} 0 \\ 1/2 \\ 1/2 \end{bmatrix} = \begin{bmatrix} 0 \\ -1/2 \\ 1/2 \end{bmatrix} \end{array}$$
- **Result:** Now we have an **Orthogonal Basis**: $\{v_1, v_2, v_3\}$. Because they are orthogonal and non-zero, they are linearly independent
**The Orthogonal Basis:**
$$\{v_1, v_2, v_3\} = \left\{ \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}, \begin{bmatrix} -2/3 \\ 1/3 \\ 1/3 \end{bmatrix}, \begin{bmatrix} 0 \\ -1/2 \\ 1/2 \end{bmatrix} \right\}$$
---
##### Stage 2: Creating the Orthonormal Set
- **Goal:** Convert our orthogonal basis into an **Orthonormal Basis** $\{q_1, q_2, q_3\}$ by dividing each vector by its norm
**Calculate the Norms:**
$$\begin{array}{c} ||v_1|| = \sqrt{3} \\ \\
||v_2|| = \sqrt{4/9 + 1/9 + 1/9} = \frac{\sqrt{6}}{3} \\ \\
||v_3|| = \sqrt{0 + 1/4 + 1/4} = \frac{1}{\sqrt{2}} \end{array}$$

**Normalise:**
$$q_1 = \begin{bmatrix} 1/\sqrt{3} \\ 1/\sqrt{3} \\ 1/\sqrt{3} \end{bmatrix}, \quad q_2 = \begin{bmatrix} -2/\sqrt{6} \\ 1/\sqrt{6} \\ 1/\sqrt{6} \end{bmatrix}, \quad q_3 = \begin{bmatrix} 0 \\ -1/\sqrt{2} \\ 1/\sqrt{2} \end{bmatrix}$$
---
###### Stage 3: The Orthogonal Shortcut
- **Goal:** We want to find the coordinates of a new vector $x$ using our new orthogonal basis $\{v_1, v_2, v_3\}$
$$x = \begin{bmatrix} 0 \\ 3 \\ 3 \end{bmatrix}$$
- **The Old Way:** We would have to solve the system $c_1v_1 + c_2v_2 + c_3v_3 = x$ using a matrix and Gaussian elimination
- **The Shortcut:** Because the basis is orthogonal, we can find the coordinates instantly using the shortcut formula:
$$x = \frac{\langle x, v_1 \rangle}{||v_1||^2} v_1 + \frac{\langle x, v_2 \rangle}{||v_2||^2} v_2 + \frac{\langle x, v_3 \rangle}{||v_3||^2} v_3$$
- **Calculating the Coefficients:**
    - **Coordinate 1:** $\langle x, v_1 \rangle = 6$, and $||v_1||^2 = 3 \implies 6 \div 3 = \mathbf{2}$
    - **Coordinate 2:** $\langle x, v_2 \rangle = 2$, and $||v_2||^2 = 2/3 \implies 2 \div (2/3) = \mathbf{3}$
    - **Coordinate 3:** $\langle x, v_3 \rangle = 0$, and $||v_3||^2 = 1/2 \implies 0 \div (1/2) = \mathbf{0}$
- **Result:** The vector $x$ is simply $2v_1 + 3v_2 + 0v_3$. The coordinates are $(2, 3, 0)$
---
## Complex Matrices
### Types of Complex Matrices
#### Conjugate Matrix $(\overline{A})$
- A matrix obtained by replacing every element $a_{ij}$ of a complex matrix $A$ with its complex conjugate $\overline{a}_{ij}$  (e.g. $3 + 2i$ becomes $3 - 2i$)
#### Conjugate Transpose $(A^* \text{ or }A^H)$
- The transpose of the conjugate of a complex matrix, mathematically defined as $A^* = (\overline{A})^T$
---
#### Hermitian Matrix
- A square complex matrix $A$ that is equal to its own conjugate transpose, such that $A = A^*$
- This is the complex equivalent of a symmetric matrix (reflects across the main diagonal). If you reflect the entries across the main diagonal, they must be complex conjugates of each other
_(Note: This forces the main diagonal to consist entirely of real numbers)_
##### Key Properties:
1. **Real Eigenvalues**: The eigenvalues of a Hermitian matrix are always purely real numbers (the imaginary part is zero)
2. **Orthogonal Eigenvectors**: The eigenvectors corresponding to different eigenvalues are perfectly orthogonal to each other
---
#### Skew-Hermitian Matrix
- A square complex matrix $A$ where its conjugate transpose is equal to its negative, such that $A^* = -A$
#### Unitary Matrices
- A square complex matrix $U$ whose conjugate transpose is also its inverse, such that $U^* U = UU^* = I$
---
### Properties of Complex Dot Products
#### Conjugate Symmetry
- The dot product of two complex vectors is the complex conjugate of their reversed dot product: $u \cdot v = \overline{v \cdot u}$
- Unlike real vectors where $u \cdot v = v \cdot u$, swapping the order of complex vectors changes the sign of the imaginary part
#### Linearity (First Argument)
- The dot product is linear with respect to vector addition and scalar multiplication in its first argument: $(u + w) \cdot v = u \cdot v + w \cdot v$ and $(cu) \cdot v = c(u \cdot v)$
#### Anti-Linearity (Second Argument)
- Pulling a complex scalar $c$ out of the second vector results in its complex conjugate: $u \cdot (cv) = \overline{c}(u \cdot v)$
- If you multiply the _second_ vector by a scalar like $3i$, it becomes $-3i$ when you pull it out to the front of the dot product
#### Positive Definitiveness
- The dot product of any complex vector with itself is always a real, non-negative scalar: $v \cdot v \ge 0$. Furthermore, $v \cdot v = 0$ if and only if $v = \mathbf{0}$
---
#### Euclidean Norm $(||v||)$
- The magnitude of a vector: $||v|| = \sqrt{v \cdot v} = \sqrt{|v_1|^2 + \dots + |v_n|^2}$
---
### The Hermitian Inner Product
#### Hermitian Inner Product on $\mathbb{C}^n$
* **Formal Definition:** Considering vectors in $\mathbb{C}^n$ as column vectors, the **Hermitian inner product** is defined as:
$$\langle u, v \rangle = u^\dagger v $$
- **Simple Definition:** Similar to a standard dot product, but you take the Hermitian conjugation (the conjugate transpose, denoted as $u^\dagger$) of the first vector before multiplying
---
#### Example: Hermitian Inner Product on $\mathbb{C}^n$
**The Setup:** Let our complex column vectors be:
$$u = \begin{bmatrix} 1+i \\ 
5 \end{bmatrix}, \quad v = \begin{bmatrix} 2 \\ 
3+4i \end{bmatrix}$$
**The Calculation:** Find $u^\dagger$ by transposing $u$ and flipping the sign of the imaginary parts, then perform matrix multiplication with $v$:
$$\begin{aligned} \langle u, v \rangle &= u^\dagger v \\ 
&= \begin{bmatrix} 1-i & 5 \end{bmatrix} 
\begin{bmatrix} 2 \\ 3+4i \end{bmatrix} \\ 
&= (1-i)(2) + (5)(3+4i) \\ 
&= (2 - 2i) + (15 + 20i) \\ 
&= 17 + 18i \end{aligned}$$
---
#linear-algebra/geometry #linear-algebra/inner-products #linear-algebra/gram-schmidt #linear-algebra/complex-matrices 