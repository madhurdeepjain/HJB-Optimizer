# HJB-Optimizer

This is an implementation of the research paper "HJB-Equation-Based Optimal Learning Scheme
for Neural Networks With Applications
in Brain–Computer Interface" by Tharun et. al. Paper can be found [here](https://ieeexplore.ieee.org/document/8437157).

HJB Optimizer can also be used for applications other than BCI. The notebook conatins an example of it being used for training on MNIST digits dataset.

Within this scheme, a neural network is modeled as a control system. For training the FFNN (Feed Forward Neural Network), the weight update problem can be cast as a control problem with output error **e**(t) as the state of the dynamical system and weight updates **u**(t) as control inputs.

Then HJB Optimal Learning framework is used to derive weight update as follows:

![\mathbf{u}^{*}(t) = \frac{\sqrt{2\mathbf{P}(\mathbf{e}(t))}}{||\mathbf{J}^{T}\mathbf{e}(t)||} \mathbf{R}^{-\frac{1}{2}} \mathbf{J}^{T}\mathbf{e}(t)](https://latex.codecogs.com/gif.latex?\mathbf{u}^{*}(t)&space;=&space;\frac{\sqrt{2\mathbf{P}(\mathbf{e}(t))}}{||\mathbf{J}^{T}\mathbf{e}(t)||}&space;\mathbf{R}^{-\frac{1}{2}}&space;\mathbf{J}^{T}\mathbf{e}(t))

This update can then be used within a standard optimizer such as Adagrad.

![\mathbf{\hat{w}}(t+1) = \mathbf{\hat{w}}(t) + \frac{\eta}{\sqrt{\sum_{t'=0}^{t} ||\mathbf{u}(t')||^2}} \mathbf{u}(t)](https://latex.codecogs.com/gif.latex?\mathbf{\hat{w}}(t&plus;1)&space;=&space;\mathbf{\hat{w}}(t)&space;&plus;&space;\frac{\eta}{\sqrt{\sum_{t'=0}^{t}&space;||\mathbf{u}(t')||^2}}&space;\mathbf{u}(t))

HJB-Optimizer enjoys both faster convergence and better accuracy.
