---
author: ["Munjung Kim"]
title: "Value Function Method with Neural Networks"
date: "2024-03-13"
description: "A lecture note of RL course by Dongrou Zhou and David Silver"
summary: "Value function for neural networks and general function approximations: q learning, DQN"
tags: ["lecture-note", "reinforcement-learning", "fitted-q-learning"]
categories: ["lecture-note", "reinforcement-learning","value-function]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
---
## What is Reinforcement Learning?

Reinforcement Leraning is across various fields including computer science, neuro science, and psychology. It's about the "science of decision making."

Reinforcement learning is different from other machine learning paradimg as there is no supervisor, only a reward signal. No one tells us right action to take. Just try and error. Also feedback is delayed. It is not instantaneous. Also time really matters, as it is sequential. Also agent's take the action, so their action can affect the subsequent data it receives. 



## Basic Concepts


### Markov Decision Process (MDP) $M = (S,A,P,\gamma)$
* State $S_t$ is Markov if and only if $P[S_{t+1}|S_t] = P[S_{t+1}|S_1, ...,S_t]$
* State space $S$, state $s \in S$ 
* Action space $A$, action $a \in A$
* Transition probability function $P(s'|s,a)$ : The probability of transitioning from state $s$ to $s'$ after taking action a while obtaining reward $r$.
* Reward function $R(s,a)$ : Expected value of next reward $R_{t+1}$ after action $a$ is implemented

### Policy
* a map from $S$ -> $A$

### Value Function

The value function $V_{\pi}(s)$ gives the long-term value of state $s$.

The state value function $V_{\pi}(s)$ of an MRP is the expected return starting from state $s$ following the policy $\pi$.

$V_{\pi}(s) = E_{\pi}[G_t|S_t = s]$

where 

$G_t = R_{t+1} + \gamma R_{t+2} + ....$

It's expectation because the environment is stochastic

The value function can be decomposed into two parts

immediate reward $R_{t+1}$ and discounted value of successor state $\gamma v(s_{t+1})$


$V_{\pi}(s) = E_{\pi}[G_t|S_t = s] = E[R_{t+1} + \gamma  v(s_{t+1})]$

### Q Function

The Q function $Q(s,a)$ gives the long-term value of state-action pairs $(s,a)$.

$Q_{\pi}(s,a) = \mathbb{E}_{\pi}[G_t|S_t = s, A_t = a] = R(s,a) + \gamma E_{s'~P(s,a)}[V^{\pi}(s')]$ 

and

$V_{\pi}(s|a) = \sum_{a\in A} Q_{\pi}(s,a)\pi(a|s)$



### Optimal value function, Q function and policy:

### Bellman Equation