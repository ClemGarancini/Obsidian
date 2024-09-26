
Mehta, B., Diaz, M., Golemo, F., Pal, C.J. &amp; Paull, L.. (2020). Active Domain Randomization. <i>Proceedings of the Conference on Robot Learning</i>, in <i>Proceedings of Machine Learning Research</i> 100:1162-1176 Available from https://proceedings.mlr.press/v100/mehta20a.html.

Inspired by Bayesian Optimization (BO)

≠ with BO: Training the policy renders the optimization objective (search of parameters for the next training env) non-stationary

* Learn policies $\mu_\phi$ as particles (Stein Variational Policy Gradient) to predict environment parameters
* Use a discriminator (NN) to estimate the probability of a trajectory to come from an informative environment -> define a reward to lead the policy $\mu_\phi$ towards informative environment parameters