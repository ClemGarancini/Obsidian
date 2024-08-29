###### Interesting papers:
* Live Repetition Counting (https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://openaccess.thecvf.com/content_iccv_2015/papers/Levy_Live_Repetition_Counting_ICCV_2015_paper.pdf&ved=2ahUKEwi83tHv8IOIAxWkElkFHVdSBhQQFnoECBsQAQ&usg=AOvVaw37fTPgliO2PNUduuBYAuK7): Model to recognise cycles in videos of human trained on randomly generated cycling pattern!!!!
* RL^2: Fast RL via Slow RL: Meta-RL
* SimOpt: Closing the Sim-to-Real Loop:
Adapting Simulation Randomization with Real World Experience.
* Active Domain Randomization

More data = better
Pre trained is unnecessary if you have enough data
System ID is still important

#### Gap in Physic
What can you randomise:
* Physical parameter
* Noise applied to policy inputs
* Sensor dropout (failure)
* Physics discretization timestep
* Backlash??
* Random forces applied

#### Why does it works?
* Covering distribution
	* High-dim space => massive amount of data needed to cover real data distribution
	* Some effects are not modeled => impossible to cover everything
![[Capture d’écran 2024-08-20 à 11.51.29.png]]
* DR is a way to telling the model **what to ignore**
* DR is **meta-learning**. 


# Domain Randomization for Robotic Review
*Robot Learning From Randomized Simulations: A Review. Fabio Muratore, Fabio Ramos, Greg Turk, Wenhao Yu, Michael Gienger and Jan Peters*
## Papers
* Adaptive Dynamic Randomization: *Muratore, F., Eilers, C., Gienger, M., and Peters, J. (2021a). Data-efficient Domain Randomization with Bayesian Optimization*

## Theory
If we define the expected discounted return as: $$J(\theta, \mathcal{E})=\mathbb{E}_{s_0 \textasciitilde \mu_\mathcal{E}(s_0), s_{t+1}\textasciitilde \mathcal{P}(s_t, a_t), a_t \textasciitilde \pi_\theta(a_t|s_t)}[\sum_{t=0}^{T-1}{\gamma^tr_\mathcal{E}(s_t, a_t)}|\theta, \mathcal{E}]$$ Where $\mathcal{E}$ represent the domain (environment) parameters.

In DR, the goal is to maximize the expected discounted return for a distribution of domain parameters: $$J(\theta)=\mathbb{E}_{\mathcal{E}\textasciitilde p(\mathcal{E})}[J(\theta,\mathcal{E})]$$
### Measurement of the Reality Gap
* *Estimated STR (Sim2Real) Disparity*: $$\tilde D(c) = \frac{1}{N} \sum_{c_i \in C_T}{\frac{D(c_i)}{b\_dist(c, c_i)}}$$Where $D$ is the real STR Disparity (comparison of trajectories in Sim and IRL), $C_T$ are the models already tested IRL, $b\_dist$ is the *behavioural distance* between two models (distance between parameter vectors). **Q: Why compare the model with the ones that are very different?**
* *Simulation Optimization Bias (SOB)*: Standard deviation between the true optimum $\theta^*$ and the sample-based optimum $\theta^*_n$, $n$ represents the randomized domains. $$b(\tilde J_n(\theta_n^*)) = \mathbb{E}_\mathcal{E}[\max_{\tilde \theta \in \Theta} \tilde J_n(\tilde \theta)] - \max_{\tilde \theta \in \Theta} \mathbb{E}_\mathcal{E}[J(\tilde \theta, \mathcal{E})]  $$
* Simulator accuracy: accumulated mean-squared error between true ground position and simulator prediction.
* Probabilistic Dynamics Model??
* *SRCC (Sim2Real Correlation Coefficient)*: correlation of performance between Simu and IRL for given policy => Need real world rollouts compared to SOB. Restriction to linear correlation (relevant?)
## Relative Fields
### Curriculum Learning (CL)
Easy -> Hard tasks.
Link: task is a part of the domain parameterization. Updating domain parameters <=> Updating task.
Challenges:
* Difficulty of domain parameterization implicit. 
* CL does not find robust solution to model uncertainty.
* CL needs target distribution ??
### Meta-Learning
### Transfer Learning
**Idea**: Source domain -> Target domain <=> Simu -> IRL
Domain Adaptation: ground truth only available in target domain and task is the same. 
Such techniques are usually not adapted for dynamical system as target domain.
### Knowledge Distillation
Learned behaviours of several "teachers" are taught to a "student" in a supervised manner. For S2R, teachers can be policies optimal for specific domains.
### Distributional Robustness
Idea: Robust control aims to design controllers that deal with uncertainties. Hence find the worst-case probabilistic model from the ambiguity set and then use the optimal policy of this worst-case.
### Adaptive Control
Idea: Changing the control at runtime to adapt to change of model (aircraft reaching supersonic speed). ≠ Robust control (AC change control law over time to fit the model whereas RC guarantees no need for control law changement if model stays within certain bounds).

*Model Reference Adaptive Control*?

*Model Identification Adaptive Control*: Online SI, estimate parameter based on prediction error. 

RL ≠ : AC defines parameters' gradient proportional to pred. error while in RL parameters is an input to policy. 

### Simulation-based Inference
Infer simulation parameters from IRL data.

*Likelihood-Free Inference*: no need for assumptions about underlying model.


## Domain Randomization Techniques
### Static Domain Randomization
![[Capture d’écran 2024-08-28 à 14.58.38.png]]Fixed domain parameter distribution

Pros:
- No need for IRL data
- Easier and quicker to implement
Cons:
- Inferior performance of final policy compared to adaptive DR in general


- With / Without IRL Data
- Dynamics / Visuals / Configurations

### Adaptive Domain Randomization
![[Capture d’écran 2024-08-28 à 14.59.05.png]]

Keys: 
- Update of domain parameter distribution
- IRL Data collection
- Trade-Off: Getting data with intermediate policies is hard BUT better than updating solely on source domain data.

Train Policy on various random models + estimate the model parameter from observed rollouts (sim or real?)

Idea: Adapt model parameters by gradient ascent on average return over domains -> Need to do R2S

**Bilevel Optimization**
2 Pbs: 
- Upper problem: Find domain parameter distribution that leads to maximal real-world return.
- Lower problem: Find a policy in the current randomized domain.

Try to generate simulators that are indistinguishable from real world according to a discriminator (?)

## Ideas
**Q: What to randomize?** 
Problem dependent: gust of wind for drones, terrain for ground robot. Start with a small set of parameters to shorten the evaluation of expectation over domains.

**Q: When randomize?** 
*Episodic dynamics randomization*: most common without deep theoretical justification.
*At every timestep*: too costly and rise variance
*Random forces and torques applied at each time step*: Distribution is fixed between two randomization schemes updates.
*Event-based randomization??*

**Q: How to randomize?**
* Defines a method.
* Noise amplitude needs to be balanced compared to state estimation precision: Too high the agent will not learn, too low the randomization is pointless.

Specific Policies that search for data IRL?

## Method discriminations
- Model-based / -free
- With / Without IRL Data
- Randomize Dynamics / Visuals / Configurations
- Latent Space Projection
- Estimate best model parameters (Inputs: R2S / S2S?)
- Bayesian Optimization (BO)
- Minimizes distance between IRL / Simu
- Restrictions on Domain Parameter Distribution (normal, uniform, etc...)

## To Learn
- Bayesian Optimization
- Gaussian Processes
- Likelihood-Free Inference
- MPC