### Eigenvector $(x)$
- A non-zero vector $x$ such that when a given square matrix $A$ is applied to it, the resulting vector is a scalar multiple of $x$ (like invariant lines)
### Eigenvalues $(\lambda)$
- The scalar $\lambda$ associated with an eigenvector $x$ such that the equation $Ax = \lambda x$ holds true. It tells you **_how much_** the eigenvector gets stretched or squashed (e.g. if $\lambda = 2$, the vector doubles in length)
---
### The Core Equation
The relationship between a matrix $A$, its eigenvector $x$, and its eigenvalue $\lambda$ is defined by:
$$Ax = \lambda x$$
### Algorithm: Finding Eigenvalues & Eigenvectors
To find eigenvalues and eigenvectors we use the characteristic equation:
1. **Set up the Characteristic Equation**: Rearrange $Ax = \lambda x$ to $(A - \lambda I)x = 0$ (where $I$ is the identity matrix). For $x$ to be a non-zero vector, the matrix $(A - \lambda I)$ must not be invertible. Therefore, its determinant must be zero:
$$\det(A - \lambda I) = 0$$
2. **Solve for the Eigenvalues ($\lambda$)**: Compute the determinant of $(A - \lambda I)$. This will give you a polynomial equation (the characteristic polynomial). The eigenvalues are the roots of the polynomial
3. **Substitute $\lambda$ back in**: Take your first eigenvalue and substitute it into the matrix $(A - \lambda I)$
4. **Solve for the Eigenvector ($x$)**: Solve the resulting homogeneous linear system $(A - \lambda I)x = 0$ (usually via Gaussian elimination) to find the components of the vector $x$
5. **Repeat**: Repeat steps 3 and 4 for every eigenvalue you found to get all corresponding eigenvectors
---
## Example: Finding Eigenvalues & Eigenvectors
**Question:** Find the eigenvalues and eigenvectors for the matrix $A$:
$$A = \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix}$$
### Step 1: Set up the Characteristic Equation
We need to find the determinant of $(A - \lambda I)$ and set it to zero. First, we subtract $\lambda$ from the main diagonal of $A$:
$$A - \lambda I = \begin{pmatrix} 4 - \lambda & 1 \\ 2 & 3 - \lambda \end{pmatrix}$$
Now, we calculate the determinant of this new matrix:
$$\det(A - \lambda I) = (4 - \lambda)(3 - \lambda) - (1)(2) = 0$$
### Step 2: Solve for the Eigenvalues ($\lambda$)
Expand the brackets and simplify to find the characteristic polynomial:
$$\begin{array}{rll} (12 - 4\lambda - 3\lambda + \lambda^2) - 2 &= 0 \\ \lambda^2 - 7\lambda + 10 &= 0 \end{array}$$
Factorise the quadratic equation to find the roots (our eigenvalues):
$$(\lambda - 5)(\lambda - 2) = 0$$
So, our two eigenvalues are **$\lambda_1 = 5$** and **$\lambda_2 = 2$**
### Step 3 & 4: Substitute $\lambda_1 = 5$ and Solve for its Eigenvector
Substitute $\lambda = 5$ back into our $(A - \lambda I)$ matrix:
$$\begin{pmatrix} 4 - 5 & 1 \\ 2 & 3 - 5 \end{pmatrix} = \begin{pmatrix} -1 & 1 \\ 2 & -2 \end{pmatrix}$$
Set up the homogeneous system $(A - \lambda I)x = 0$:
$$\begin{pmatrix} -1 & 1 \\ 2 & -2 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$
This gives us two equations, but they are multiples of each other (which is exactly what should happen!):
$$-x_1 + x_2 = 0 \implies x_1 = x_2$$
To find an eigenvector, we just pick a simple, non-zero value that satisfies this rule. Let $x_1 = 1$. Then $x_2 = 1$
###### Eigenvector 1:
$$v_1 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$$
### Step 5: Repeat for $\lambda_2 = 2$
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
## Eigenspaces & Multiplicity
### Eigenspace **$(E_{\lambda})$
- The set of all eigenvectors corresponding to a specific eigenvalue $\lambda_0$, together with the zero vector. It is the null space (or kernel) of the matrix $(A - \lambda I)$
- If an eigenvalue is the "stretch factor", the eigenspace is the entire line, plane, or 3D space of all possible vectors that get stretched by that exact amount
#### Basis for an Eigenspace
- A set of linearly independent eigenvectors that spans the eigenspace $E_{\lambda}$
#### Algebraic Multiplicity
- The number of times a specific eigenvalue $\lambda$ appears as a repeated root of the characteristic polynomial
#### Geometric Multiplicity
- The dimension of the eigenspace $E_{\lambda}$. This is equal to the number of linearly independent basis vectors that span $E_{\lambda}$
---
## Example: Finding the Eigenspace & Multiplicity
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
$\underline{\textbf{Related Pages: }}$
- [[LU and PLU Decomposition]]
- [[Similar Matrices & Eigendecomposition]]
- [[Complex Matrices]]