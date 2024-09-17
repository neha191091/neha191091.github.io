---
title: 'Inverse LQR'
date: 2024-09-01
permalink: /notes/2024/09/inverselqr
tags:
  - IOC
  - IRL
  - LQR
---

Dynamics
-----
Given a linear system of discrete dynamics:<br>
$\mathbf{x}_{t+1}= \mathbf{A}_t\mathbf{x}_t + \mathbf{B}_t\mathbf{u}_t$

where:<br>
$\mathbf{x}_t\in\mathbb{R}^{n}$ is the state,<br> 
$\mathbf{u}_t\in\mathbb{R}^{m}$, is the action,<br>
$\mathbf{A}_t\in\mathbb{R}^{n\times n}$ is the state-transition matrix,<br>
$\mathbf{B}_t\in\mathbb{R}^{n\times m}$ is the input-transition matrix

## Finite Horizon Cost

### Instantaneous Cost<br>
$C(\mathbf{x}_t, \mathbf{u}_t)= \mathbf{x}_t^T\mathbf{Q}\mathbf{x}_t + \mathbf{u}_t^T\mathbf{Q}\mathbf{u}_t$

### Cumulative cost<br>
$J(\mathbf{x}_{0:T}, \mathbf{u}_{0:T-1})= \mathbf{x}_T^T\mathbf{Q}\mathbf{x}_T+\sum_{t=0}^{T-1}\big[\mathbf{x}_t^T\mathbf{Q}\mathbf{x}_t + \mathbf{u}_t^T\mathbf{R}\mathbf{u}_t\big]$
where $\mathbf{Q}\geq\mathbf{0}; \mathbf{R}>0$

### Cost-to-go<br>
$V^*(\mathbf{x}_t)=\min_{\mathbf{u}_{t:T}}\sum_t^T \Big[\mathbf{x}_t^T\mathbf{Q}\mathbf{x}_t + \mathbf{u}_t^T\mathbf{R}\mathbf{u}_t\Big]$<br>
$\qquad\quad=\min_{\mathbf{u}_t}\Big[ \mathbf{x}_t^T\mathbf{Q}\mathbf{x}_t + \mathbf{u}_t^T\mathbf{R}\mathbf{u}_t+V^*(\mathbf{x}_{t+1})\Big]$ 



