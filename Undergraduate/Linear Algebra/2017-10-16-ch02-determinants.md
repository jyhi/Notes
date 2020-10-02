# Chapter 2: Determinants

## 2.1 The Determinant of a Matrix

**det(A)** or **|A|** is a scalar, telling us whether A is singular or nonsingular.

### 1 * 1 Matrices

**A = [a]**, then **A** will have a multiplicative inverse **[1/a]** if and only if **a ≠ 0**. Thus, if we define **det(A) = a**, then **A** will be nonsingular _if and only if_ **det(A) ≠ 0**.

### 2 * 2 Matrices

Let ![2 * 2 Matrices](https://latex.codecogs.com/svg.latex?A=\begin{bmatrix}a_{11}&&a_{12}\\a_{21}&&a_{22}\end{bmatrix}), A will be nonsingular if and only if it is row equivalent to I.

### **Definition**

The determinant of a 2 x 2 matrix A is denoted **|A|** and is given by

![Determinant Definition](https://latex.codecogs.com/svg.latex?\begin{vmatrix}a_{11}&&a_{12}\\a_{21}&&a_{22}\end{vmatrix}=a_{11}a_{22}-a_{12}a_{21})

Observe that the determinant of a 2 x 2 matrix is given by the difference of the products of the two diagonals of the matrix.
The notation **det(A)** is also used for the determinant of A.

...

## 2.2 Properties of Determinants

- det(A^T) = det(A)
- If A has a row (column) of all 0, det(A) = 0
- If any 2 rows (columns) of A are equal, det(A) = 0 **(since A is singular)**

If an `n * n` matrix A = [a_{ij}] is upper triangular or lower triangular or diagonal, **det(A) = a11a22 ... ann (the product of the main diagonal elements)**

**det(AB) = det(A) det(B)**. Proof in book.

If A is nonsingular, then **det(A) ≠ 0** and ![](https://latex.codecogs.com/svg.latex?det[A^{-1}]=\frac{1}{det[A]})

![](https://latex.codecogs.com/svg.latex?det[kA]=k^ndet[A]) (**k** is row number)

### Row Operation I

Two rows of A are interchanged, then

![](https://latex.codecogs.com/svg.latex?det[E_{ij}]A=-det[A]) <!-- [] To Bypass Atom Link Breakage -->

where E_{ij} is the elementary matrix that swaps rows i and j.

### Row Operation II

A row of A is multiplied by a nonzero constant. (**Constant \* det(A)**)

![](https://latex.codecogs.com/svg.latex?det[EA]=\mathbf{a}det[A]) <!-- [] To Bypass Atom Link Breakage -->

### Row Operation III

A multiple of one row is added to another row. (**det(A) Not Changed**)

![](https://latex.codecogs.com/svg.latex?det[EA]=det[A]) <!-- [] To Bypass Atom Link Breakage -->
