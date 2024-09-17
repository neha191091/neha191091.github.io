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
Given a linear system of discrete dynamics:
$\boldsymbol{x}_{t+1}= \bold{A}_t\boldsymbol{x}_t + \bold{B}_t\boldsymbol{u}_t$
where:
$\boldsymbol{x}_t\in\mathbb{R}^{n}$ is the state, 
$\boldsymbol{u}_t\in\mathbb{R}^{m}$, is the action
$\bold{A}_t\in\mathbb{R}^{n\times n}$ is the state-transition matrix
$\bold{B}_t\in\mathbb{R}^{n\times m}$ is the input-transition matrix