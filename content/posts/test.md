---
author: ["Munjung Kim"]
title: "Lecture 1: Introduction to Reinforcement Learning"
date: "2022-01-22"
description: "A lecture note of RL course by David Silver"
summary: "Characteristics of Reinforcement Learning"
tags: ["lecture-note", "reinforcement-learning"]
categories: ["lecture-note", "reinforcement-learning"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
---

### What is Reinforcement Learning?

Reinforcement Leraning is across various fields including computer science, neuro science, and psychology. It's about the "science of decision making."

Reinforcement learning is different from other machine learning paradimg as there is no supervisor, only a reward signal. No one tells us right action to take. Just try and error. Also feedback is delayed. It is not instantaneous. Also time really matters, as it is sequential. Also agent's take the action, so their action can affect the subsequent data it receives. 

### Rewards

* A reward $R_t$ is a scalar feedback signal.
* It indicates how well agent is doing at stpe $t$.
* THe agent's job is to maximise cumulative reward.

##### Reward hypothesis
All goals can be described by the maximization of expected cumulative reward.


### Major Components of an RL Agent

An RL agent may include one or more of these components:

* Policy: agent's behaviour function
* Value function: how good is each state and/or action
* Model: agent's representation of the environment

#### Policy

* A plicy is the agent's behaviour
* It is a map from state to action
* Stochastic policy, deterministic policy

#### Value

* Value function is a prediction of future reward
* Used to evaluate the goodness and badness of states
* And therefore to select between actions, 


### MDPs

* Markov decision processes formally describe an environment for reinforcement learning where the environemnt is fully observable
* Almost all RL problems can be formalized as MDPs

#### Markov Property
"The future is independent of the past given the present"
* Definition : A state $S_t$ is Markov if and only if $P[S_{t+1}|S_t] = P[S_{t+1}|S_1, ...,S_t]$


#### Markov Process

#### Markov Reward Process

A Markov Reward Process is a tuple  $<S,P,R,\gamma>$

* $S$ is a finite set of states
* $P$ is a state stransition probability matrix.
* $R$ is a reward function, $R_s = E[R_{t+1}|S_t = s]$
* $\gamma$ is a discount factor.


#### Return

The return $G_t$ is the total discounted reward from time-stemp $t$.

$G_t = R_{t+1} + \gamma R_{t+2} + ....$

* Why discount?
- Animal/human behaviour shows preference for immediate reward
- Avoids infinite returns in cyclic Markov processes


#### Value Function

The value function $v(s)$ gives the long-term value of state $s$.

The state value function $v(s)$ of an MRP is the expected return starting from state $s$.

$v(s) = E[G_t|S_t = s]$

where 

$G_t = R_{t+1} + \gamma R_{t+2} + ....$


It's expectation because the environment is stochastic

The value function can be decomposed into two parts

imeediate reward $R_t$

discounted value of successor state $\gamma v(s_{t+1})$


$v(s) = E[G_t|S_t = s] = E[R_{t+1} + \gamma  v(s_{t+1})] = R_s + \gamma \sum_{s' \inc S} P_{ss'} v(s') $



#### Bellman Equation

* The Bellman Equation is a linear equation
* It can be solved directly

$v = R + \gamma Pv$

* comutational complexity is O(n^3) for n states

### Markov Decision Process

A Markov Decision Process is a tuple  $<S,A,P,R,\gamma>$


#### Policy

A policy $\pi$ is a distribution over actions given states,

$\pi(a|s) = P[A_t = a| S_t = s]$

* MDP policies depend on the current states (not the history)
* Policies are stationary (time-independent)


{{< math.inline >}}

<p>
Inline math: \(\varphi = \dfrac{1+\sqrt5}{2}= 1.6180339887…\)
</p>
{{</ math.inline >}}

Block math:

$$
 \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } }
$$