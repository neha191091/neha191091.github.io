---
title: "Reimplementation of Importance Weighted Autoencoders"
collection: projects
permalink: /projects/IWAE
type: "Practical Project"
venue: "Chair of Robotics and Embedded Systems, TUM"
location: "Munich"
code: https://github.com/neha191091/IWAE
poster: http://neha191091.github.io/files/IWAE.pdf
---

Importance Weighted Autoencoders are a variant of Variational Autoencoders with 
a more powerful posterior. The Variational Autoencoder is a generative modelling technique
that assumes an underlying latent structure to the data x. To successfully generate samples
from the same distribution x was generated from, one must have a model of the data that
maximizes p(x). However p(x) is the integral over p(x|z)p(z), which is intractable. Therefore,
we instead maximize the lower bound by assuming a variational posterior (since we cannot tractably
compute the true one or sample from it.)

Unfortunately, VAE assumes the variational posterior form to be factorial which restricts the
capacity of the generative model to only simple distributions with factorial true posterior. 
IWAE overcomes this assumption by sampling multiple times from the approximate posterior to get 
a tighter lower bound on p(x). The variational posterior provably approaches the true posterior
in the limit of infinite samples.

This work re-implements IWAE and VAE. The results and comparisons between these two models 
are laid out in a poster that can be downloaded by following the link below.