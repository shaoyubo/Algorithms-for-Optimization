# Chapter 1. Introduction

Many disciplines involve optimization at their core. In physics, systems are driven to their lowest energy state subject to physical laws. In business, corporations aim to maximize shareholder value. In biology, fitter organisms are more likely to survive. This book will focus on optimization from an engineering perspective, where the objective is to design a system that optimizes a set of metrics subject to constraints. 

## 1.1 History

We will begin our discussion of the history of algorithms for optimization with the ancient Greek philosophers. Pythagoras of Samos, the developer of the Pythagorean theorem, claimed that "the principles of mathematics were the principles of all things," popularizing the idea that mathematics could model the world. Both Plato and Aristotle used reasoning for the purpose of societal optimization. They contemplated the best style of human life, which involves the optimization of both individual lifestyle and functioning of the state. Aristotelian logic was an early formal process - an algorithm - by which deductions can be made.

Central to the study of optimization is the use of algebra, which is the study of the rules for manipulating mathematical symbols. Optimization problems are often posed as a search in a space defined by a set of coordinates. The concept of calculus, or the study of continuous change, plays an important role in our discussion of optimization. The mid-twentieth century saw the rise of the electronic computer, spurring interest in numerical algorithms for optimization. The ease of calculations allowed optimization to be applied to much larger problems in a variety of domains. One of the major breakthroughs came with the introduction of linear programming, which is an optimization problem with a linear objective function and linear constraints.

Decades of advances in large scale computation have resulted in innovative physical engineering designs as well as the design of artificially intelligent systems. The optimization of deep neural networks is fueling a major revolution in artificial intelligence that will likely continue.

## 1.2 Optimization Process

A typical engineering design optimization process is shown in figure 1.2. The role of the designer is to provide a problem specification that details the parameters, constants, objectives, and contraints that are to be achieved. The designer is responsible for crafting the problem and quantifying the merits of potential designs. The designer also typically supplies a baseline design or inital design point to the optimization algorithm.

This book is about automating the process of refining the design to improve performance. An optimization algorithm is used to incrementally improve the design until it can no longer be improved or until the budgeted time or cost has been reached. The designer is responsible for analyzing the result of the optimization process to ensure its suitability for the final appliication. Misspecifications in the problem, poor baseline designs, and improperly implemented or unsuitable optimization algorithms can all lead to suboptimal or dangerous designs. 

There are several advantages of an optimization approach to engineering design. First of all, the optimization process provides a systematic, logical design procedure. If properly followed, optimization algorithms can help reduce the chance of human error in design. Sometimes intuition in engineering design can be misleading; it can be much better to optimize with respect to data. Optimization can speed the process of design, especially when a procedure can be written once and then be reapplied to other problems. Traditional engineering techniques are often visualized and reasoned about by humans in two or three dimensions. Modern optimization techniques, however, can be applied to problems with milions of variables and constraints.

There are also challenges associated with using optimization for design. We are generally limited in our computational resources and time, and so our algorithms have to be selective in how they explore the design space. Fundamentally, the optimization algorithms are limited by the designer's ability to specify the problem. In some cases, the optimization algorithm may exploit modeling errors or provide a solution that does not adequately solve the intended problem. When an algorithm results in an apparently optimal design that is counterintuitive, it can be difficult to interpret. Another limitation is that many optimization algorithms are not always guaranteed to produce optimal designs.

## 1.3 Basic Optimization Problem

The basic optimization problem is:

> minimize<sub>x</sub> f(x)

> subject to x &in; X

Here x is a design point. A design point can be represented as a vector of values corresponding to different design variables. Any value of x from among all points in the feasible set X that minimizes the objective function is called a solution or minimizer. A particular solution is written x<sup>&star;</sup>.

In particular, a problem 

> maximize<sub>x</sub> f(x)

> subject to x &in; X

can be replaced by

> minimize<sub>x</sub> -f(x)

> subject to x &in; X

The new form is the same problem in that it has the same set of solutions.

## 1.4 Constraints

Many problems have constraints. Each constraint limits the set of possible solutions and together the constraints define the feasible set X. Feasible design points do not violate any constraints. For example, consider the following optimization problem:

> minimize<sub>x<sub>1</sub>, x<sub>2</sub></sub> f(x<sub>1</sub>, x<sub>2</sub>)

> subject to x<sub>1</sub> &ge; 0, x<sub>2</sub> &ge;0, x<sub>1</sub> + x<sub>2</sub> &le; 1

Constraints are typically written with &le;, &ge;, or =. If constraints involve < or >, then the feasible set does not include the constraint boundary.

## 1.5 Critical Points

Figure 1.6 shows a univariate function f(x) with several labeled critical points, where the derivative is zero, that are of interest when discussing optimization problems. When minimizing f, we wish to find a global minimizer, a value of x for which f(x) is minimized. A function may have at most one global minimum, but it may have multipe global minimizers.

Figure 1.6 shows two types of local minima: strong local minima and weak local minimal. A strong local minimizer, also known as a strict local minimizer, is a point that uniquely minimizes f within a neighborhood. A weak local minimizer is a local minimizer that is not a strong minimizer.

The derivative is zero at all local and global minima of continuous, unbounded objective functions. While having a zero derivative is a necessary condition for a local minimum, it is not a sufficient condition.

Figure 1.6 also has an inflection point where the derivative is zero but the point does not locally minimize f. An inflection point is where the sign of the second derivative of f changes, which corresponds to a local minimum or maximum of f'. An inflection point does not necessarily have a zero derivative.

## 1.6 Conditions for Local Minima

Many numerical optimization methods seek local minima. Local minima are locally optimal, but we do not generally know whether a local minimum is a global minimum. The conditions we discuss in this section assume that the objective function is differentiable. Derivatives, gradients, and Hessians are reviewed in the next chapter. We also assume in this section that the problem is unconstrained. 

### 1.6.1 Univariate

A design point is guaranteed to be at a strong local minimum if the local derivative is zero and the second derivative is positive:

1. f'(x<sup>&star;</sup>) = 0

2. f''(x<sup>&star;</sup>) > 0

A zero derivative ensures that shifting the point by small values does not affect the function value. A positive second derivative ensures that the zero first derivative occurs at the bottom of a bowl.

A point can also be at a local minimium if it has a zero derivative and the second derivative is merely nonnegative:

1. f'(x<sup>&star;</sup>) = 0, the first-order necessary condition (FONC)

2. f''(x<sup>&star;</sup>) &ge; 0, the second-order necessary condition (SONC)

There conditions are referred to as necessary because all local minima obey these two rule.

### 1.6.2 Multivariate

The following conditions are necessray for x to be at a local mimimum of f:

1. &nabla;f(x) = 0, the first-order necessary condition (FONC)

2. &nabla;<sup>2</sup>f(x) is positive semidefinite, the second-order necessary condition (SONC)

While necessary for optimality, the FONC and SONC are not sufficient for optimality. For unconstrained optimization of a twice-differentiable function, a point is guaranteed to be at a strong local minimum if the FONC is satisfied and &nabla;<sup>2</sup>f(x) is positive definite. These conditions are collectively known as the second-order sufficient condition (SOSC).

## 1.7 Contour Plots

This book will include problems with a variety of numbers of dimensions, and will need to display information over one, two, or three dimensions. Functions of the form f(x<sub>1</sub>, x<sub>2</sub>) = y can be rendered in three-dimensional space, but not all orientations provide a complete view over the domain. A contour plot is a visual representation of a three-dimensional surface obtained by plotting regions with constant y values, known as contours, on a two-dimensional plot with axes indexed by x<sub>1</sub> and x<sub>2</sub>.

## 1.8 Overview

This section provides a brief overview of the chapters of this book.

Chapter 2 begins by discussing derivatives and their generalization to multiple dimensions. Chapter 3 discusses bracketing, which involves identifying an interval in which a local minimum lies for a univariate function. Chapter 4 introduces local descent as a general approach to optimizing multivariate functions. Chapter 5 builds upon the previous chapter, explaining how to use first-order
information obtained through the gradient estimate as a local model to inform the descent direction. Chapter 6 shows how to use local models based on second-order approximations to inform local descent.
Chapter 7 presents a collection of direct methods for finding optima that avoid using gradient information for informing the direction of search. Chapter 8 introduces stochastic methods, where randomness is incorporated into the optimization process. Chapter 9 discusses population methods, where a collection of points is used to explore the design space. Chapter 10 introduces the notion of constraints in optimization problems. Chapter 11 makes the assumption that both the objective function and constraints are linear. Chapter 12 shows how to address the problem of multiobjective optimization, where we have multiple objectives that we are trying to optimize simultaneously. Chapter 13 discusses how to create sampling plans consisting of points that cover the design space. Chapter 14 explains how to build surrogate models of the objective function. Chapter 15 introduces probabilistic surrogate models that allow us to quantify our confidence in the predictions of the models. Chapter 16 shows how to use the probabilistic models from the previous chapter to guide surrogate optimization. Chapter 17 explains how to perform optimization under uncertainty, relaxing the assumption made in previous chapters that the objective function is a deterministic function of the design variables. Chapter 18 outlines approaches to uncertainty propagation, where known input distributions are used to estimate statistical quantities associated with the output distribution. Chapter 19 shows how to approach problems where the design variables are constrained to be discrete. Chapter 20 discusses how to search design spaces consisting of expressions defined by a grammar. Chapter 21 explains how to approach multidisciplinary design optimization.

## 1.9 Summary

- Optimization in engineering is the process of finding the best system design subject to a set of constraints.

- Optimization is concerned with finding global minima of a function.

- Minima occur where the gradient is zero, but zero-gradient does not imply optimality.