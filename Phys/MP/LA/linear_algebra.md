# Linear Algebra

![Matrix](https://i.imgur.com/Tn046ii.png)


### Brief Questions (and proofs)

- If $Ax = \lambda x$ and $\lambda \neq 0$, then $x$ is an eigenvector of $A^{-1}$.
- $A$ and $A^T$ share the same eigenvalues.

- Suppose $A$ is an $n \times n$ matrix with $n$ linearly independent eigenvectors. Let the matrix $S$ consist of these eigenvectors as its columns. For a diagonal matrix $\Lambda$ defined as $(\Lambda)_{ij} = 0 \; (i \neq j)$, it holds that $S^{-1} A S = \Lambda$. (Proof: compute $AS = S\Lambda$)

- Does $S$ have an inverse? > Yes.  
  If $\vec{x_i}$ are linearly independent, the equation $S\vec{c} = 0$ implies that $c_1 = \cdots = c_n = 0$. When $S$ is converted to echelon form, if $\text{rank}(S) \neq n$, then a non-zero solution for $c$ exists. Therefore, $\text{rank}(S) = n$, which implies $|S| \neq 0$, and hence $S^{-1}$ exists.

- Does $\text{rank}(S) = n$ imply $\text{det}(S) \neq 0 $? > Yes.   
One of the key properties of determinants: $\text{det}(A) = \sum a_{i1}A_{i1} = \sum a_{1j}A_{1j}$. This shows that the determinant value is invariant under expansion by rows or columns, and $\text{det}(A) = \text{det}(A^T)$.  
  For an $n \times n$ matrix with $\text{rank} = n$, the echelon form $U$ satisfies $\text{det}(U) = p_1p_2 \cdots p_n$, where $p_i \neq 0$, so $\text{det}(U) \neq 0$. To prove the equivalence of $\text{det}(S) \neq 0$ and $\text{det}(U) \neq 0$:
  Echelon form is achieved through row operations. Hence, $\text{det}(S) \neq 0$ if and only if $\text{det}(U) \neq 0$.

- If $B$ is obtained by swapping two rows of an $n \times n$ matrix $A$, then $\text{det}(B) = -\text{det}(A)$.
- If the nonzero eigenvectors $\vec{x_1}, \vec{x_2}, \dots, \vec{x_k}$ correspond to distinct eigenvalues $\lambda_1, \lambda_2, \dots, \lambda_k$, then these eigenvectors are linearly independent.

- Do all $n \times n$ matrices have eigenvectors and eigenvalues?
  - This question is ambiguous:
    - Do all have distinct eigenvalues?  > No, but it is possible.
    - When do they have distinct eigenvalues? > If they have linearly independent and distinct eigenvectors.

- If $\text{det}(A - \lambda I) = 0$, does there always exist an eigenvector $x (\neq 0)$ satisfying $Ax = \lambda x$?
  - For $\text{rank} = 1$, $x$ lies on a line through the origin, so $x \neq 0$ exists.  
  - For $\text{rank} = 2$, $x$ lies on a plane through the origin, so $x \neq 0$ exists.  
  - What about $\text{rank} > 3$?  

- A Hermitian matrix always has linearly independent eigenvectors, even for repeated eigenvalues. Can a Hermitian matrix with repeated eigenvalues have two independent eigenvectors? > Possible.

- For Hermitian $A$, if $A = U \Lambda U^\dagger$ and $B = UAU^{-1}$, are the determinants of $A$ and $B$ equal? > Yes:  
$\text{det}(B - \lambda I) = \text{det}(U(A - \lambda I)U^\dagger) = \text{det}(A - \lambda I)$

- Is a Hermitian matrix $S$ always orthogonal? > No, but possible if it is real.  
Becasue we arbitrarily set the eigenvectors orthognal, so $S^T=S^{-1}$. If including complex number, $S^\dagger S=\mathbb{1}$ (unitary). $A^H=S\lambda S^{-1}=U\Lambda U^\dagger$: spectral theorem

- $H^\dagger =H$. Are there always two independent $\ket{x}$ satisfying $H \ket{x}=\lambda\ket{x}$? > no

- Are $AB$'s eigenvalues the product of eigenvalues of $A$ and $B$? > No.  
  Example: $\sigma_x \sigma_y = i\sigma_z$. It holds when $AB = BA$ (commutative).

- If $A$ and $B$ are Hermitian and $AB = BA$, do they share eigenvectors? > Not necessarily.
  - For $B\vec{x}$ to be an eigenvector of $A$, does $\text{rank} = 1$ suffice?  
  - If $Ax = \lambda x$ and $\lambda$ is a simple eigenvalue, is $x = cx'$?

- If eigenvalues are not distinct, can eigenvectors for repeated eigenvalues form a linearly independent set? > Use geometric reasoning. (How?)