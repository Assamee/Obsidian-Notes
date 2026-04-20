# Eigenvalues, Diagonalisation & Spectral Theory

> [!Summary] 
**Theory:** 
This file covers Matrix Theory and matrix decomposition
**Content:** 
Eigenvalues, Eigenvectors, Similar Matrices, Orthogonal Diagonalisability,  Eigendecomposition & Spectral Decomposition

---
## Eigenvalues & Eigenvectors
### Definitions & The Core Equation
#### Eigenvector $(x)$
- A non-zero vector $x$ such that when a given square matrix $A$ is applied to it, the resulting vector is a scalar multiple of $x$ (like invariant lines)
#### Eigenvalues $(\lambda)$
- The scalar $\lambda$ associated with an eigenvector $x$ such that the equation $Ax = \lambda x$ holds true. It tells you **how much** the eigenvector gets stretched or squashed (e.g. if $\lambda = 2$, the vector doubles in length)
#### The Core Equation
The relationship between a matrix $A$, its eigenvector $x$, and its eigenvalue $\lambda$ is defined by:
$$Ax = \lambda x$$

---
### Algorithm: Finding Eigenvalues & Eigenvectors
To find eigenvalues and eigenvectors we use the characteristic equation:
1. **Set up the Characteristic Equation**: Rearrange $Ax = \lambda x$ to $(A - \lambda I)x = 0$ (where $I$ is the identity matrix). For $x$ to be a non-zero vector, the matrix $(A - \lambda I)$ must not be invertible. Therefore, its determinant must be zero:
$$\det(A - \lambda I) = 0$$
2. **Solve for the Eigenvalues ($\lambda$)**: Compute the determinant of $(A - \lambda I)$. This will give you a polynomial equation (the characteristic polynomial). The eigenvalues are the roots of the polynomial
3. **Substitute $\lambda$ back in**: Take your first eigenvalue and substitute it into the matrix $(A - \lambda I)$
4. **Solve for the Eigenvector ($x$)**: Solve the resulting homogeneous linear system $(A - \lambda I)x = 0$ (usually via Gaussian elimination) to find the components of the vector $x$
5. **Repeat**: Repeat steps 3 and 4 for every eigenvalue you found to get all corresponding eigenvectors
---
### Example: Finding Eigenvalues & Eigenvectors
**Question:** Find the eigenvalues and eigenvectors for the matrix $A$:
$$A = \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix}$$
#### Step 1: Set up the Characteristic Equation
We need to find the determinant of $(A - \lambda I)$ and set it to zero. First, we subtract $\lambda$ from the main diagonal of $A$:
$$A - \lambda I = \begin{pmatrix} 4 - \lambda & 1 \\ 2 & 3 - \lambda \end{pmatrix}$$
Now, we calculate the determinant of this new matrix:
$$\det(A - \lambda I) = (4 - \lambda)(3 - \lambda) - (1)(2) = 0$$
#### Step 2: Solve for the Eigenvalues ($\lambda$)
Expand the brackets and simplify to find the characteristic polynomial:
$$\begin{array}{rll} (12 - 4\lambda - 3\lambda + \lambda^2) - 2 &= 0 \\ \lambda^2 - 7\lambda + 10 &= 0 \end{array}$$
Factorise the quadratic equation to find the roots (our eigenvalues):
$$(\lambda - 5)(\lambda - 2) = 0$$
So, our two eigenvalues are **$\lambda_1 = 5$** and **$\lambda_2 = 2$**
#### Step 3 & 4: Substitute $\lambda_1 = 5$ and Solve for its Eigenvector
Substitute $\lambda = 5$ back into our $(A - \lambda I)$ matrix:
$$\begin{pmatrix} 4 - 5 & 1 \\ 2 & 3 - 5 \end{pmatrix} = \begin{pmatrix} -1 & 1 \\ 2 & -2 \end{pmatrix}$$
Set up the homogeneous system $(A - \lambda I)x = 0$:
$$\begin{pmatrix} -1 & 1 \\ 2 & -2 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$
This gives us two equations, but they are multiples of each other (which is exactly what should happen!):
$$-x_1 + x_2 = 0 \implies x_1 = x_2$$
To find an eigenvector, we just pick a simple, non-zero value that satisfies this rule. Let $x_1 = 1$. Then $x_2 = 1$
###### Eigenvector 1:
$$v_1 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$$
#### Step 5: Repeat for $\lambda_2 = 2$
Substitute $\lambda = 2$ back into our $(A - \lambda I)$ matrix:
$$\begin{pmatrix} 4 - 2 & 1 \\ 2 & 3 - 2 \end{pmatrix} = \begin{pmatrix} 2 & 1 \\ 2 & 1 \end{pmatrix}$$
Set up the homogeneous system:
$$\begin{pmatrix} 2 & 1 \\ 2 & 1 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$
This gives us the equation:
$$2x_1 + x_2 = 0 \implies x_2 = -2x_1$$
Again, pick a simple value. Let $x_1 = 1$. Then $x_2 = -2$.
###### Eigenvector 2:
$$v_2 = \begin{pmatrix} 1 \\ -2 \end{pmatrix}$$
---
### Eigenspaces & Multiplicity
#### Definitions
##### Eigenspace **$(E_{\lambda})$
- The set of all eigenvectors corresponding to a specific eigenvalue $\lambda_0$, together with the zero vector. It is the null space (or kernel) of the matrix $(A - \lambda I)$
- If an eigenvalue is the "stretch factor", the eigenspace is the entire line, plane, or 3D space of all possible vectors that get stretched by that exact amount
##### Basis for an Eigenspace
- A set of linearly independent eigenvectors that spans the eigenspace $E_{\lambda}$
##### Algebraic Multiplicity
- The number of times a specific eigenvalue $\lambda$ appears as a repeated root of the characteristic polynomial
##### Geometric Multiplicity
- The dimension of the eigenspace $E_{\lambda}$. The number of linearly independent basis vectors in the eigenspace
---
### Example: Finding the Eigenspace & Multiplicity
Note that this is the exact same matrix we just solved:
$$A = \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix}$$
#### Step 1: Check Algebraic Multiplicity from the Polynomial
Our characteristic polynomial was:
$$(\lambda - 5)(\lambda - 2) = 0$$
- The root $\lambda = 5$ appears exactly once. Therefore, its **Algebraic Multiplicity is 1**
- The root $\lambda = 2$ appears exactly once. Therefore, its **Algebraic Multiplicity is 1**
#### Step 2: Define the Eigenspace and Basis for $\lambda = 5$
When we solved $(A - 5I)x = 0$, we found the defining relationship was $x_1 = x_2$
###### The Eigenspace ($E_5$):
$\therefore$ This is the set of all vectors where the top and bottom numbers are identical
$$E_5 = \left\{ \begin{pmatrix} c \\ c \end{pmatrix} \Big| c \in \mathbb{R} \right\}$$
- **The Basis**: We factor out the constant $c$ to find our core direction vector
$$\text{Basis for } E_5 = \left\{ \begin{pmatrix} 1 \\ 1 \end{pmatrix} \right\}$$
- **Geometric Multiplicity**: Because our basis contains exactly $1$ vector, the **Geometric Multiplicity is 1**
#### Step 3: Define the Eigenspace and Basis for $\lambda = 2$
When we solved $(A - 2I)x = 0$, we found the defining relationship was $x_2 = -2x_1$
- **The Eigenspace ($E_2$)**: This is the set of all vectors where the bottom number is negative two times the top number
$$E_2 = \left\{ \begin{pmatrix} c \\ -2c \end{pmatrix} \Big| c \in \mathbb{R} \right\}$$
- **The Basis**: We factor out the constant $c$ to isolate the core vector.
$$\text{Basis for } E_2 = \left\{ \begin{pmatrix} 1 \\ -2 \end{pmatrix} \right\}$$
- **Geometric Multiplicity**: Because our basis contains exactly $1$ vector, the **Geometric Multiplicity is 1**
---
## Similar Matrices & Eigendecomposition
### Matrix Similarity
#### Formal Definition:
- Square matrices $A$ and $B$ are called similar if there exists an invertible matrix $P$ such that $A = P^{-1}BP$
- Note that this also implies $B = Q^{-1}AQ$ where $Q = P^{-1}$
#### Simple Definition:
- Two matrices are "similar" if they represent the exact same linear transformation, but are just being viewed from different coordinate systems (bases)
- The matrix $P$ acts as the translator that shifts the perspective between these two coordinate systems
#### Key Properties of Similar Matrices
- **Identical Core Invariants:** Similar matrices share the exact same determinant, trace, rank, and nullity
- **Identical Eigen-properties**: They have the same characteristic polynomial, the same eigenvalues, and the same dimensions for their corresponding eigenspaces
- **Invertibility**: Matrix $A$ is invertible **iff** matrix $B$ is invertible
---
### Matrix Diagonalisation
#### Formal Definition:
- A square matrix $A$ is **diagonalisable** if it is **similar to a diagonal matrix**. In other words, if there exists an invertible matrix $P$ such that $P^{-1}AP = D$, where $D$ is a diagonal matrix
#### Simple Definition:
- You can simplify a complex matrix transformation into a diagonal matrix as long as the matrix has enough independent eigenvectors to form a complete basis for the space
#### Diagonal Matrix:
- A square matrix $D$ where all entries outside the main diagonal are exactly zero. Formally, $d_{ij} = 0$ for all $i \neq j$
$$D = \begin{pmatrix} \lambda_1 & 0 & 0 \\ 0 & \lambda_2 & 0 \\ 0 & 0 & \lambda_3 \end{pmatrix}$$
---
#### Matrix Diagonalisation Rules:
- **Theorem:** An $n \times n$ matrix is diagonalisable **iff** it has exactly $n$ linearly independent eigenvectors
- **Distinct Eigenvalues Shortcut:** If an $n \times n$ matrix has **$n$ distinct eigenvalues** (meaning the algebraic multiplicity is exactly 1 for all of them), it is guaranteed to have an **eigendecomposition** and be diagonalisable
- **Repeated Eigenvalues:** If a matrix has repeated eigenvalues, it is only diagonalisable if the [[#Geometric Multiplicity]] (number of **basis vectors** in the eigenspace) matches the [[#Algebraic Multiplicity]] for every **repeated eigenvalue**
---
### The Eigendecomposition Formula $A = PDP^{-1}$
#### Definition:
- The factorisation of a **diagonalisable matrix** $A$ into the product $A = PDP^{-1}$
- Where $P$ is an invertible matrix whose columns are the **eigenvectors** of $A$
- $D$ is a **diagonal matrix** whose diagonal entries are the corresponding **eigenvalues**
#### Geometric Interpretation of $A = PDP^{-1}$
Eigendecomposition can **break down** complex linear transformations into **three steps** by shifting our **basis vectors**:
1. **Change to Eigenbasis ($P^{-1}$):** The $P^{-1}$ matrix translates co-ordinates from the **standard basis** into the **eigenbasis** (A basis made from the matrix's own **eigenvectors**)
2. **Diagonal Scaling ($D$):** Now that we are aligned with the eigenvectors, the matrix $D$ applies a **scalar multiplication** to each new basis vector by its corresponding eigenvalue
3. **Return to Standard Basis ($P$):** The $P$ matrix maps the scaled co-ordinates back from the **eigenbasis** to the original **standard basis**
###### Diagram:
$$\begin{array}{|ccc|} \hline \mathbb{R}^n \text{ (Standard Basis)} & \xrightarrow{\text{Multiply by } A} & \mathbb{R}^n \text{ (Standard Basis)} \\ \big\downarrow \text{Multiply by } P^{-1} & & \big\uparrow \text{Multiply by } P \\ \mathbb{R}^n \text{ (Eigenbasis)} & \xrightarrow{\text{Multiply by } D \text{ (Scale)}} & \mathbb{R}^n \text{ (Eigenbasis)} \\ \hline  \end{array}$$
---
#### Creating Matrices $P$ and $D$
- **The $P$ Matrix (Eigenvectors)**: Formed by placing the $n$ linearly independent **eigenvectors** of $A$ side-by-side as column vectors
- **The $D$ Matrix (Eigenvalues)**: A diagonal matrix where the main diagonal entries are the **eigenvalues**. 
- **Note**: The order of the eigenvalues in $D$ **must exactly match** the column order of their corresponding eigenvectors in $P$
---
#### Benefits of Eigendecomposition
- **Problem:** Computing high powers of a matrix ($A^k$) through standard multiplication is incredibly computationally expensive
- **Solution:** Because $A = PDP^{-1}$, calculating $A^k$ collapses all the adjacent $P^{-1}P$ pairs into the identity matrix, streamlining the formula to **$A^k = PD^kP^{-1}$
- **Benefit**: Raising a diagonal matrix $D$ to a power $k$ is really fast, you just **raise each individual diagonal element to the power of $k$**
- **Real-World Use:** Used to simplify data visualisation with Principal Component Analysis (PCA) in **machine learning** and Markov Chains for probability
---
#### Example: Finding an Eigendecomposition
**Question:** Calculate the eigendecomposition of matrix $A$:
$$A = \begin{pmatrix} -2 & 0 & 3 \\ -8 & 2 & 8 \\ 0 & 0 & 1 \end{pmatrix}$$
#### Step 1: Find the Eigenvalues ($\lambda$)
By solving the characteristic equation $\det(A - \lambda I) = 0$, we find the three roots:
$$\lambda_1 = -2, \quad \lambda_2 = 2, \quad \lambda_3 = 1$$
#### Step 2: Find the Eigenvectors ($v$)
Solving $(A - \lambda I)x = 0$ for each eigenvalue to get their respective eigenvectors:
$$v_1 = \begin{pmatrix} 1 \\ 2 \\ 0 \end{pmatrix}, \quad v_2 = \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}, \quad v_3 = \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}$$
#### Step 3: Construct the $P$ and $D$ Matrices
Place the **eigenvectors** as columns to form **$P$**, and place the corresponding **eigenvalues** on the diagonal to form **$D$**:
$$P = \begin{pmatrix} 1 & 0 & 1 \\ 2 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix}, \quad D = \begin{pmatrix} -2 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 1 \end{pmatrix}$$
#### Step 4: Find the Inverse Matrix ($P^{-1}$)
Calculate the inverse of $P$ using standard matrix inversion techniques:
$$P^{-1} = \begin{pmatrix} 1 & 0 & -1 \\ -2 & 1 & 2 \\ 0 & 0 & 1 \end{pmatrix}$$
#### Step 5: Write the Final Decomposition
Substitute all three matrices back into the core formula $A = PDP^{-1}$:
$$\begin{pmatrix} -2 & 0 & 3 \\ -8 & 2 & 8 \\ 0 & 0 & 1 \end{pmatrix} = \begin{pmatrix} 1 & 0 & 1 \\ 2 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} -2 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} 1 & 0 & -1 \\ -2 & 1 & 2 \\ 0 & 0 & 1 \end{pmatrix}$$
---
## Spectral Decomposition
### Symmetric Matrices
#### Formal Definition
- A square matrix $A$ is **symmetric** if it is equal to its own transpose ($A = A^T$). This means the entries are mirrored across the main diagonal ($a_{ij} = a_{ji}$)
#### Core Properties of Symmetric Matrices
- **Real Eigenvalues**: All eigenvalues of a symmetric matrix are **purely real numbers**, even if the characteristic polynomial could theoretically have complex roots
- **Orthogonal Eigenspaces**: Eigenvectors belonging to **different eigenvalues** are automatically **orthogonal** to each other
- **Orthogonal Diagonalisability**: A matrix is orthogonally diagonalisable **iff** it is symmetric
----
#### Orthogonal Matrices
- **Definition:** A square matrix $Q$ is **orthogonal** if $Q^T = Q^{-1}$ (Transpose $=$ Inverse), which is mathematically equivalent to $Q^T Q = I$
- **Orthonormal Basis Property:** A square matrix $Q$ is orthogonal **iff** its **column vectors** form an **orthonormal basis** in $\mathbb{R}^n$ (the same also applies to its rows)
###### Core Properties:
- **Determinant**: The determinant of an orthogonal matrix is always **$\pm 1$**.
- **Inverse/Transpose**: Both $Q^T$ and $Q^{-1}$ are also orthogonal
- **Products**: The product of any two orthogonal matrices is always orthogonal
---
### Orthogonal Diagonalisability
#### Definitions:
- **Orthogonal Diagonalisability:** Where matrix $P$ from the eigendecomposition formula ($A = PDP^{-1}$) is an **Orthonormal Eigenbasis**
- **Orthonormal Eigenbasis:** A basis made of **eigenvectors** that are both **mutually perpendicular** (orthogonal) and are **normalised** (magnitude of one)
#### Geometric Preservation
Unlike standard diagonalisation, which can "warp" the fabric of your coordinate system, orthogonal diagonalisation maintains the **geometric properties** of the space:
- **Rigid Transformations:** The **orthogonal matrix** $Q$ (where $Q^T = Q^{-1}$), acts as a rigid **rotation or reflection**
- **Same Length:** It preserves the **norm** ($||Qx|| = ||x||$), so the lengths of vectors stay the same during the change of basis
- **Same Angles**: It preserves the **inner product** ($\langle Qx, Qy \rangle = \langle x, y \rangle$), meaning the angles between vectors remain identical after the transformation is applied
#### Standard vs Orthogonal Diagonalisation
##### The "Warped" Standard Basis
- In general diagonalisation ($A = PDP^{-1}$), eigenvectors can point in any direction as long as they are independent
- This often results in a **distorted coordinate system** where the grid lines aren't perpendicular
##### The "Rigid" Orthogonal Basis
- In orthogonal diagonalisation ($A = QDQ^T$), the matrix $Q$ consists of an **orthonormal set** of eigenvectors. 
- This maintains a **perfectly square grid**, merely rotating the entire system to align with the matrix's natural axes
---
### The Spectral Theorem
#### Spectral Theorem
For any $n \times n$ matrix $A$, the three statements are **either all True or all False**:
1. $A$ is **orthogonally diagonalisable** (i.e., $A = QDQ^T$)
2. $A$ has an **orthonormal set** of $n$ eigenvectors
3. $A$ is **symmetric**
#### Proof of the Spectral Theorem
##### 1. Equivalence of Diagonalisation and Eigenvectors ($1 \Longleftrightarrow 2$)
- **Forward ($1 \Longrightarrow 2$):** If $A$ is diagonalisable, then $A = QDQ^T$. By definition, the columns of $Q$ are the eigenvectors of $A$. Since $Q$  

##### 2. Proof that Orthogonal Diagonalisation implies Symmetry ($1 \implies 3$)



##### 3. Logic for Symmetry implying Orthogonal Diagonalisability ($3 \implies 1$)


#### Orthogonal Similarity
- Two matrices $A$ and $B$ are **orthogonally similar** if there exists an **orthogonal matrix** $Q$ such that $Q^T A Q = B$
#### Algorithm: Orthogonally Diagonalising a Symmetric Matrix
Assuming matrix $A$ is symmetric, follow these steps to factorise it into $QDQ^T$:


---
#linear-algebra/theory #linear-algebra/eigenvalues #linear-algebra/diagonalisation #linear-algebra/spectral-theory

