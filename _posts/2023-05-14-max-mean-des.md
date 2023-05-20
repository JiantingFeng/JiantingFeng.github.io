---
title: Maximum Mean Discrepancy and Reproduce Hilbert Space
layout: post
date: '2023-05-14'
description: Introduction of Maximum Mean Discrepancy
categories:
- machine-learning
giscus_comments: true
---

## Intuition
The concept of *Maximum Mean Discrepancy* is introduced in [gretton12a](https://www.jmlr.org/papers/volume13/gretton12a/gretton12a.pdf) to solve following question:
	
Let $$X$$ and $$Y$$ be random variables defined on a topological space $$\mathcal{X}$$ , with respective Borel probability measure $$p$$ and $$q$$ . Given observations $$X = \{X_1,\cdots, X_n\}$$ and $$Y=\{Y_1, \cdots, Y_m\}$$ i.i.d. from $$p$$ and $$q$$ , respectively. **How can we decided whether** $$p\neq q$$?

In other words, we need to measure the **distance** between two group of samples.

## Technique Details
First we have following lemma,

> Let $$(\mathcal X, d)$$ be a metric space, and $$p, q$$ be two Borel probability measures defined on $$\mathcal X$$ . Then $$p=q$$ if and only if $$\mathbb{E}_X[f(X)]=\mathbb{E}_Y[f(Y)]$$ for all $$f\in C(\mathcal X)$$ . Where $$C(\mathcal X)$$ denoted the space of bounded  continuous functions on $$\mathcal X$$.


With the help of this lemma, we can turn our problem into an equivalent form:

Let $$\mathcal F\in C(\mathcal X)$$, we define *maximal mean discrepancy* (MMD) as 


$$\textrm{MMD}[\mathcal F, p, q] = \sup_{f\in\mathcal F}\left(\mathbb{E}_X[f(X)] - \mathbb{E}_Y(f(Y)\right)$$ 

where $$x\sim p$$ and $$y\sim q$$, then $$p = q$$ **if and only** $$\textrm{MMD}[\mathcal F, p, q] = 0$$.

*MMD* is also referred as **integral probability metric**. In practicle, we tends to use a biased empirical estimation of *MMD*:

$$\widehat{\textrm{MMD}}[\mathcal F, X, Y] = \sup_{\varphi\in\mathcal H}\left(\frac{1}{m}\sum_{i=1}^m\varphi(X_i) - \frac{1}{n}\sum_{i=1}^n\varphi(Y_i)\right)$$

Here, we restrict the function class in a unit ball of **reproducing kernel Hilbert space** $$\mathcal H$$.

This empiricial formula seems intractable as well because of the $$\sup$$, however, we will illustrate how to get rid of that in the following context. Now, let's first under an important concept: *Reproducing Kernel Hilbert Space*.

### Reproducing Kernel Hilbert Space (RKHS)

Indeed, RKHS is a ubiquitus concept in the field of Machine Learning. In order to figure out what it is, firstly we need some math foundations, I put some useful links here:

- [Hilbert Space](https://mathworld.wolfram.com/HilbertSpace.html)
- [Riesz Representation Theorem](https://www.wikiwand.com/en/Riesz_representation_theorem)
- [Kernel Method](https://www.wikiwand.com/en/Kernel_method)

The kernel function is a generalization of normal inner product in Euclidan space, with **non-negative, symmetry, and bilinearily**. 

Given any two data points $$x, x^\prime \in \mathcal X$$, together with feature map $$\Phi: \mathcal X\to\mathcal F\subset \mathbb R^{N}$$, we can define a **kernel** $$K: \mathcal X\times \mathcal X\to \mathbb R$$ as:

$$
\forall x, x^\prime\in\mathcal X,\qquad K(x, x^\prime) = \langle \Phi(x), \Phi(x^\prime)\rangle = \Phi(x^\prime)^T\Phi(x)
$$

The reason why we use kernel function rather than original inner product is that: in many machine learning problems, inner product in feature space is extensively (e.g. support vector machine). Normally we don't use the original form $$\Phi(x)$$, which always appears in the form of inner product. 

then, the Reproducing Kernel Hilbert space is a Hilbert space with **reproducing property**:

$$
	\forall h\in\ \mathcal H, \forall x\in\mathcal X,\qquad h(x) = \langle h, K(x, \cdot)\rangle.
$$

By the definition of kernel, partial evaluation $$K(x, \cdot)$$ is a function from $$\mathcal X$$ to $$\mathcal F$$
therefore, from the perspective of function space, it can be viewed as the Riesz representation theorem.

Recall the evaluation function in RKHS is bounded. By Riesz representation,  for all $$x\in\mathcal H$$ , $$\exists \phi(x)\in\mathcal H$$ , such that the evaluation $$f(x) = \langle f, \phi(x)\rangle_{\mathcal H}$$ . The feature map takes the form $$\phi(x) = k(x, \cdot)$$ where $$k(\cdot, \cdot)$$ is a kernel function defined as $$k(x, z) = \langle\phi(x), \phi(z)\rangle_{\mathcal{H}}$$
- This notation can also be extended into expectation, i.e. $$\exists\mu\in\mathcal H$$ , $$\forall f\in \mathcal H$$ , we have $$\mathbb{E}f = \langle f, \mu\rangle_{\mathcal H}$$
- We have
	-
$$\mathrm{MMD}^2[\mathcal F, p, q] = \lVert \mu_p - \mu_q \rVert^2$$	- Proof is directly followed by the Riesz repr. of expectation.
- With inner product, it can also be written as $$\langle\mu_p, \mu_p\rangle_{\mathcal H}^2 - 2\langle\mu_p, \mu_q\rangle_{\mathcal H}+\langle\mu_q, \mu_q\rangle_{\mathcal H}^2$$
- Note that $$\langle\mu_p, \mu_q\rangle_{\mathcal H} = \int_{\mathcal X\times \mathcal X}k(x, z) \mathrm d\mathbb P\mathrm d\mathbb Q$$
We can expand the previous form 
- With inner product, it can also be written as $$\langle\mu_p, \mu_p\rangle_{\mathcal H}^2 - 2\langle\mu_p, \mu_q\rangle_{\mathcal H}+\langle\mu_q, \mu_q\rangle_{\mathcal H}^2$$
	- as expectation of kernel function
	- When do actual calculating, directly use sample expectation to replace the integral.
	- Empirical $$\textrm{MMD}^2 = \frac{1}{m(m-1)}\sum_i\sum_{j\neq i}k(x_i, x_j) - \frac{2}{mn}\sum_i\sum_j k(x_i, z_j) + \frac{1}{n(n-1)}\sum_i\sum_{j\neq i}k(z_i, z_j)$$
- you can use different kernel function with different hyperparameters (e,g, bandwidth for Gaussian kernel)
