---
title: "Model-Based Inverse Reinforcement Learning from Visual Demonstrations"
collection: publications
permalink: /publication/2021-01-06-model-based-irl
excerpt: 'In this work, we propose to apply meta-learning to learn structured, state-dependent loss functions during a meta-training phase. This allows us to quickly adapt the model to changes in dynamics'
date: 2021-01-06
venue: 'CoRL'
paperurl: 'https://corlconf.github.io/paper_432'
citation: 'N. Das, S. Bechtle, T. Davchev, D. Jayaraman, A. Rai and F. Meier, "Model-Based Inverse Reinforcement Learning from Visual Demonstrations," <i>2020 Conference on Robot Learning (CoRL)</i>'
---
*Abstract*

Scaling model-based inverse reinforcement learning (IRL) to real robotic manipulation tasks with unknown dynamics remains an open problem. The key challenges lie in learning good dynamics models, developing algorithms that scale to high-dimensional state-spaces and being able to learn from both visual and proprioceptive demonstrations. In this work, we present a gradient-based inverse reinforcement learning framework that utilizes a pre-trained visual dynamics model to learn cost functions when given only visual human demonstrations. The learned cost functions are then used to reproduce the demonstrated behavior via visual model predictive control. We evaluate our framework on hardware on two basic object manipulation tasks.
