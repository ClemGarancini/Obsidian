# MDP
A MDP is defined by 

$M = (S,A,T,R)$ where:
* $S$ is the set of possible states
* $A$ is the set of possible actions
* $T: S\times A\times S \rightarrow [0,1]$  is the transition probability of a state $s_0$ and an action $a$ to a state $s_1$
* $R: S\times A \rightarrow \mathbb{R}$ is the reward function
