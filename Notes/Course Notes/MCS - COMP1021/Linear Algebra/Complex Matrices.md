# Types of Complex Matrices
### Conjugate Matrix $(\overline{A})$
- A matrix obtained by replacing every element $a_{ij}$ of a complex matrix $A$ with its complex conjugate $\overline{a}_{ij}$  (e.g. $3 + 2i$ becomes $3 - 2i$)
### Conjugate Transpose $(A^* \text{ or }A^H)$
- The transpose of the conjugate of a complex matrix, mathematically defined as $A^* = (\overline{A})^T$
### Hermitian Matrix
- A square complex matrix $A$ that is equal to its own conjugate transpose, such that $A = A^*$
- This is the complex equivalent of a symmetric matrix (reflects across the main diagonal). If you reflect the entries across the main diagonal, they must be complex conjugates of each other
_(Note: This forces the main diagonal to consist entirely of real numbers)_
##### Key Properties:
1. **Real Eigenvalues**: The eigenvalues of a Hermitian matrix are always purely real numbers (the imaginary part is zero)
2. **Orthogonal Eigenvectors**: The eigenvectors corresponding to different eigenvalues are perfectly orthogonal to each other
### Skew-Hermitian Matrix
- A square complex matrix $A$ where its conjugate transpose is equal to its negative, such that $A^* = -A$
### Unitary Matrix  $(U)$
- A square complex matrix $U$ whose conjugate transpose is also its inverse, such that $U^* U = UU^* = I$
---
## Properties of Complex Dot Products
#### Conjugate Symmetry
- The dot product of two complex vectors is the complex conjugate of their reversed dot product: $u \cdot v = \overline{v \cdot u}$
- Unlike real vectors where $u \cdot v = v \cdot u$, swapping the order of complex vectors changes the sign of the imaginary part
#### Linearity (First Argument)
- The dot product is linear with respect to vector addition and scalar multiplication in its first argument: $(u + w) \cdot v = u \cdot v + w \cdot v$ and $(cu) \cdot v = c(u \cdot v)$
#### Anti-Linearity (Second Argument)
- Pulling a complex scalar $c$ out of the second vector results in its complex conjugate: $u \cdot (cv) = \overline{c}(u \cdot v)$
- If you multiply the _second_ vector by a scalar like $3i$, it becomes $-3i$ when you pull it out to the front of the dot product
### Positive Definitiveness
- The dot product of any complex vector with itself is always a real, non-negative scalar: $v \cdot v \ge 0$. Furthermore, $v \cdot v = 0$ if and only if $v = \mathbf{0}$
---
### Euclidean Norm $(||v||)$
- The magnitude of a vector: $||v|| = \sqrt{v \cdot v} = \sqrt{|v_1|^2 + \dots + |v_n|^2}$
---
$\underline{\textbf{Related Pages: }}$
- [[LU and PLU Decomposition]]
- [[Eigenvalues & Eigenvectors]]
- [[Similar Matrices & Eigendecomposition]]