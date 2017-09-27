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
