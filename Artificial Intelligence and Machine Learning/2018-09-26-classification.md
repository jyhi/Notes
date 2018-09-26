# Logistic Regression: Classification

![cls]

[cls]: https://latex.codecogs.com/svg.latex?y\in\{0,1\}

## Logistic Function

**Hypothesis:** ![logistic-func]

[logistic-func]: https://latex.codecogs.com/svg.latex?0\leq{h_\theta(x)}\leq1

## Hypothesis Representation

### Logistic Regression Model

#### Sigmoid Function

![sigmoid]

[sigmoid]: https://latex.codecogs.com/svg.latex?h_\theta(x)=\frac{1}{1+e^{-\theta^TX}}

## Decision Boundary

...

## Cost Function

![cost]

[cost]: https://latex.codecogs.com/svg.latex?J(\theta)=-\frac{1}{m}[\sum^m_{i=1}y^{(i)}logh_\theta(x^{(i)})+(1-y^{(i)})log(1-h_\theta(x^{(i)}))]

```
repeat {
  theta_j := theta_j - alpha * diff(J(theta), theta_j)
}
```

Note:
  - Simultaneously update all `theta_j`s!
  - The algorithm looks identical to linear regression (?)

## Advanced Optimization

- Optimization algorithms:
  - Conjungate gradient
  - BFGS
  - L-BFGS
- Pros
  - No need to manually pick `alpha`
  - Often faster than gradient descent
- Cons
  - Complex
