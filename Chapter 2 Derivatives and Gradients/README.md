# Chapter 2. Derivatives and Gradients

Optimization is concerned with finding the design point that minimizes (or maximizes) an objective functon. Knowing how the valu of a function changes as its input is varied is useful because it tells us in which direction we can move to improve on previous points. The change in the value of the function is measured by the derivative in one dimensionand the gradientin multiple dimensions. This chapter briefly reviews some essential elements from calculus.

## 2.1 Derivatives

The derivative f'(x)of a function f of a single variable x is the rate at which the value of f changes at x. The value of the derivative equals the slope of the tangent line.

We can us the derivative to provide a linear approximation of the function near x:

> f(x + &nabla;x) &asymp; f(x) + f'(x)&nabla;x.

The derivative is the ratio between the change in f and the change in x at the point x:

> f'(x) = &nabla;f(x) / &nabla;x = df(x) / dx

which is the change in f(x) divided by the change in x as the step becomes infinitesimally small.

The limit equation defining the derivative can be presented in three different ways:the forward difference, the central difference, and the backward difference.

```
The implementation details of symbolic differentiation is outside the scope of this text. Various software packages, such as SymEngine.jl in Julia and SymPy in Python, provide implementations.

julia> using SymEngine
julia> @vars x; # define x as a symbolic variable 
julia> f = x^2 + x/2 - sin(x)/x;
julia> diff(f, x)
1/2 + 2*x + sin(x)/x^2 - cos(x)/x
```

## 2.2 Derivatives in Multiple Dimensions

