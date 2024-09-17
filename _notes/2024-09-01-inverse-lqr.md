---
title: 'Inverse LQR'
date: 2024-09-01
permalink: /notes/2024/09/inverselqr
tags:
  - IOC
  - IRL
  - LQR
excerpt: Given a trajectory of states and actions $\{\mathbf{x}^\*\_{0:T},\mathbf{u}^\*\_{0:T-1}\}$ that is solution of Linear Quadratic Regulator optimization where $\mathbf{R}=\mathbf{I}$<br>

from the following system of linear discrete dynamics:<br>
$\mathbf{x}_{t+1}= \mathbf{A}_t\mathbf{x}_t + \mathbf{B}_t\mathbf{u}_t$

where:<br>
$\mathbf{x}_t\in\mathbb{R}^{n}$ is the state,<br> 
$\mathbf{u}_t\in\mathbb{R}^{m}$, is the action,<br>
$\mathbf{A}_t\in\mathbb{R}^{n\times n}$ is the state-transition matrix,<br>
$\mathbf{B}_t\in\mathbb{R}^{n\times m}$ is the input-transition matrix

the problem is to find $\mathbf{Q}^*$ that generates the trajectory
---

Problem Statement
-----
Given a trajectory of states and actions $\{\mathbf{x}^\*\_{0:T},\mathbf{u}^\*\_{0:T-1}\}$ that is solution of Linear Quadratic Regulator optimization where $\mathbf{R}=\mathbf{I}$<br>

from the following system of linear discrete dynamics:<br>
$\mathbf{x}_{t+1}= \mathbf{A}_t\mathbf{x}_t + \mathbf{B}_t\mathbf{u}_t$

where:<br>
$\mathbf{x}_t\in\mathbb{R}^{n}$ is the state,<br> 
$\mathbf{u}_t\in\mathbb{R}^{m}$, is the action,<br>
$\mathbf{A}_t\in\mathbb{R}^{n\times n}$ is the state-transition matrix,<br>
$\mathbf{B}_t\in\mathbb{R}^{n\times m}$ is the input-transition matrix

the problem is to find $\mathbf{Q}^*$ that generates the trajectory

Finite Horizon Cost
-----
For the cost parameters $\mathbf{Q}, \mathbf{R}$, the following can be stated:

### Instantaneous Cost<br>
$C(\mathbf{x}_t, \mathbf{u}_t)= \mathbf{x}_t^T\mathbf{Q}\mathbf{x}_t + \mathbf{u}_t^T\mathbf{R}\mathbf{u}_t$

### Cumulative cost<br>
$J(\mathbf{x}\_{0:T},\mathbf{u}\_{0:T-1})=\mathbf{x}\_T^T\mathbf{Q}\mathbf{x}\_T+\sum\_{t=0}^{T-1}\big[\mathbf{x}\_t^T\mathbf{Q}\mathbf{x}\_t + \mathbf{u}\_t^T\mathbf{R}\mathbf{u}\_t\big]$
where $\mathbf{Q}\geq\mathbf{0}; \mathbf{R}>0$

### Cost-to-go<br>
$V^*(\mathbf{x}\_t)=\min\_{\mathbf{u}\_{t:T}}\sum\_t^T \Big[\mathbf{x}\_t^T\mathbf{Q}\mathbf{x}\_t + \mathbf{u}\_t^T\mathbf{R}\mathbf{u}\_t\Big]$

$\qquad\quad=\min\_{\mathbf{u}\_t}\Big[\mathbf{x}\_t^T\mathbf{Q}\mathbf{x}\_t + \mathbf{u}\_t^T\mathbf{R}\mathbf{u}\_t+V^*(\mathbf{x}\_{t+1})\Big]$ 

Feedback Law 
-----
For the cost parameters $\mathbf{Q}, \mathbf{R}$, the feedback law is given as:

$\mathbf{u}^*\_t=-(\mathbf{R} + \mathbf{B}^T_t\mathbf{P}\_{t+1}\mathbf{B}\_t)^{-1}\mathbf{B}^T\_t\mathbf{P}\_{t+1}\mathbf{A}\_t\mathbf{x}\_t$

where<br>
$\mathbf{P}\_t = \mathbf{Q}+ \mathbf{A}^T\mathbf{P}\_{t+1}\mathbf{A} -\mathbf{A}^T\_{t}\mathbf{P}\_{t+1}\mathbf{B}\_t(\mathbf{R} + \mathbf{B}^T\_t\mathbf{P}\_{t+1}\mathbf{B}\_t)^{-1}\mathbf{B}^T\_t\mathbf{P}\_{t+1}\mathbf{A}_t \qquad\dots$ **Algebraic Ricatti Equation**


Applying Pontryagin's Minimum Principle (PMP)
-----
Let $H_t(\mathbf{x}\_t, \mathbf{u}\_t, \mathbf{\lambda}\_{t+1})=\frac{1}{2}\mathbf{x}\_t^T\mathbf{Q}\mathbf{x}\_t+\frac{1}{2}\mathbf{u}\_t^T\mathbf{R}\mathbf{u}\_t + \mathbf{\lambda}\_{t+1}^T(\mathbf{A}\mathbf{x}\_t+\mathbf{B}\mathbf{u}\_t)$ 

Given that the trajectory $\{\mathbf{x}^*\_t\}_{t=0}^T$ minimizes the cumulative cost $J$, the following are satisfied: 

1. $\mathbf{x}^\*\_{t+1}=\mathbf{A}\mathbf{x}^\*\_t + \mathbf{B}\mathbf{u}^\*\_t\quad\quad\quad\dots\quad (1)$
2. $\nabla\_{\mathbf{u}\_t}H\_t(\mathbf{x}^\*\_t, \mathbf{u}^\*\_t, \mathbf{\lambda}_{t+1})=0$<br>
$\implies \mathbf{R}\mathbf{u}^\*\_t + \mathbf{B}^T\mathbf{\lambda}\_{t+1}=0\quad\dots\quad (2)$
3. $\nabla\_{\mathbf{x}\_t}H\_t(\mathbf{x}^\*\_t, \mathbf{u}^\*\_t, \mathbf{\lambda}\_{t+1})=\mathbf{\lambda}\_t$<br>
$\implies \mathbf{Q}\mathbf{x}^\*\_t + \mathbf{A}^T\mathbf{\lambda}\_{t+1}=\mathbf{\lambda}\_{t}\quad\dots\quad (3)$

Assuming $\mathbf{R}=\mathbf{I}$, we have:<br>
$\mathbf{u}^\*\_t = -\mathbf{B}^T\mathbf{\lambda}\_{t+1}\quad\qquad\qquad\qquad\qquad\quad\dots\quad(4)$<br>
(4) into (1) gives us:<br>
$\mathbf{x}^\*\_{t+1}=\mathbf{A}\mathbf{x}^\*\_t - \mathbf{B}\mathbf{B}^T\mathbf{\lambda}\_{t+1}\quad\qquad\qquad\quad\dots\quad(5)$<br>
$\implies\mathbf{B}\mathbf{B}^T\mathbf{\lambda}\_{t+1}=\mathbf{A}\mathbf{x}^\*\_{t}-\mathbf{x}^\*\_{t+1}$<br>
$\implies\mathbf{\lambda}\_{t+1}=(\mathbf{B}\mathbf{B}^T)^{-1}(\mathbf{A}\mathbf{x}^\*\_{t}-\mathbf{x}^\*\_{t+1})\quad\dots\quad(6)$

Solution
-----

### Algorithm for exact solution

1. Find $\mathbf{\lambda}\_t=(\mathbf{B}\mathbf{B}^T)^{-1}(\mathbf{A}\mathbf{x}^\*\_{t-1}-\mathbf{x}^\*\_{t}); \qquad t=1, \dots, T$
2. Calculate $\mathbf{\gamma}\_t=\mathbf{\lambda}\_{t}-\mathbf{A}^T\mathbf{\lambda}\_{t+1}; \qquad\qquad t=1, \dots, T$
3. $\mathbf{Q}\mathbf{x}^\*\_t=\mathbf{\gamma}\_t$<br>
$\implies\mathbf{Q}\mathbf{X}^\*=\mathbf{\Gamma}$<br>
$\implies\mathbf{Q}=\mathbf{\Gamma}{\mathbf{X}^\*}^{T}(\mathbf{X}^\*{\mathbf{X}^\*}^{T})^{-1}$,  
where 
$\mathbf{X}^\*=[\mathbf{x}^\*\_1, \dots, \mathbf{x}^\*\_T]$,<br>
$\mathbf{\Gamma}=[\mathbf{\gamma}\_1, \dots, \mathbf{\gamma}\_T]$

### Soft IOC Solution

Assuming $\mathcal{H}\equiv\{0\leq t<T: \mathbf{u}\_t \in \text{int}\ \mathcal{U}\}$. <br>
the soft IOC solution is given by:

$\inf\_{\mathbf{\theta},\mathbf{\lambda}\_{0,T}} \sum\_{t\_k\in\mathcal{H}}\Vert\nabla\_{\mathbf{u}\_t}H\_t(\mathbf{x}^\*\_t,\mathbf{u}^\*\_t,\mathbf{\lambda}\_{t+1},\mathbf{\theta})\Vert^2 + \sum\_0^{T-1}\Vert\mathbf{\lambda}\_t-\nabla\_{\mathbf{x}\_t}H\_t(\mathbf{x}^\*\_t, \mathbf{u}^\*\_t,\mathbf{\lambda}\_{t+1},\mathbf{\theta})\Vert^2+\Vert\mathbf{\lambda}\_T-\nabla\_{\mathbf{x}\_T}F(\mathbf{x}^\*\_T)\Vert^2$<br>
$=\inf\_{\mathbf{Q},\mathbf{\lambda}\_{0,T}} \sum\_{t\_k\in\mathcal{H}}\Vert\mathbf{u}^\*\_t + \mathbf{B}^T\mathbf{\lambda}\_{t+1}\Vert^2 + \sum_0^{T-1}\Vert\mathbf{\lambda}\_t-\mathbf{Q}\mathbf{x}^\*\_t - \mathbf{A}^T\mathbf{\lambda}\_{t+1}\Vert^2+\Vert\mathbf{\lambda}\_T-\mathbf{Q}\mathbf{x}^\*\_T\Vert^2$


