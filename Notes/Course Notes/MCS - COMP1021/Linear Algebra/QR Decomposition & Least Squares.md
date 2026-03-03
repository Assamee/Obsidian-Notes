### QR Decomposition
- **Formal Definition:** If $A$ is an $m \times n$ matrix with linearly independent column vectors, then $A$ can be factored as $A = QR$, where $Q$ is an $m \times n$ matrix with orthonormal column vectors, and $R$ is an $n \times n$ invertible upper triangular matrix
### Algorithm: Factoring into $Q$ and $R$
To find the QR decomposition of matrix $A$, you do Gram-Schmidt on its columns
1. **Step 1: Identify the column vectors**
	- Treat the columns of matrix $A$ as your standard basis vectors $\{u_1, u_2, \dots, u_n\}$
2. **Step 2: Gram-Schmidt (Find $Q$)** 
	- Apply the Gram-Schmidt process to these column vectors to find an **orthonormal** basis $\{q_1, q_2, \dots, q_n\}$
	- Place these orthonormal vectors side-by-side to form the columns of matrix $Q$
3. **Step 3: Construct the Upper Triangular Matrix $(R)$**
	- The matrix $R$ is formed by taking the inner products (dot products) of your original $u$ vectors with your new orthonormal $q$ vectors
$$R = \begin{bmatrix} \langle u_1, q_1 \rangle & \langle u_2, q_1 \rangle & \dots & \langle u_n, q_1 \rangle \\ 0 & \langle u_2, q_2 \rangle & \dots & \langle u_n, q_2 \rangle \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \langle u_n, q_n \rangle \end{bmatrix}$$
_**Shortcut for $R$:** Note that the diagonal of $R$ $(\langle u_1, q_1 \rangle$, $\langle u_2, q_2 \rangle \text{, etc.)}$ are the norms of the orthogonal vectors $||v_i||$ calculated during the Gram-Schmidt Process (Before they were normalised)

---
### Example: QR Decomposition
**The Setup:**
We want to find the QR decomposition of the following $3 \times 3$ matrix $A$:
$$A = \begin{bmatrix} 1 & 0 & 0 \\ 1 & 1 & 0 \\ 1 & 1 & 1 \end{bmatrix}$$
###### Step 1: Identify the Column Vectors
- Treat the columns of matrix $A$ as your standard basis vectors $\{u_1, u_2, u_3\}$
$$u_1 = \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}, \quad u_2 = \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix}, \quad u_3 = \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}$$
---
###### Step 2: Gram-Schmidt (Find $Q$)
- We apply the Gram-Schmidt process to these exact vectors $\{q_1, q_2, q_3\}$ (which we calculated here [[Gram-Schmidt#^0ca6fd|Gram-Schmidt Example]])
- Place these orthonormal vectors side-by-side to form the columns of matrix $Q$:
$$Q = \begin{bmatrix} \frac{1}{\sqrt{3}} & -\frac{2}{\sqrt{6}} & 0 \\ \frac{1}{\sqrt{3}} & \frac{1}{\sqrt{6}} & -\frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{3}} & \frac{1}{\sqrt{6}} & \frac{1}{\sqrt{2}} \end{bmatrix}$$
---
###### Step 3: Construct the Upper Triangular Matrix ($R$)
- The matrix $R$ is formed by taking the inner products of our original $u$ vectors with our new orthonormal $q$ vectors
- Using the **Shortcut for $R$**, the diagonal entries are simply the norms of the orthogonal vectors $||v_i||$ that we calculated _before_ they were normalised in the previous example ($\sqrt{3}$, $\frac{\sqrt{6}}{3}$, and $\frac{1}{\sqrt{2}}$)
$$R = \begin{bmatrix} \langle u_1, q_1 \rangle & \langle u_2, q_1 \rangle & \langle u_3, q_1 \rangle \\ 0 & \langle u_2, q_2 \rangle & \langle u_3, q_2 \rangle \\ 0 & 0 & \langle u_3, q_3 \rangle \end{bmatrix}$$
- Now, we calculate the remaining inner products for the upper triangle:
    - $\langle u_2, q_1 \rangle = (0)\left(\frac{1}{\sqrt{3}}\right) + (1)\left(\frac{1}{\sqrt{3}}\right) + (1)\left(\frac{1}{\sqrt{3}}\right) = \mathbf{\frac{2}{\sqrt{3}}}$
        
    - $\langle u_3, q_1 \rangle = (0)\left(\frac{1}{\sqrt{3}}\right) + (0)\left(\frac{1}{\sqrt{3}}\right) + (1)\left(\frac{1}{\sqrt{3}}\right) = \mathbf{\frac{1}{\sqrt{3}}}$
        
    - $\langle u_3, q_2 \rangle = (0)\left(-\frac{2}{\sqrt{6}}\right) + (0)\left(\frac{1}{\sqrt{6}}\right) + (1)\left(\frac{1}{\sqrt{6}}\right) = \mathbf{\frac{1}{\sqrt{6}}}$
- Fill in the values to get our final $R$ matrix:
$$R = \begin{bmatrix} \sqrt{3} & \frac{2}{\sqrt{3}} & \frac{1}{\sqrt{3}} \\ 0 & \frac{\sqrt{6}}{3} & \frac{1}{\sqrt{6}} \\ 0 & 0 & \frac{1}{\sqrt{2}} \end{bmatrix}$$
**Final Result:**
Matrix $A$ has now been successfully decomposed into $A = QR$

---
