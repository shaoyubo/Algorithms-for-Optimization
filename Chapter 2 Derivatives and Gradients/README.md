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

The gradient is the generalization of the derivative to multivariate functions. It captures the local slope of the function, allowing us to predict the effect of taking a small step from a point in any direction. Recall that the derivative is the slope of the tangent line. The gradient points in the direction of steepest ascent of the tangent hyperplane. A hyperplane in an n-dimensional space is the set of points that satisfies

> w<sub>1</sub> + ... + w<sub>n</sub> = b

for some vector w and scalar b. A hyperplane has n - 1 dimensions.

The gradient of f at x is written &nabla;f(x) and is a vector. Each component of that vector is the partial derivative of f with respect to that component. The Hessian of a multivariate function is a matrix containing all of the second derivatives with the respect to the input. The second derivatives capture information about the local curvature of te function.

The directional derivative &nabla;<sub>s</sub>f(x) of a multivariate function f is the instantaneous rate of change of f(x) as x is moved with velocity s. The directional derivative can be computed using the gradient of the functon:

>  &nabla;<sub>s</sub>f(x) = &nabla;f(x)<sup>T</sup>s.

Another way to compute the directional derivative &nabla;<sub>s</sub>f(x) is to define g(&alpha;) = f(x + &alpha;s) and then compute g'(0).

## 2.3 Numerical Differentiation

The process of estimating derivativs numerically is referred to as numerical differentiation. Estimates can be derived in different ways from function evaluations. This section discusses finite difference methods and the complex step method.

### 2.3.1 Finite Difference Methods

As the name implis, finite difference methods compute the difference between two values that differ by a finite step size. They approximate the derivative definitions using small differences. Mathematically, the smaller the step size h, the better the derivative estimate. Practically, valus for h that are too small can result in numerical cancellation errors.

The finite difference methods can be derived using the Taylor expansion. And we can show that the approximation has quadratic error.

### 2.3.2 Complex Step Method

We often run into the problem of needing to choose a step size h small enough to provide a good approximation but not too small so as to lead to numerical subtractive cancellation issues. The complex step method bypasses the effect of substractive cancellation by using a single function evaluation. We evaluate the function once after taking a step in the imaginary direction.

The ral part approximates f(x) to within O(h<sup>2</sup>) as h approaches 0.

## 2.4 Automatic Differentiation

This section introduces algorithms for the numeric evaluation of derivatives of functions specified by a computer program. Key to these automatic differentiation techniques is the application of the chain rule. A program is composed of elementary operations like addition, subtraction, multiplication, and division.

This process can be automated through the use of a computational graph. A computational graph represnets a function where the nodes are operations and the edges are input-output relations.The leaf nodes of a computational graph are input variables or constants, and terminal nodes are values output by the function.

There are two methods for automatically differentiating f using its computational graph. The forward accumulation method used by dual numbers traverses the tree from inputs to outputs, whereas reverse accumulation requires a backwards pass through the graph.

### 2.4.1 Forward Accumulation