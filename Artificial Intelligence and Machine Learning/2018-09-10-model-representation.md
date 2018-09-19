# Linear Regression With One Variable: Model Representation

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
[J]: https://latex.codecogs.com/svg.latex?J(\theta_0,\theta_1)=\frac{1}{2m}\sum^m_{i=1}(h\theta(x^{(i)})-y^{(i)})^2

## Gradient Descent

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

### "Batch" Gradient Descent

Each step of gradient descent uses all the training examples
