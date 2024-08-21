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


#### Domain Randomization for Robotic Review
*Robot Learning From Randomized Simulations: A Review. Fabio Muratore, Fabio Ramos, Greg Turk, Wenhao Yu, Michael Gienger and Jan Peters*

##### Papers
* Adaptive Dynamic Randomization: *Muratore, F., Eilers, C., Gienger, M., and Peters, J. (2021a). Data-efficient Domain Randomization with Bayesian Optimization*
* 