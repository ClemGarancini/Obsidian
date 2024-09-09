*Yuankun Jiang , Chenglin Li, Wenrui Dai, Junni Zou, and Hongkai Xiong*

**Idea:**  DR induce high variance -> the paper proposes a Variance Reduced Domain Randomization (VRDR) baseline to address this problem. 
Dividing space of environments into subspace -> baseline is state/subspace-dependent.

**Contribution:**
* Theoretical optimal **state/environment-dependent** baseline
* Criterion for **state/subspace-dependent** baseline construction (environment-dependent baseline is not doable in pratic)
* VRDR:
![[Capture d’écran 2024-09-06 à 11.48.20.png]]

**Theoretical ideas:**
* Adding an action-independent baseline do not add bias to the gradient estimate
* The convergence is dominated by the variance of gradient estimate, thus reducing the variance of gradient estimate improve the convergence.

**Optimal state/environment-dependent baseline:**
$$b^*(s,p)=\frac{\mathbb{E}_\pi[G(a,s)Q_\pi(s,a,p)]}{\mathbb{E}_\pi[G(a,s)]}$$ where $G(a,s) = \nabla_\theta\log \pi_\theta(a|s)^T\nabla_\theta\log \pi_\theta(a|s)$.

* Need to maintain a baseline for each environment -> hard