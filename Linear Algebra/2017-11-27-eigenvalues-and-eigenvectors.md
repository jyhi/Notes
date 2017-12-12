# Chapter 6: Eigenvalues and Eigenvectors

## 6.3 Diagonalization

### Theorem

![](./img/eigenv-diagnoalization-theorem-1.png)

### Diagonalization

![](./img/eigenv-diagnoalization-diagnoalizable.png)

![](./img/eigenv-diagnoalization-theorem-2.png)

=> ![Example](https://latex.codecogs.com/svg.latex?\begin{bmatrix}a-\lambda&&&&\\&&b-\lambda&&\\&&&&c-\lambda\end{bmatrix})

### Notations

- Diagonal Matrix: ![D](https://latex.codecogs.com/svg.latex?D=\begin{bmatrix}\lambda_1&&&&\\&&\lambda_2&&\\&&&&\lambda_3\end{bmatrix})
- P: ![P](https://latex.codecogs.com/svg.latex?[\mathbf{x}_1|\mathbf{x}_2|\mathbf{x}_3]) (where **x** are eigenvectors respectively)

### Orthogonally Diagonalizable

![](./img/eigenv-diagonalization-orthogonally-diagonalizable.png)

![](./img/eigenv-diagnoalization-symmetrix-orthogonal-eigenv.png)

## 6.5 The Singular Value Decomposition

### Motivation

- Compute `rank()` without Gauss-Jordan Elimination (not practical in finite-precision arithmetic)

### The Singular Value Decomposition

- Assume that **A** is an m × n matrix with m ≥ n.
- Factorize **A** into a product where **U** is an _m × m_ orthogonal matrix, **V** is an _n × n_ orthogonal matrix, and **E (_Sigma_)** is an _m × n_ matrix whose off-diagonal entries are all 0s and whose diagonal elements satisfy:

![](./img/eigenv-singular-value-decomposition.png)

where _delta\_i_ are unique.

### Theorem

If **A** is an m × n matrix, then **A** has a singular value decomposition.
