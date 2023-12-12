# HJB-Optimizer

This is an implementation of the research paper "HJB-Equation-Based Optimal Learning Scheme
for Neural Networks With Applications
in Brain–Computer Interface" by Tharun et. al. Paper can be found [here](https://ieeexplore.ieee.org/document/8437157).

HJB Optimizer can also be used for applications other than BCI. The notebook conatins an example of it being used for training on MNIST digits dataset.

Within this scheme, a neural network is modeled as a control system. For training the FFNN (Feed Forward Neural Network), the weight update problem can be cast as a control problem with output error **e**(t) as the state of the dynamical system and weight updates **u**(t) as control inputs.

Then HJB Optimal Learning framework is used to derive weight update as follows:

$$u^{*}(t) = \frac{\sqrt{2P(e(t))}}{||J^{T}e(t)||} R^{-\frac{1}{2}} J^{T}e(t)$$

This update can then be used within a standard optimizer such as Adagrad.

$$\hat{w}(t+1) = \hat{w}(t) + \frac{\eta}{\sqrt{\Sigma_{t'=0}^{t}||u(t')||^2}}u(t)$$

HJB-Optimizer enjoys both faster convergence and better accuracy.
