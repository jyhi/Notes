# Chapter 1: Matrices and Systems of Equations

## 1.1 Systems of Linear Equations

### Linear Equation

A linear equation in n unknowns x1, x2, x3, …, xn has the form

![Linear Equation](https://latex.codecogs.com/svg.latex?a_1x_1+a_2x_2+a_3x_3+...+a_nx_n=b)

where the coefficients a1, a2, a3, …, an and b are real numbers.

### Linear System

### Solutions

- A **solution** of an `m x n` system is an ordered n-tuple of numbers `x1, x2, x3, ..., xn` that satisfies all the equations of the system.
  - An **inconsistent** linear system has _no_ solution;
  - A **consistent** system has _at least one_ solution.
- **The solution set** - the set of all solutions of a linear system.
- **Equivalent systems** - two linear systems with the same solution set.

A linear equation in _three variables_ corresponds to **a plane** in three-dimensional (3D) space.

### N-space: N dimensional Space

The set of all n-vector with real entries is called Euclidean n-space and is denoted as ![N-D Space](https://latex.codecogs.com/svg.latex?R^n)

### Matrices

- A **matrix** is a rectangular array of numbers.
- The numbers in the array are called the **elements** of the matrix.

#### Identity Matrices

Diagonal=1, others are 0, subscript is the size.

![Identity Matrices](https://latex.codecogs.com/svg.latex?I_3=\begin{bmatrix}1&&0&&0\\0&&1&&1\\0&&0&&1\end{bmatrix})

### Linear Combination

### Consistency Theorem

A linear system `Ax = b` is **consistent** (has at least one vector solution x) if and only if `b` can be written as a linear combination of the column vectors of `A`.

### Augmented Matrix (增广矩阵)

Given:

![Matrix Ex](https://latex.codecogs.com/svg.latex?\begin{bmatrix}1&&1&&1\\2&&3&&1\\1&&-1&&-2\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}2\\3\\-6\end{bmatrix})

- Coefficient Matrix: ![Coefficient Matrix](https://latex.codecogs.com/svg.latex?\begin{bmatrix}1&&1&&1\\2&&3&&1\\1&&-1&&-2\end{bmatrix})
- Augmented Matrix:
![Augmented Matrix](https://latex.codecogs.com/svg.latex?\begin{bmatrix}1&&1&&1&&2\\2&&3&&1&&3\\1&&-1&&-2&&-6\end{bmatrix})

### Solving A System of Linear Equations

Strategy: Replace one system with an **equivalent system** that is easier to solve.

Three operations used to obtain equivalent systems:

- **Elementary Row Operations**:
  - Interchange two rows.
  - Multiply a row by a nonzero real number.
  - Replace a row by its sum with a multiple of another row.
- **Row equivalent matrices**: Two matrices where one matrix can be transformed into the other matrix by a sequence of elementary row operations.
- **Fact about Row Equivalence**: If the augmented matrices of two linear systems are row equivalent, then the two systems have the same solution set.

#### Notation

Add (-3)R2 to R1, hence R1 is changed but R2 keep intact:

```
    ~
R1 + (-3)R2
```

**Avoid multiply a scalar on the row to be changed:**

```
Not good:
   ~
2R1 + R2
```

Try to make the matrix to the below form (**Strictly Triangular System**):

![Strictly Triangular System](https://latex.codecogs.com/svg.latex?\left[\begin{array}{cccc|c}1&1&1&1&6\\0&-1&-1&1&0\\0&0&-3&-2&-13\\0&0&0&-1&-2\end{array}\right])

## 1.2 Row Echelon Form (梯阵式)

A matrix is in echelon form if

1. Any rows consisting entirely of zeros are grouped at the bottom of the matrix.
2. The first nonzero element of each row is 1. This element is called a **leading 1**.
3. The leading 1 of each row after the first is positioned to the right of the leading 1 of the previous row.

(This implies that all the elements below a leading 1 are zero.)

![Row Echelon Form](https://latex.codecogs.com/svg.latex?\begin{bmatrix}*&&*&&*\\0&&*&&*\\0&&0&&*\end{bmatrix})

The process of using row operations to transform a linear system into one whose augmented matrix is in row echelon form is called **Gaussian elimination**.

### Reduced Row Echelon Form (简约梯阵式)

A matrix is in reduced row echelon form

1. If the matrix is in row echelon form.
2. If the first nonzero entry in each row is **the only nonzero entry in its column**.

![Non-Reduced Echelon Form](https://latex.codecogs.com/svg.latex?\begin{bmatrix}1&&*&&*&&*\\0&&1&&*&&*\\0&&0&&0&&1\end{bmatrix}) -> ![Reduced Echelon Form](https://latex.codecogs.com/svg.latex?\begin{bmatrix}1&&0&&0&&*\\0&&1&&0&&*\\0&&0&&0&&1\end{bmatrix})

The process of using elementary row operations to transform a matrix into reduced row echelon form is called **Gauss-Jordan reduction**. The reduced echelon form of a matrix is **unique**.

### Solve a System using Gauss-Jordan Elimination

1. Write the _augmented matrix_ of the system.
2. Obtain an equivalent augmented matrix in _reduced echelon form_. Decide whether the system is consistent.
  - If not, stop;
  - Otherwise, go to the next step.
3. Write the system of equations corresponding to the matrix obtained in step 2.
4. State the _solution_ by expressing each basic variable in terms of the free variables and declare the free variables.

### Underdetermined system

The number of variables > The number of equations. Many solutions.

- Using multiple parameters (`r`, `s`, ...) is okay

### Overdetermined system

The number of variables < The number of equations.

### Homogeneous System of linear Equations

A system of homogeneous linear equations that has more variables than equations has many solutions.

e.g. ![Homogeneous System of linear Equations](https://latex.codecogs.com/svg.latex?\begin{cases}x_1+2x_2-5x_3=0\\-2x_1-3x_2+6x_3=0\end{cases})

## 1.3 & 1.4 Matrix Algebra

### Equality

Two matrices are equal if:

- They are of the same size;
- If their corresponding elements are equal.

### Addition

Let A and B be matrices of the same size:

- Their sum `A + B` is the matrix obtained by **adding together the corresponding elements of A and B**.
  - The matrix `A + B` will be of the same size as A and B.
- If A and B are _not_ of the same size, they _cannot be added_, and we say that _the sum does not exist_.

### Negation and Subtraction

- The matrix `(-1)C` is written `–C` and is called **the negative of `C`**.
- We now define subtraction in terms of _addition and scalar multiplication_.
  - `A – B = A + (–1)B`

### Multiplication

Let `A` be a matrix and `c` be a scalar.

- The scalar multiple of `A` by `c`, denoted `cA`, is the matrix obtained by multiplying every element of `A` by `c`.
  - The matrix `cA` will be the same size as `A`.

Let the **number of columns** in a matrix `A` be the **same** as the **number of rows** in a matrix `B`. The product `AB` then exists.

![Multiplication](https://latex.codecogs.com/svg.latex?c_{ij}=\begin{bmatrix}a_{i1}&&a_{i2}&&\dots&&a_{in}\end{bmatrix}\begin{bmatrix}b_{1j}\\b_{2j}\\\vdots\\b_{nj}\end{bmatrix}=a_{i1}b_{1j}+a_{i2}b_{2j}+\dots+a_{in}b_{nj})

**NOTE**: `AB` != `BA`

#### Size of a Product Matrix

If A is a `m * r` matrix and B is an `r * n` matrix:

- Because A has `m` columns and B has `n` rows. Thus AB **exits**.
- And AB will be a `m * n` matrix.

### Algebraic Properties of Matrix Operations

- Addition: ...
- Multiplication: **NOT commutative (cannot change the order of matrices)**

### **Caution**

- **No cancellation laws**
  - `AB = AC` **does not imply** `B = C`
  - `PQ = O` **does not imply** `P = O` or `Q = O` (`O` is an all-0 matrix)

### Transpose (转置) of a Matrix

The transpose of a matrix `A`, denoted ![Transpose](https://latex.codecogs.com/svg.latex?A^T), is the matrix whose **columns are the rows** of the given matrix `A`.

#### Properties of Transpose

**Transpose of a product**: ![Transpose of a product](https://latex.codecogs.com/svg.latex?(AB)^T=B^TA^T) <!-- Broken on Atom -->

### Symmetric Matrix

A symmetric matrix is a matrix that is **equal to its transpose**.

- If `A` and `B` are _symmetric matrices of the same size_, the product `C` is **also symmetric**.

### The Inverse of a Matrix

Let A be an `n * n` matrix.

- If a matrix `B` can be found such that ![Inverse](https://latex.codecogs.com/svg.latex?AB=BA=I_n), then `A` is said to be **invertible** and **`B` is called the inverse** of `A`.
- If such a matrix `B` does not exist, then `A` has no inverse (denote ![](https://latex.codecogs.com/svg.latex?B=A^{-1}), and ![](https://latex.codecogs.com/svg.latex?A^{-k}=(A^{-1})^k)). <!-- Broken on Atom -->

**If a matrix has an inverse, that inverse is unique.**

#### Why we need inverse?

**Nonsingular = Invertible Matrices**

- A square `n * n` matrix `A` is nonsingular (invertible) if there exists a matrix ![](https://latex.codecogs.com/svg.latex?A^{-1}) such that ![](https://latex.codecogs.com/svg.latex?AA^{-1}=A^{-1}A=I).
- The matrix ![](https://latex.codecogs.com/svg.latex?A^{-1}), if it exists, is called **the inverse of `A`**.
  - If `A` does not have an inverse (![](https://latex.codecogs.com/svg.latex?A^{-1}) does not exist), then `A` is singular (noninvertible).
- Nonsingular matrix = _consistent_ linear system
- Singular matrix = _inconsistent_ linear system
