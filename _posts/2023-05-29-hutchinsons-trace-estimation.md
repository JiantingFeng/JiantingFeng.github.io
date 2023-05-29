---
title: Hutchinson's Trace Estimation
---

# Intuition

Given a matrix $$A\in \mathbb{R}^{n\times n}$$, if we want to compute its trace, then we can use this trick, called *Hutchinson's Trace Estimation*.

The intuition of Hutchinson's trace estimator is **replace matrix-matrix product by matrix-vector product, and use Monte-Carlo to estimate the trace**

$$\mathrm{tr}\left(A\right) = \mathrm{tr}\left(A\mathbb{E}[\varepsilon \varepsilon^T]\right)=\mathbb{E}\left[\mathrm{tr}(A\varepsilon\varepsilon^T)\right]=\mathbb{E}\left[\mathrm{tr}(\varepsilon^TA\varepsilon)\right] = \mathbb{E}\left[\varepsilon^T A \varepsilon\right]$$

where $$\varepsilon\sim \mathcal{N}(0, I)\in\mathbb{R}^n$$, then you can use Monte Carlo method to approximate the expectation.

But, why don't we directly calculate the trace?

Suppose you need to calculate the trace of a matrix function, i.e. $$\mathrm{tr}(A^2), \mathrm{tr}( A^3)$$, etc

By traditional way, you should go through the following steps

- Calculate the Jordan canonical form of $$A$$ . Indeed, in numerical computation, every matrix is diagonalizable since all eigenvalues are different (approximation error). Then the cost of this step takes $$\mathcal{O}(n^3)$$ , the diag. form is denoted as $$\Lambda$$
	
- Calculate $$f(\Lambda)$$ , and add them up to calculate trace, which takes $$\mathcal{O}(n)$$
	
Total time complexity is $$\mathcal{O}(n^3)$$

If we use *Hutchinson's Trace Estimation* to estimate $$\mathrm{tr}  A^2$$


- For $$t=0, 1, \cdots, T$$ do
	- Draw $$\varepsilon\sim \mathcal{N}(0,  I)\in\mathbb{R}^n$$
	- Calculate $$\varepsilon^T A^2\varepsilon$$, you can calculate vector-matrix product rather than matrix-matrix product, which takes $$\mathcal{O}(n^2)$$
- Calculate the average of previous results, takes $$\mathcal{O}(T)$$
- Total time complexity is $$\mathcal{O}(n^2T)$$

The vector $$\varepsilon$$ is referred as *probe vector*. If the number of probe vector is smaller than the dimension $$n$$, we can reduce the time complexity.


# Formal Statement and Property

W.I.P.
