---
title: "IAF_Dynamics"
collection: projects
permalink: /projects/IAF_Dynamics
type: "Practical Project"
venue: "Chair of Robotics and Embedded Systems, TUM"
location: "Munich"
code: https://github.com/neha191091/IAF_Dynamics
poster: http://neha191091.github.io/files/IAF_Dynamics.jpg
---

Through this work, we propose the incorporation of Inverse Autoregressive Flows
for determining the state space (latents) in a dynamical system model. 
This reduces the number of samples that need to be obtained in order to approximate 
the posterior distribution (and thus the underlying states/latents for a set of 
observations and controls) from one per time step to one per sequence of observations. 
Our experiments with pendulum-v01, an environment from openai gym confirmed that the 
accuracy with which the observations are generated are close to the state of the art 
for sequence models.


The results from this work, along with its benefits and issues are present in [this](https://github.com/neha191091/human-segmentation) poster.

Find the project [here](https://github.com/neha191091/IAF_Dynamics) on github.