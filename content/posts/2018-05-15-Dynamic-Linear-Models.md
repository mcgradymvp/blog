---
title: "Dynamic Linear Models"
date: 2018-05-15
tags: ["Time Series"]
layout: single
draft: true
---
### Dynamic linear models and examples
<div>$$\begin{eqnarray}\label{dlm}Y\_t = F\_t\theta\_t + v\_t, \qquad v\_t\sim\mathcal{N}\_m(0, V\_t) \newline
\theta\_t = G\_t\theta\_{t-1} + w\_t, \qquad w\_t\sim\mathcal{N}\_p(0, W\_t)\end{eqnarray}
$$</div>
where $F\_t$ is observation matrix and $G\_t$ is transition matrix. $v\_t$ and $w\_t$ are two independent sequences of independent Gaussian random vectors with zero mean and variance matrix $V\_t$ and $W\_t$ respectively.

One simple example of DLM is _**random walk plus noise model**_, or _**local level model**_. By setting $F\_t=G\_t=1$. Formally, the model can be expressed as
<div>$$Y\_t = \mu\_t + v\_t, \qquad v\_t\sim\mathcal{N}(0, V)$$</div>
<div>$$\mu\_t = \mu\_{t-1} + w\_t, \qquad w\_t\sim\mathcal{N}(0, W)$$</div>
This random walk plus noise model is suitable for time series with no significant trend of seasonality.

Another example of DLM is _**linear growth model**_, or _**local linear trend model**_. This model has the same observation equation as local level model, but adds a time-varying slope for $\mu\_t$. Here, we set
<div>$$\begin{equation}\theta\_t=
\begin{bmatrix}\mu\_t\\\ \beta\_t
\end{bmatrix},\quad G=\begin{bmatrix}1, 1\\\ 0, 1\end{bmatrix},\quad W=\begin{bmatrix}\sigma\_{\mu}^2, 0\\\ 0, \sigma\_{\beta}^2\end{bmatrix},\quad F=\begin{bmatrix}1, 0\end{bmatrix}\end{equation}
$$</div>
Followings are the formal equations for local linear trend model.
<div>$$Y\_t = \mu\_t + v\_t, \qquad v\_t\sim\mathcal{N}(0, V)$$</div>
<div>$$\mu\_t = \mu\_{t-1} + \beta\_{t-1} + w\_{t, 1}, \qquad w\_{t, 1}\sim\mathcal{N}(0, \sigma\_{\mu}^2)$$</div>
<div>$$\beta\_t = \beta\_{t-1} + w\_{t, 2}, \qquad w\_{t, 2}\sim\mathcal{N}(0, \sigma\_{\beta}^2)$$</div>
In above examples, matrices $G\_t$ and $F\_t$ and covariance matrices $V\_t$ and $W\_t$ are constant, and those models are all time-invariant models. We will discuss other examples in future posts.

### Filtering, smoothing, and forecasting
Since we assume we know the relationship between successive states, and that between states and observations, $i.e.$ the model is known. Although, in general application, we are facing difficulties specifying the exact form of the model, which requires both knowledge from statistics and specific experts familiar with the problems, here we consider the model being given, where the densities $\pi(y\_t|\theta\_t)$ and $\pi(\theta\_t|\theta\_{t-1})$ are known.

In a time series problem, data is collected sequentially, and filtering problem is to estimate the current value of state vector, based on the data we collected till now. Mathematically speaking, we wish to compute the conditional probability $\pi(\theta\_t|y\_{1:t})$.

Smoothing is a procedure to understand the past data. We are estimating a sequence of state vector, using all the data
