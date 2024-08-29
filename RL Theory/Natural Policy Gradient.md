*Kakade, S. M. (2001). VancouverBritish Columbia, Canada, 1531–1538.A Natural Policy GradientConference on Neural Information Processing Systems (NIPS) December 3-8.*

**Exact Gradient**: $$\nabla \eta(\theta)=\sum_{s,a}{\rho(s)\nabla\pi(a|s,\theta)Q^\pi(s,a)}$$
The steepest descent is defined as the vector $d\theta$ that minimizes $\eta(\theta + d\theta)$ while keeping $|d\theta|^2 := d\theta^TGd\theta$ under a certain small constant. In the case $G = I$, the steepest descent is the exact gradient.

**Natural Gradient**:
We define the Natural Policy Gradient as the steepest descent when the metric is based on the Fisher information matrix: $$F(\theta):=\mathbb{E_{\rho^\pi(s)}}[F_s(\theta)]=\mathbb{E_{\rho^\pi(s)}}[\mathbb{E}_{\pi(a|s,\theta)}[(\frac{\partial \log\pi(a|s,\theta)}{\partial \theta})^{T}(\frac{\partial \log\pi(a|s,\theta)}{\partial \theta})]]$$