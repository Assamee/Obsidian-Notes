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
### The Gram-Schmidt Process
- The algorithm converts any standard basis $\{u_1, \dots, u_n\}$ into an orthogonal basis $\{v_1, \dots, v_n\}$ for the exact same subspace
#### Algorithm:
1. **Step 1:** Set the first orthogonal vector equal to the first original vector
$$v_1 = u_1$$
2. **Step 2:** Take the second vector ($u_2$) and subtract its projection onto $v_1$
$$v_2 = u_2 - proj_{_{W_1}} u_2 = u_2 - \frac{\langle u_2, v_1 \rangle}{||v_1||^2} v_1$$
3. **Step 3:** Take the third vector ($u_3$) and subtract its projections onto both $v_1$ and $v_2$
$$v_3 = u_3 - proj_{_{W_2}} u_3 = u_3 - \frac{\langle u_3, v_1 \rangle}{||v_1||^2} v_1 - \frac{\langle u_3, v_2 \rangle}{||v_2||^2} v_2$$
4. **Iterate:** Continue this pattern for $n$ steps
5. **Optional Final Step:** If an _orthonormal_ basis is needed, normalise all resulting $v_i$ vectors at the end
---
### Example: Gram-Schmidt

^0ca6fd
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
$\underline{\textbf{Related Pages: }}$
- [[Course Notes/MCS - COMP1021/Linear Algebra/Lecture Notes/Inner Product Spaces]]
- [[QR Decomposition & Least Squares]]
- [[Linear Regression]]