---
title: Ito Lemma and Stochastic Differential Equation
layout: post
categories:
  - probability
  - financial
description: A brief introduction to stochastic differential equation and Ito lemma
date: "2023-05-27 20:00:00"
---

# Martingales in Discrete Time

## Conditional expectation

If $$\mathbf X$$ is a random variable, then $$\mathbb{E} \mathbf X$$ can be thought as the best guess for $$\mathbf X$$ given no extra information. A conditional expectation can be viewed as the best guass given certain information.

Let $$\mathbf X_1, \mathbf X_2,\cdots$$ be a series of random variables. At time $$n$$ we have wiewed the first $$n$$ values $$\mathbf X_1, \cdots, \mathbf X_n$$. If $$\mathbf Y$$ is another random variable, then

$$
    \mathbb{E}\left[\mathbf Y\vert \mathbf X_1,  \cdots, \mathbf X_n\right]
$$

can be thought as the best guess given $$\mathbf X_1, \cdots, \mathbf X_n$$. $$\mathcal{F}_n$$ represents the information contained in $$\mathbf X_1, \cdots, \mathbf X_n$$, and $$\mathcal{F}_0$$ contains no information. We have following property

1. If we have no information, then the best guess is the unconditional expectation, $$\mathbb{E}\left[\mathbf{Y}\vert \mathcal{F}_0\right] = \mathbb{E}\left[\mathbf{Y}\right] $$
2. The conditional exepctation $$\mathbb{E}\left[\mathbf{Y}\vert \mathcal{F}_n\right]$$ should only contain the information up to time $$n$$, we say $$\mathbb{E}\left[\mathbf{Y}\vert \mathcal{F}_n\right]$$ is $$\mathcal{F}_n$$-measurable, i.e.

$$
	\mathbb{E}\left[\mathbf{Y}\vert \mathcal{F}_n\right] = \varphi(\mathbf{X}_1, \cdots, \mathbf{X}_n)
$$

A basic property of conditional expectation is that

$$
	\mathbb{E}\left[\mathbb{E}\left[\mathbf{Y}\vert \mathcal{F}_n\right]\right] = \mathbb{E}\left[\mathbf{Y}\right]
$$

Besides, conditional expectation is linear, which means, for any $$a, b\in \mathbb{R}$$ and random variable $$\mathbf{Y, Z}$$, we have

$$
	    \mathbb{E}\left[a\mathbf{Y}+b\mathbf{Z}\vert \mathcal{F}_n\right] = a\mathbb{E}\left[\mathbf{Y}\vert \mathcal{F}_n\right] + b\mathbb{E}\left[\mathbf{Z}\vert \mathcal{F}_n\right]
$$

## Martingales

Martingale is a concept for modeling the fair game. Suppose $$\mathbf{X}_1, \mathbf{X}_2, \cdots$$ is a sequence of random variables associated with filtration $$\left\{\mathcal{F}n\right\}$$. A sequence of random variables $$\mathbf{M}0, \mathbf{M}1, \cdots$$ is called a _martingale_ w.r.t. filtration $$\left\{\mathcal{F}n\right\}$$ if:

1. For each $$n$$, $$\mathbf{M}_n$$ is $$\mathcal{F}_n$$ measurable with $$\mathbb{E}\left[\lvert \mathbf{M}_n\rvert\right]< \infty$$]
2. If $$m > n$$, then

$$
	\mathbb{E}\left[\mathbf{M}_n\vert \mathcal{F}_m\right] = \mathbf{M}_m.
$$

We can also define a _submartingale_ as

$$
	\mathbb{E}\left[\mathbf{M}_n\vert \mathcal{F}_m\right] \leq \mathbf{M}_m
$$

and a _supermartingale_

$$
	\mathbb{E}\left[\mathbf{M}_n\vert \mathcal{F}_m\right] \geq \mathbf{M}_m
$$

Note: For all "fair" games you play in casino, they are always submartingale since you have to pay commission.

# Brownian Motion

## Limits of sums of independent variables

Suppose $$\mathbf{X}_1, \mathbf{X}_2,\cdots, \mathbf{X}_n$$ are i.i.d. random variables with mean $$\mu$$ and variance $$\sigma^2<\infty$$. Let

$$
	\mathbf{Z}_n = \dfrac{\left(\mathbf{X}_1 + \cdots + \mathbf{X}_n\right) - n\mu}{\sigma\sqrt{n}}
$$

Let $$\Phi(b)$$ be the c.d.f. of standard Gaussian, i.e.

$$
	\Phi(b) = \int_{-\infty}^b \dfrac{1}{\sqrt{2\pi}} e^{-x^2/2} \mathrm{d} x
$$

By central limit theorem,

$$
	\lim_{n\to\infty} \mathbb{P}\left[a\leq Z_n\leq b\right] = \Phi(b) - \Phi(a)
$$

the proof of CLT can be easily derived by the characteristic function.

## Limits of random walks

Brownian motion can be viewed as the limit of random walk as the time and space increments tends to zero. Suppose $$\mathbf{X}_1, \mathbf{X}_2, \cdots $$ are independent random variables with $$\mathbb{P}\left[\mathbf{X}_j = 1\right] = \mathbb{P}\left[\mathbf{X}_j = -1\right] = \dfrac{1}{2}$$ and let

$$
	S_n = X_1 + \cdots + X_n
$$

here we suppose time and space difference $$\Delta x = 1, \Delta t = 1$$. If we choose time increment as $$\Delta t = \dfrac{1}{N}$$ where $$N$$ is sufficiently large, we view the process at

$$
	\Delta t, 2\Delta t, 3\Delta t, \cdots
$$

and at each time step we have a jump $$\pm \Delta x$$, the value of the process will be

$$
	W_1^{N} = \Delta x\left(X_1 + \cdots + X_N\right)
$$

we would like to choose $$\text{Var}\left(W_1^N\right) = 1$$, i.e.

$$
\begin{align*}
	\text{Var}\left(W_1^{N}\right) & = \left(\Delta x\right)\left(\text{Var}X_1 + \cdots + \text{Var}X_N\right) \\
	                               & = \left(\Delta x\right)^2\cdot N = 1                                       \\
\end{align*}
$$

we get $$\Delta x = \dfrac{1}{\sqrt{N}}$$, note how we choose $$\Delta t$$, we deduce that

$$
	\Delta x = \sqrt{\Delta t}
$$

## Brownian Motion

_Brownian motion_ or _Wiener process_ is a model of continuous random process. Let $$B_t = B(t)$$ be the value at time $$t$$, $$B_t$$ is a random variable. A collection of random variable indexed by time is called a _stochastic process_.

There are three major assumptions about $$B_t$$

1. \textbf{Stationary increments.} If $$s < t$$, then the distribution of $$B_t - B_s$$ is identical to the distribution of $$B_{t-s}$$,
2. \textbf{Independent increments.} If $$s < t$$, then the random variable $$B_t - B_s$$ is independent of $$B_r$$ if $$r < s$$,
3. \textbf{Continuous path.} The function $$t\mapsto B_t$$ is continuous (i.e. H\"older continuous with exponent equals $$1/ 2$$ ).

For convenience, we often set $$B_0 = 0$$.

A stochastic process $$B_t$$ is called (one-dimensional) _Brownian motion_ if it satisfies the following.

1. $$B_0 = 0$$,
2. For $$s < t$$, $$B_t - B_s \sim \mathcal{N}\left((t-s)m, (t-s)\sigma^2\right)$$ where $$m$$ is \textit{drift} and $$\sigma^2$$ is _variance_,
3. If $$s < t$$, then $$B_t - B_s$$ is independent of $$B_r$$ if $$r < s$$,
4. With probability $$1$$, the function $$t\mapsto B_t$$ is continuous.

If $$m = 0$$ and $$\sigma^2 = 1$$, then $$B_t$$ is called _standard Brownian motion_.

Recall the reparameterization trick of standard Gaussian, take $$B_t$$ as standard Brownian motion, then

$$
	Y_t = \sigma B_t + mt
$$

is a Brownian motion with drift $$m$$ and variance $$\sigma^2$$.

# Ito Integral

## Ito Process

Let $$W_t$$ denote the standard Brownian motion, we define the _Ito process_ as following

Let $$X_t$$ be a stochastic process, $$X_t$$ is called an _Ito process_ if it satisfies the following stochastic differential equation,

$$
		\mathrm{d} X_t = \underbrace{\mu\left(t, X_t\right) \mathrm{d} t}_{\text{drifting term}} + \underbrace{\sigma\left(t, X_t\right) \mathrm{d} W_t}_{\text{diffusion term}}

$$

where $$\mu$$ and $$\sigma$$ are functions of $$t$$ and $$X_t$$.
Remembering the definition of Riemann integral, we can not integrate the stochastic differential equation directly. We need to define a new integral to solve the equation. Which is called \textit{It\^o integral}.

## Ito Integral

Recall the way we solve ordinary differential equation, we can use the following method to solve stochastic differential equation.

Let $$f(x, t)$$ be a second order differentiable function, we can calculate the Taylor expansion of it as:

$$
	\mathrm{d} f = \dfrac{\partial f}{\partial x} \mathrm{d} x + \dfrac{\partial f}{\partial t} \mathrm{d} t + \dfrac{1}{2} \dfrac{\partial^2 f}{\partial x^2} \mathrm{d} x^2 + \dfrac{1}{2} \dfrac{\partial^2 f}{\partial t^2} \mathrm{d} t^2 + \dfrac{\partial^2 f}{\partial x \partial t} \mathrm{d} x \mathrm{d} t
$$

substitute $$\mathrm dx$$ with $$\mathrm{d}X_t = \mu\left(t, X_t\right) \mathrm{d} t + \sigma\left(t, X_t\right)\mathrm{d}W_t$$, recall that $$\left(\mathrm{d}W_t\right)^2 = \mathrm{d}t$$ (magic happens here), ignore the high-order term, we get

$$
	\mathrm{d} f = \left(\dfrac{\partial f}{\partial t} + \mu\left(t, X_t\right)\dfrac{\partial f}{\partial x} + \dfrac{\sigma\left(t, X_t\right)^2}{2}\dfrac{\partial^2 f}{\partial x^2}\right) \mathrm{d}t + \sigma\left(t, X_t\right)\dfrac{\partial f}{\partial x} \mathrm{d}W_t
$$

The equation above is called _Ito's lemma_ . It is the key to solve stochastic differential equation.

Consider $$X_t = W_t^2$$, we use Ito's lemma to calculate $$\mathrm{d}X_t$$.

$$
	\begin{align*}
		\mathrm{d}X_t & = \left(\dfrac{\partial f}{\partial t} + \mu\left(t, X_t\right)\dfrac{\partial f}{\partial x} + \dfrac{\sigma\left(t, X_t\right)^2}{2}\dfrac{\partial^2 f}{\partial x^2}\right) \mathrm{d}t + \sigma\left(t, X_t\right)\dfrac{\partial f}{\partial x} \mathrm{d}W_t \\
		              & = \left(0 + 0 + \dfrac{1}{2}\cdot 2\cdot 1\right) \mathrm{d}t + 2W_t \mathrm{d}W_t                                                                                                                                                                                  \\
		              & = \mathrm{d}t + 2W_t \mathrm{d}W_t
	\end{align*}
$$

compared to normal differentiation, we have an extra term $$\mathrm{d}t$$ term here. On the other hand,

$$
		\int_0^t W_s\mathrm{d}W_s  = \dfrac{1}{2}W_t^2 - \dfrac{1}{2}t


$$

when we reverse the process.

This shows we can reverse the process of Ito's lemma to solve stochastic differential equation.

If $$f$$ doesn't contain $$t$$, then we can use the following simplyfied form to calculate $$\mathrm{d}f$$ ($$\mu=0, \sigma=1$$).

$$
		\mathrm{d}f = f^\prime(X_t) \mathrm{d}X_t + \dfrac{1}{2} \ f^{\prime\prime}(X_t) \mathrm{d}t
$$

### Example: Geometric Brownian Motion (GBM)

Geometric Brownian Motion is used to model the stock price. It is defined as

$$
		\mathrm{d}S_t = \mu S_t \mathrm{d}t + \sigma S_t \mathrm{d}W_t


$$

In order to solve it, take logarithm transformation, i.e. $$\log S_t$$, then by It\^o's lemma,

$$
		\mathrm{d}\log S_t = \dfrac{1}{S_t} \mathrm{d}S_t - \dfrac{1}{2} \dfrac{1}{S_t^2} \mathrm{d}S_t^2 = \left(\mu - \dfrac{1}{2}\sigma^2\right) \mathrm{d}t + \sigma \mathrm{d}W_t
$$

Integrate both sides, we get the solution

$$
		S_t = S_0 \exp\left(\left(\mu - \dfrac{1}{2}\sigma^2\right)t + \sigma W_t\right)
$$

> The correction term $$\dfrac{1}{2}\sigma^2$$ is called \textit{convexity correction}, which comes from the difference between arithmetic mean and geometric mean.

> We can easily verify whether a process is a martingale by It\^o's lemma. If the process is a martingale, then the drift term should be zero. For example, $$B_t^2$$ is not a martingale, because we have drift term $$- \dfrac{1}{2}\mathrm{d}t$$.

You can also check whether the following processes are martingales or not, $$W_t$$ standards for standard Brownian motion.

1. $$W_t^3$$,
2. $$\dfrac{1}{W_t}$$,
3. $$\log W_t$$,
4. $$W_t^2 - t$$,

All of them are not martingales except the last one.
