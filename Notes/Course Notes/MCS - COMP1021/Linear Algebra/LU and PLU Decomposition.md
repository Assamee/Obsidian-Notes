# LU Decomposition
- A factorisation of a square matrix $A$ into the product $A=LU$, where $L$ is a lower triangular matrix and $U$ is an upper triangular matrix
- **Usage:** Makes it easier to solve linear systems (Used in `NumPy`)
```Plaintext
    [A]     =    [L]      *     [U]
Square Matrix   Lower Triangle   Upper Triangle
 [ * * * ]    [ * 0 0 ]      [ * * * ]
 [ * * * ]  = [ * * 0 ]   *  [ 0 * * ]
 [ * * * ]    [ * * * ]      [ 0 0 * ]
```
---
### Algorithm: Solving Linear Systems using LU Decomposition#
If you need to solve a system of equations in the form $Ax=b$, and you already know the decomposition $A=LU$:
1. **Substitute the decomposition**: Re-write the original equation $Ax=b$ as $LUx=b$
2. **Create an intermediate variable**: Define a new vector $y$ such that $Ux=y$
3. **Solve the first triangular system**: Substitute $y$ into your first equation to get $Ly=b$. Solve this lower triangular system for $y$ using forward substitution
4. **Solve the second triangular system**: Now that you have the vector $y$, return to $Ux=y$. Solve this upper triangular system for $x$ using backward substitution to get your final answer
---
## Example: Using LU Decomposition
- **Question:** Solve this linear system in the form $Ax=b$:
$$\begin{pmatrix}2&6&2\\ -3&-8&0\\ 4&9&2\end{pmatrix} \begin{pmatrix}x_1\\ x_2\\ x_3\end{pmatrix} = \begin{pmatrix}2\\ 2\\ 3\end{pmatrix}$$
- We are given the LU decomposition of matrix $A$:
$$L = \begin{pmatrix}2&0&0\\ -3&1&0\\ 4&-3&7\end{pmatrix}, \quad U = \begin{pmatrix}1&3&1\\ 0&1&3\\ 0&0&1\end{pmatrix}$$
### Step 1 & 2: Set up $Ly = b$
Instead of solving $Ax=b$ directly, we substitute $A$ with $LU$, giving us $LUx=b$. We then let $y = Ux$, which allows us to first solve the lower triangular system $Ly = b$:
$$\begin{pmatrix}2&0&0\\ -3&1&0\\ 4&-3&7\end{pmatrix} \begin{pmatrix}y_1\\ y_2\\ y_3\end{pmatrix} = \begin{pmatrix}2\\ 2\\ 3\end{pmatrix}$$
Written out as a system of equations, this is:
$$\begin{array}{rll} 2y_1 &= 2 \\ -3y_1 + y_2 &= 2 \\ 4y_1 - 3y_2 + 7y_3 &= 3 \end{array}$$
### Step 3: Forward Substitution
Because $L$ is lower triangular, we can easily solve this from top to bottom:
From the first equation, we can see immediately:
$$y_1 = 1$$
Substitute $y_1$ into the second equation:
$$-3(1) + y_2 = 2 \implies y_2 = 5$$
Substitute $y_1$ and $y_2$ into the third equation:
$$4(1) - 3(5) + 7y_3 = 3 \implies -11 + 7y_3 = 3 \implies 7y_3 = 14 \implies y_3 = 2$$
So, our intermediate vector $y$ is:
$$y = \begin{pmatrix}1\\ 5\\ 2\end{pmatrix}$$
### Step 4: Set up and solve $Ux = y$ (Backward Substitution)
Now we return to our substitution $Ux = y$ and solve for our final answer, $x$:
$$\begin{pmatrix}1&3&1\\ 0&1&3\\ 0&0&1\end{pmatrix} \begin{pmatrix}x_1\\ x_2\\ x_3\end{pmatrix} = \begin{pmatrix}1\\ 5\\ 2\end{pmatrix}$$
Written out as equations, this gives us an upper triangular system:
$$\begin{array}{rll} x_1 + 3x_2 + x_3 &= 1 \\ x_2 + 3x_3 &= 5 \\ x_3 &= 2 \end{array}$$
Because it is upper triangular, we solve from bottom to top (backward substitution):
From the third equation, we instantly have:
$$x_3 = 2$$
Substitute $x_3$ into the second equation:
$$x_2 + 3(2) = 5 \implies x_2 = -1$$
Substitute $x_2$ and $x_3$ into the first equation:
$$x_1 + 3(-1) + 2 = 1 \implies x_1 - 1 = 1 \implies x_1 = 2$$
### Final Answer
We have successfully found the components of vector $x$:
$$x = \begin{pmatrix}2\\ -1\\ 2\end{pmatrix}$$
---
# Calculating LU Decomposition
### Conditions for using LU Decomposition
- If a square matrix $A$ can be reduced to its row echelon form $U$ via Gaussian elimination without any row exchanges, then $A$ can be factored into $A=LU$, where $L$ is lower triangular
### Algorithm: Finding $L$ and $U$
$U$ is found with _**Gaussian Elimination**_ and $L$ is found by tracking the row operations used to find $U$. Every valid row operations corresponds to multiplying by an **"Elementary Matrix"** $(E)$
1. **Setup:** Start with matrix $A$ (which will become $U$) and an identity matrix $I$ (which will become $L$) of the same size
2. **Pivots (The Diagonal)**: When you perform a row operation to create a leading $1$ (a pivot) in $A$ by dividing the row by a scalar, place that exact scalar directly into the corresponding diagonal position in your $L$ matrix
3. **Clear Columns:** When you subtract a multiple of a pivot row from a row below it to create a $0$ in $A$, take that specific multiplier and place it into the corresponding diagonal position in your $L$ matrix
4. **Finish the Elimination:** Repeat this process until $A$ reaches upper triangular form (this is now $U$). The modified Identity matrix is now the lower triangular matrix $L$
---
## Example: Finding the LU Decomposition
**Question:** Find the LU decomposition of $A = \begin{pmatrix} 2 & -4 \\ 3 & -2 \end{pmatrix}$
### Setup
Set up matrix $A$ and the Identity matrix side-by-side:
$$A = \begin{pmatrix} 2 & -4 \\ 3 & -2 \end{pmatrix}, \quad L = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$$
### Step 1: Create the first pivot
- **For $U$**: Divide Row 1 by $2$ to get a $1$ in the top-left
- **For $L$**: Place that scalar ($2$) into the top-left diagonal position $(1,1)$
$$A \rightarrow \begin{pmatrix} 1 & -2 \\ 3 & -2 \end{pmatrix}, \quad L \rightarrow \begin{pmatrix} 2 & 0 \\ 0 & 1 \end{pmatrix}$$
### Step 2: Clear the column below the pivot
- **For $U$**: Subtract $3 \times$ (Row 1) from Row 2 to clear the bottom-left entry
- **For $L$**: Take that multiplier ($3$) and place it in the bottom-left position $(2,1)$
$$A \rightarrow \begin{pmatrix} 1 & -2 \\ 0 & 4 \end{pmatrix}, \quad L \rightarrow \begin{pmatrix} 2 & 0 \\ 3 & 1 \end{pmatrix}$$
### Step 3: Create the second pivot
- **For $U$**: Divide Row 2 by $4$ to get a $1$ in the bottom-right. $A$ is now fully upper-triangular, so this is $U$
- **For $L$**: Place that scalar ($4$) into the bottom-right diagonal position $(2,2)$. The Identity matrix is now fully populated, so this is $L$
$$U = \begin{pmatrix} 1 & -2 \\ 0 & 1 \end{pmatrix}, \quad L = \begin{pmatrix} 2 & 0 \\ 3 & 4 \end{pmatrix}$$
---
# Permutation Matrices & PLU Decomposition
- **Issue:** Standard LU Decomposition fails if we ever have to perform a row exchange (swapping rows) to avoid a $0$ in a pivot position
- **Solution:** We can permute (swap) the rows of our equations in advance to avoid these zeros, this method is called PLU Decomposition
### Permutation Matrix $(P)$
- A square matrix $P$ obtained from the identity matrix $I$ by permuting (swapping) its rows
- **Property:** $P$ is always invertible, and its inverse is simply its transpose: $P^{-1} = P^T$ (which is also a permutation matrix)
---
## PLU Decomposition
- A representation of a square matrix $A$ in the form $A = PLU$, where $P$ is a permutation matrix, $L$ is lower triangular, and $U$ is upper triangular
- Every square matrix has a PLU-decomposition
###### Logic:
- We record the necessary row swaps in matrix $P$. Because $P^{-1} = P^T$, the equation $A = PLU$ is mathematically equivalent to $P^T A = LU$
- This means if we shuffle the rows of $A$ using $P^T$ first, we can perform a standard LU decomposition on the result
### Algorithm: Solving Linear Systems using PLU Decomposition
If you need to solve $Ax = b$ and you are given the PLU decomposition $A = PLU$:
1. **Transform the constant vector:** Because $A = PLU$ is equivalent to $P^T A = LU$, the system $Ax = b$ has the exact same solutions as $P^T Ax = P^T b$. 
	- First, compute a new vector $b'$ by multiplying $P^T$ by $b$ ($b' = P^T b$)
2. **Set up the LU system**: Substitute $b'$ into the equation to get a standard LU system: $LUx = b'$
3. **Solve like Standard LU**: Just like standard LU, denote $Ux = y$. Solve $Ly = b'$ for $y$ using forward substitution, and then solve $Ux = y$ for $x$ using backward substitution
---
## Example: Solving Linear Systems using PLU Decomposition
**Question:** Solve the linear system $Ax = b$:
$$\begin{pmatrix} 0 & 1 & 1 \\ 1 & 2 & 1 \\ 2 & 7 & 9 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} 5 \\ 8 \\ 43 \end{pmatrix}$$
You are given the PLU decomposition for matrix $A$:
$$P = \begin{pmatrix} 0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1 \end{pmatrix}, \quad L = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 2 & 3 & 1 \end{pmatrix}, \quad U = \begin{pmatrix} 1 & 2 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 4 \end{pmatrix}$$
_(Note: Matrix $P$ tells us that rows 1 and 2 had to be swapped to avoid a zero pivot)_
### Step 1: Transform the Constant Vector ($b'$)
Because we swapped the rows of $A$, we must swap the rows of $b$ to match. We do this by computing a new vector $b' = P^T b$.

For this specific permutation matrix, its transpose ($P^T$) is identical to $P$:
$$b' = \begin{pmatrix} 0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} 5 \\ 8 \\ 43 \end{pmatrix} = \begin{pmatrix} 8 \\ 5 \\ 43 \end{pmatrix}$$
(Notice how the $5$ and $8$ simply swapped places)
### Step 2: Solve $Ly = b'$ (Forward Substitution)
Now we write out our lower triangular system using our new $b'$ vector:
$$\begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 2 & 3 & 1 \end{pmatrix} \begin{pmatrix} y_1 \\ y_2 \\ y_3 \end{pmatrix} = \begin{pmatrix} 8 \\ 5 \\ 43 \end{pmatrix}$$
We solve from top to bottom:
- From row 1: $y_1 = 8$
- From row 2: $y_2 = 5$
- Substitute into row 3: $2(8) + 3(5) + y_3 = 43 \implies 16 + 15 + y_3 = 43 \implies y_3 = 12$
Our intermediate vector is $y = \begin{pmatrix} 8 \\ 5 \\ 12 \end{pmatrix}$
### Step 3: Solve $Ux = y$ (Backward Substitution)
Finally, we set up our upper triangular system:
$$\begin{pmatrix} 1 & 2 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 4 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} 8 \\ 5 \\ 12 \end{pmatrix}$$
We solve from bottom to top:
- From row 3: $4x_3 = 12 \implies x_3 = 3$
- Substitute into row 2: $x_2 + 3 = 5 \implies x_2 = 2$
- Substitute into row 1: $x_1 + 2(2) + 3 = 8 \implies x_1 + 7 = 8 \implies x_1 = 1$
### Final Answer
$$x = \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix}$$
---
$\underline{\textbf{Related Pages: }}$
- [[Eigenvalues & Eigenvectors]]