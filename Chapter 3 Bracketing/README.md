# Chapter 3 Bracketing

This chapter presents a variety of bracketing methods for univariate functions, or functions involving a single variable. Bracketing is the process of identifying an interval in which a local minimum lies and then successively shrinking the interval. For many functions, derivative information can be helpful in directing the search for an optimum, but, for some functions, this information may not be available or might not exist. This chapter outlines a wide variety of approaches that leverage different assumptions. Later chapters that consider multivariate optimization will build upon the concepts introduced here.

## 3.1 Unimodality

Several of the algorithms presented in this chapter assume unimodality of the objective function. A unimodal function f is one where there is a unique x&star; such that f is monotonically decreasing for x &le; x&star; and monotonically increasing for x &ge; x&star;. It follows from this definition that the unique global minimum is at x&star;, and there are no other local minima.

Given a unimodal function, we can bracket an interval [a, c] containing the global minimum if we can find three points a < b < c, such that f(a) > f(b) < f(c).

## 3.2 Finding an Initial Bracket

When optimizing a function, we often start by first bracketiung an interval containing a local minimum. We then successively reduce the size of the bracketed interval to converge on the local minimum. A simple procedure can be used to find an initial bracket. Starting at a given point, we take a step in the positive direction. The distance we take is a hyperparameter to this algorithm, but the algorithm provided defaults it to 1x10<sup>-2</sup>. We then serach in the downhill direction to find a new point that exceeds the lowest point. With each step, we expand the step size by some factor, which is another hyperparameter to this algorithm that is often set to 2. 

```
function bracket_minimum(f, x=0; s=1e-2, k=2.0)
	a, ya = x, f(x)
	b, yb = a + s, f(a + s)
	if yb > ya
		a, b = b, a
		ya, yb = yb, ya
		s = -s
	end
	while true
		c, yc = b + s, f(b + s)
		if yc > yb
			return a < c ? (a, c) : (c, a)
		end
		a, ya, b, yb = b, yb, c, yc
		s *= k
	end
end
```