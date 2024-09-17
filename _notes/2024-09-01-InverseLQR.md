---
title: 'Blog Post number 1'
date: 2024-09-01
permalink: /notes/2024/09/InverseLQR/
tags:
  - IOC/IRL
  - LQR
---

# IOC LQR

## Dynamics
Given a linear system of discrete dynamics:
$\boldsymbol{x}_{t+1}= \bold{A}_t\boldsymbol{x}_t + \bold{B}_t\boldsymbol{u}_t$
where:
$\boldsymbol{x}_t\in\mathbb{R}^{n}$ is the state, 
$\boldsymbol{u}_t\in\mathbb{R}^{m}$, is the action
$\bold{A}_t\in\mathbb{R}^{n\times n}$ is the state-transition matrix
$\bold{B}_t\in\mathbb{R}^{n\times m}$ is the input-transition matrix

## Finite Horizon Cost

### Instantaneous Cost
$C(\boldsymbol{x}_t, \boldsymbol{u}_t)= \boldsymbol{x}_t^T\bold{Q}\boldsymbol{x}_t + \boldsymbol{u}_t^T\bold{Q}\boldsymbol{u}_t$

### Cumulative cost
$J(\boldsymbol{x}_{0:T}, \boldsymbol{u}_{0:T-1})= \boldsymbol{x}_T^T\bold{Q}\boldsymbol{x}_T+\sum_{t=0}^{T-1}\big[\boldsymbol{x}_t^T\bold{Q}\boldsymbol{x}_t + \boldsymbol{u}_t^T\bold{R}\boldsymbol{u}_t\big]$
where $\bold{Q}\geq\bold{0}; \bold{R}>0$

### Cost-to-go
$V^*(\boldsymbol{x}_t)=\min_{\boldsymbol{u}_{t:T}}\sum_t^T \Big[\boldsymbol{x}_t^T\bold{Q}\boldsymbol{x}_t + \boldsymbol{u}_t^T\bold{R}\boldsymbol{u}_t\Big]$
$\qquad\quad=\min_{\boldsymbol{u}_t}\Big[ \boldsymbol{x}_t^T\bold{Q}\boldsymbol{x}_t + \boldsymbol{u}_t^T\bold{R}\boldsymbol{u}_t+V^*(\boldsymbol{x}_{t+1})\Big]$ 

## Feedback Law and Algebraic Ricatti
### Feedback Law 
***
$\boldsymbol{u}^*_t=-(\bold{R} + \bold{B}^T_t\bold{P}_{t+1}\bold{B}_t)^{-1}\bold{B}^T_t\bold{P}_{t+1}\bold{A}_t\boldsymbol{x}_t$
***

### Algebraic Ricatti Equation
***
$\bold{P}_t = \bold{Q}+ \bold{A}^T\bold{P}_{t+1}\bold{A} -\bold{A}^T_{t}\bold{P}_{t+1}\bold{B}_t(\bold{R} + \bold{B}^T_t\bold{P}_{t+1}\bold{B}_t)^{-1}\bold{B}^T_t\bold{P}_{t+1}\bold{A}_t$
***

## PMP
Let $H_t(\boldsymbol{x}_t, \boldsymbol{u}_t, \boldsymbol{\lambda}_{t+1})=\frac{1}{2}\boldsymbol{x}_t^T\bold{Q}\boldsymbol{x}_t+\frac{1}{2}\boldsymbol{u}_t^T\bold{R}\boldsymbol{u}_t + \boldsymbol{\lambda}_{t+1}^T(\bold{A}\boldsymbol{x}_t+\bold{B}\boldsymbol{u}_t)$ Given that the trajectory $\{\boldsymbol{x}^*_t\}_{t=0}^T$ minimizes the cumulative cost $J$, the following are satisfied: 
1. $\boldsymbol{x}^*_{t+1}=\bold{A}\boldsymbol{x}^*_t + \bold{B}\boldsymbol{u}^*_t$$\quad\dots\quad (1)$
2. $\nabla_{\boldsymbol{u}_t}H_t(\boldsymbol{x}^*_t, \boldsymbol{u}^*_t, \boldsymbol{\lambda}_{t+1})=0$
$\implies \bold{R}\boldsymbol{u}^*_t + \bold{B}^T\boldsymbol{\lambda}_{t+1}=0$$\quad\dots\quad (2)$
3. $\nabla_{\boldsymbol{x}_t}H_t(\boldsymbol{x}^*_t, \boldsymbol{u}^*_t, \boldsymbol{\lambda}_{t+1})=\boldsymbol{\lambda}_t$
$\implies \bold{Q}\boldsymbol{x}^*_t + \bold{A}^T\boldsymbol{\lambda}_{t+1}=\boldsymbol{\lambda}_{t}$$\quad\dots\quad (3)$

Assuming $\bold{R}=\bold{I}$, we have:
$\boldsymbol{u}^*_t = -\bold{B}^T\boldsymbol{\lambda}_{t+1}$$\quad\dots\quad(4)$
(4) into (1) gives us:
$\boldsymbol{x}^*_{t+1}=\bold{A}\boldsymbol{x}^*_t - \bold{B}\bold{B}^T\boldsymbol{\lambda}_{t+1}$$\quad\dots\quad(5)$
$\implies\bold{B}\bold{B}^T\boldsymbol{\lambda}_{t+1}=\bold{A}\boldsymbol{x}^*_{t}-\boldsymbol{x}^*_{t+1}$
$\implies\boldsymbol{\lambda}_{t+1}=(\bold{B}\bold{B}^T)^{-1}(\bold{A}\boldsymbol{x}^*_{t}-\boldsymbol{x}^*_{t+1})$$\quad\dots\quad(6)$

### Exact Solution Algorithm (?)

1. Find $\boldsymbol{\lambda}_t=(\bold{B}\bold{B}^T)^{-1}(\bold{A}\boldsymbol{x}^*_{t-1}-\boldsymbol{x}^*_{t}); t=1, \dots, T$
2. Calculate $\boldsymbol{\gamma}_t=\boldsymbol{\lambda}_{t}-\bold{A}^T\boldsymbol{\lambda}_{t+1}; t=1, \dots, T$
3. $\bold{Q}\boldsymbol{x}^*_t=\boldsymbol{\gamma}_t$
$\implies\bold{Q}\boldsymbol{X}^*=\boldsymbol{\Gamma}$
$\implies\bold{Q}=\boldsymbol{\Gamma}\underbrace{{\boldsymbol{X}^*}^{T}(\boldsymbol{X}^*{\boldsymbol{X}^*}^{T})^{-1}}_{Moore-penrose\ inverse}$,  
where 
$\bold{X}^*=[\boldsymbol{x}^*_1, \dots, \boldsymbol{x}^*_T]$,
$\bold{\Gamma}=[\boldsymbol{\gamma}_1, \dots, \boldsymbol{\gamma}_T]$

### Soft IOC Solution

Assuming $\mathcal{H}\equiv\{0\leq t<T: \boldsymbol{u}_t \in \text{int}\ \mathcal{U}\}$. 
the soft IOC solution is given by:

$\inf_{\boldsymbol{\theta},\boldsymbol{\lambda}_{0,T}} \sum_{t_k\in\mathcal{H}}||\nabla_{\boldsymbol{u}_t}H_t(\boldsymbol{x}^*_t,\boldsymbol{u}^*_t,\boldsymbol{\lambda}_{t+1},\boldsymbol{\theta})||^2 + \sum_0^{T-1}||\boldsymbol{\lambda}_t-\nabla_{\boldsymbol{x}_t}H_t(\boldsymbol{x}^*_t, \boldsymbol{u}^*_t,\boldsymbol{\lambda}_{t+1},\boldsymbol{\theta})||^2+||\boldsymbol{\lambda}_T-\nabla_{\boldsymbol{x}_T}F(\boldsymbol{x}^*_T)||^2$
$=\inf_{\bold{Q},\boldsymbol{\lambda}_{0,T}} \sum_{t_k\in\mathcal{H}}||\boldsymbol{u}^*_t + \bold{B}^T\boldsymbol{\lambda}_{t+1}||^2 + \sum_0^{T-1}||\boldsymbol{\lambda}_t-\bold{Q}\boldsymbol{x}^*_t - \bold{A}^T\boldsymbol{\lambda}_{t+1}||^2+||\boldsymbol{\lambda}_T-\bold{Q}\boldsymbol{x}^*_T||^2$

## Finite Horizon OCP with Constraints on state

To be done ...

