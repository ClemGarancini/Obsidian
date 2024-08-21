Graham C. Goodwin, Robert L. Payne, 1977


##### Basic Knowledge
###### Gaussian distribution
* Density function: $p(y)=$
##### Efficient Estimators
###### Cramer-Rao Inequality (p.6)
For any unbiased estimator $g(Y)$ of $\theta$, we have the inequality:
$$cov\ g \geq M_{\theta}^{-1}$$
Where: 
$$cov\ g = \mathbb{E}_{Y|\theta}[(g(y)-\theta)(g(y)-\theta)^{-1}]$$
and where $M_{\theta}$, known as the *Fisher's information matrix*, is defined by
$$M_{\theta} = \mathbb{E}_{Y|\theta}[(\frac{\partial log\ p(Y|\theta)}{\partial \theta})^{T}(\frac{\partial log\ p(Y|\theta)}{\partial \theta})]$$
###### Efficient Estimator
An unbiased estimator is said to be *efficient* for $\theta$ if its covariance is equal to the Cramer-Rao lower bound $M_\theta$.

###### Theorem
There exist an unbiased efficient estimator for $\theta$ if, and only if, we can express $\frac{\partial log\ p(y|\theta)}{\partial \theta}$ under the form: 
$$[\frac{\partial log\ p(y|\theta)}{\partial \theta}]^T=A(\theta)[g(y)-\theta]$$
##### Statistics
###### Definition
* A *statistic* $s(y)$ is a measurable function of the data (*e.g.* an estimator).
* A *sufficient statistic* $s(y)$ is a statistic such that the conditional probability $p_Y(\cdot |s(y))$ does not depend on $\theta$.
###### Factorization theorem
A statistic $s(y)$ is sufficient for the class $\mathcal{P} = \{p(\cdot,\theta): \theta \in \Theta \}$ if, and only if, we can factorize the likelihood function $p(y|\theta)$ as:
$$p(y|\theta)=f(s(y),\theta)g(y)$$
Where $g(y)$ is not dependant on $\theta$.

##### Hypothesis testing
*Q: Is the given data consistent with the hypothesis about the true state of nature?*
The Neyman-Parson theory answers that question.
###### Definitions
* The *null hypothesis* denoted by $H_0$ is the hypothesis of prime interest.
* The *alternative hypothesis*, denoted by $H_A$ is the complement of $H_0$.
* There are two types of error: 
	* Type I: Reject the null hypothesis when it is actually true.
	* Type II: Accept the null hypothesis when it is actually false.
* $A$ is the set in which we accept the null hypothesis.
* $\bar A$ is the critical region, the complementary of $A$.
* $\alpha = P(\bar A|H_0)$, called the *significance* of the test, is the probability of having the Type I error.
* $\beta = P(A | H_A)$ is the probability of having the Type II error.
* $1-\beta$ is called the *power function* of the test.
###### Theorem
The critical region $\bar A$ for which $\alpha$ is fixed and $1-\beta$ is maximized is given by:
$$\bar A = \{y:\frac{p(y|\theta_1)}{p(y|\theta_0)} \geq k_\alpha\}$$
where $k_\alpha$ is a positive constant chosen such that the fixed value of $\alpha$ is matched.

##### Bayesian Theory Approach
###### Definitions
* $\{d:d \in \mathcal{D}\}$ a *decision space* of possible decisions $d$.
* $\{y:y \in \Omega\}$ a *sample space* of data $y$.
* $\{\theta: \theta \in \Theta\}$ a *parameter space* of possible true states of nature $\theta$.
* $\{\mathcal{e} : \mathcal{e} \in \mathcal{E}\}$ a *family of possible experiments* $\mathcal{e}$.
* $p: \Theta \rightarrow [0;1]$ the *prior* *probability distribution*.
* $p(\cdot|y): \Theta \rightarrow [0;1]$ the *posterior* *probability distribution* given by Bayes' rule: $p(\theta|y)=\frac{p(y|\theta)p(\theta)}{p(y)}$.
* $J:\mathcal{D}\times\Omega\times\Theta\times\mathcal{E} \rightarrow \mathbb{R}$ the *loss function*. $J(d,y,\theta,\mathcal{e})$ represents the cost associated with performing experiment $\mathcal{e}$ and making the decision $d$ when the data is $y$ and the true state of nature is $\theta$.
* $\begin{array}{l} \bar J: \mathcal{D}\times\Omega\times\mathcal{E} \rightarrow \mathbb{R} \\ \hspace{1.4cm} (d, y, \mathcal{e}) \mapsto \mathbb{E}_{\theta|y,\mathcal{e}}[J(d, y, \theta, \mathcal{e})] \end{array}$ the *posterior loss* or *risk*.
* $\begin{array}{l} \hat J: \mathcal{D}\times\mathcal{E} \rightarrow \mathbb{R} \\ \hspace{1cm} (d, e) \mapsto \mathbb{E}_{Y|\mathcal{e}}[\bar J(d, y, e)] \end{array}$ the *expected posterior loss*.

###### Optimal decision making
The *optimal decision rule* is a function $d^*: \Omega\times\mathcal{E}\rightarrow\mathcal{D}$ that minimizes the posterior loss, *i.e.* $$\bar J(d^*(y,e), y, e)\leq\bar J(\tilde d(y,e), y, e)$$  for all other functions $\tilde d: \Omega\times\mathcal{E}\rightarrow\mathcal{D}$.

###### Optimal experiment design
The *optimal experiment design* is a function $e^*: \mathcal{D}\rightarrow\mathcal{E}$ which minimizes the expected posterior loss *i.e.* $$\hat J(d, e^*(d))\leq \hat J(d, \tilde e(d))$$ for all other $\tilde e : \mathcal{D}\rightarrow\mathcal{E}$.
###### Joint optimal decision rule and experiment design
The *joint optimal decision rule and experiment design* $d^{**}$ and $e^{**}$ may be defined by: $e^{**}$ minimizes $$\mathbb{E}_{Y|\mathcal{e}}[\bar J(d^*(y,e), y, e)]$$and $d^{**}$ is given by $$d^{**}(y) = d^*(y,e^{**})$$
##### Information Theory Approach
Shannon's theory
###### Definitions
- The *entropy* of a random variable $X$ is defined to be $H_X=-\mathbb{E}_X[\log\ p(X)]$.
- The *Lindley's average amount of information* provided by an experiment $e$ with data $y$ and parameters $\theta$ is defined to be $$\mathcal{J}(e)=H_\theta - \mathbb{E}_y[H_{\theta | y}]$$Where $$H_\theta = -\mathbb{E}_\theta[\log p(\theta)],\hspace{1cm}H_{\theta | y} = -\mathbb{E}_{\theta | y}[\log p(\theta|y)]$$
###### Results
* In the Gaussian case, the entropy is given by: $$H_X = c + \frac{1}{2}\log \det \Sigma$$ Where $\Sigma$ is the covariance matrix.
* Gaussian distribution provides the highest entropy.
* Entropy is related to the dispersion (covariance) of the density variance hence the uncertainty.
* $\mathcal{J}(e)$ can be seen to be the difference between the prior uncertainty and the expected posterior uncertainty.

##### Commonly Used Estimators
###### Definitions
* Given a function $f: \mathbb{R}^N\times\mathbb{R}^p\rightarrow\mathbb{R}^N$, then a *least squares estimator* $g^*(y)$ is defined as follows: $$||f(y,g^*)||_Q\leq||f(y,\tilde g)||_Q$$ for any other function $\tilde g$ where $y \in \mathbb{R}^N$ are the given data and $||x||_Q = x^TQx,\hspace{0.5cm} Q$ positive definite.
* Given a parametric family $\mathcal{P}=\{p(\cdot|\theta):\theta \in \Theta\}$ of probability densities on a sample space $\Omega$, the *maximum likelihood estimator* (MLE), $g^*: \Omega \rightarrow \Theta$ is defined by: $$p(y|g^*)\geq p(y|\tilde g)$$ where $\tilde g$ is any other function.
* A *maximum a posteriori estimate* (MAP) is the mode of the posterior distribution $p(\theta|y)$.
  