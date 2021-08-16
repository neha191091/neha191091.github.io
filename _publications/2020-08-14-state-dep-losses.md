---
title: "Learning State-Dependent Losses for Inverse Dynamics Learning"
collection: publications
permalink: /publication/2020-08-14-state-dep-losses
excerpt: 'In this work, we propose to apply meta-learning to learn structured, state-dependent loss functions during a meta-training phase. This allows us to quickly adapt the model to changes in dynamics'
date: 2020-08-14
venue: 'IROS'
paperurl: 'https://ieeexplore.ieee.org/document/9341701'
citation: 'K. Morse, N. Das, Y. Lin, A. S. Wang, A. Rai and F. Meier, "Learning State-Dependent Losses for Inverse Dynamics Learning," <i>2020 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)</i>'
---
*Abstract*

Being able to quickly adapt to changes in dynamics is paramount in model-based control for object manipulation tasks. In order to influence fast adaptation of the inverse dynamics model's parameters, data efficiency is crucial. Given observed data, a key element to how an optimizer updates model parameters is the loss function. In this work, we propose to apply meta-learning to learn structured, state-dependent loss functions during a meta-training phase. We then replace standard losses with our learned losses during online adaptation tasks. We evaluate our proposed approach on inverse dynamics learning tasks, both in simulation and on real hardware data. In both settings, the structured and state-dependent learned losses improve online adaptation speed, when compared to standard, state-independent loss functions.
