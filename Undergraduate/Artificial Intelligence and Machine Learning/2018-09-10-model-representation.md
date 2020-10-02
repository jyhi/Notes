# Linear Regression: Model Representation

## Supervisored

                Traning Set
                     |
              Learning Algorithm
                     |
    Size of house -> h -> Estimated Price

## Linear Regression Model

Let:
 - ![h]
 - ![J]

[h]: https://latex.codecogs.com/svg.latex?h_\theta(x)=\theta_0+\theta_1x
[J]: https://latex.codecogs.com/svg.latex?J(\theta_0,\theta_1)=\frac{1}{2m}\sum^m_{i=1}(h_\theta(x^{(i)})-y^{(i)})^2

## Gradient Descent With One Parameter

Gradient descent can converge to a local minimum.

```
repeat until convergence {
  x[j] := x[j] - a * derivative(x[j], J(x[0], x[1]))
}
```

Given **cost function** `J(x[0], x[1])`, we want `min(J(x[0], x[1]))`.

- Start with some `x[0]`, `x[1]`
- Keep changing `x[0]`, `x[1]` to reduce `J(x[0], x[1])` until we (hopefully) end up with a minimum
- `a` is **step size**
  - If `a` is too small, the process will be too slow
  - If `a` is too large, the process can overshoot the minimum, possibly causing failure of convergence (even diverge)
  - As it is approaching a local minimum, gradient descent will automatically take smaller steps
    - No need to decrease `a` overtime

Note: simultaneously update 2 params!

```
temp0 := x[0] - a * derivative(x[0], J(x[0], x[1]))
temp1 := x[1] - a * derivative(x[1], J(x[0], x[1]))

# Update parameters after calculation
x[0]  := temp0
x[1]  := temp1
```

## "Batch" Gradient Descent

Each step of gradient descent uses all the training examples.

## Gradient Descent With Multiple Variables

`Repeat {`

![gradient-descent-multivar]

`}`

[gradient-descent-multivar]: https://latex.codecogs.com/svg.latex?\theta_j:=\theta_j-\alpha\frac{\delta}{\delta\theta_j}\sum{(\theta)}

## Feature Scaling

Ideas:

- **Make sure features are on a similar scale**
- **Get every feature into approximately a `-1 <= x_i <= 1` range**

## Mean Normalization

Replace `x_i` with `x_i - u_i` to make features have approximately zero mean (do not apply to `x_0 = 1)

## Learning Rate (\alpha)

Making sure gradient descent is working correctly.

- If `\alpha` is too small: slow convergence
- If `\alpha` is too large: `J(\theta)` may diverge
  - Slow converge also possible
- For sufficiently small `\alpha`, `J(\theta)` should decrease on every iteration

## Polynomial Regression

...

## Normal Equation

Method to solve `\theta` analytically.

![norm-eq]

Octave:

```matlab
pinv(X' * X) * X' * Y
```

[norm-eq]: https://latex.codecogs.com/svg.latex?\theta=(X^TX)^{-1}X^Ty

### What If `X^T X` Is Not Invertible?

This is because:

1. Redundant features (linearly dependent)
  - e.g.
    - `x1 = size in feet2`
    - `x2 = size in m2`
2. Too many features
  - e.g. `m <= n`

To solve, remove some features.

## Comparison Between Gradient Descent And Normal Equation

- Gradient Descent
  - Need to choose `\alpha`
  - Needs many iterations
  - Works well even when `n` is large
- Normal Equation
  - No need to choose `\alpha`
  - Don't need to iterate
  - Need to compute `(X^TX)^{-1}`
  - Slow if `n` is very large
