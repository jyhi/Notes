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
