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

Here 