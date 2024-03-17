---
author: ["Munjung Kim"]
title: "What is Reinforcement Learning?"
date: "2024-03-13"
description: "A lecture note of RL course by Dongrou Zhou and David Silver"
summary: "Key concepts of reinforcement learning"
tags: ["lecture-note", "reinforcement-learning", "fitted-q-learning"]
categories: ["lecture-note", "reinforcement-learning"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
math: true
---

## What is Reinforcement Learning?

Reinforcement Leraning is about the "science of decision making." It is a type of machine learning paradigm where an agent learns to make sequential decisions by interacting with an environment in order to ahcieve a specific goal. In RL, the agent learns through trial and error, receiving feedback in the form of rewards or penalties based on its actions. The goal of the agent is typically to maximize the cumulative reward it receives over time.


## Basic Concepts


### Markov Decision Process (MDP) 

 {{< math.inline >}} <p>A Markov Decision Process is a mathematical framework used to model decision-making problems in which an agent interacts with an environment. It is a fundamental concept in the field of reinforcement learning. A Markov Decision Process consists of a tuple of \(M = (S,A,P,R)\)</p>{{</ math.inline >}}

{{< math.inline >}} <p>
- State space \(S\): A set of all possible situations state \(s\) that the environment can be in.
</p>{{</ math.inline >}}
{{< math.inline >}} <p>
- Action space \(A\): A set of all possible actions \(a\) that the agent can take.
</p>{{</ math.inline >}}
{{< math.inline >}} <p>

- Transition probability function \(P(s'|s,a)\): The probability of transitioning from state \(s\) to \(s'\) after taking action a while obtaining reward \(r\).
</p>{{</ math.inline >}}
{{< math.inline >}} <p>
- Reward function \(R(s,a)\) : Expected value of next reward \(R_{t+1}\) after action \(a_t\) is implemented in state \(s_t\)

</p>{{</ math.inline >}}

### Policy
{{< math.inline >}} <p>
A strategy or mapping which action the agent should take in each state; \(\pi (s)\) = a.
</p>{{</ math.inline >}}

### Value Function
{{< math.inline >}} <p>
The value function \(V(s)\) gives the long-term reward that the agent can obtain from a given state \(s\).

The state value function \(V_{\pi}(s)\) of an MDP is the expected return starting from state \(s\) following the policy \(\pi\).

Mathematically, the value function is defined as the expected sum of discounted future rewards starting from state \(s\):
\(V_{\pi}(s) = E_{\pi}[ R_{t+1} + \gamma R_{t+2} + ....|S_t = s]\) .


It's expectation because the environment can be stochastic.

The value function can be decomposed into two parts: immediate reward \(R_{t+1}\) and discounted value of successor state \(\gamma V(s_{t+1})\).



Therefore, \(V_{\pi}(s)\)can be expressed as 
</p>{{</ math.inline >}}
 $$ E_{\pi}[G_t|S_t = s] = E[R_{t+1} + \gamma  V_{\pi}(s_{t+1})]$$.


### Q Function
{{< math.inline >}} <p>
The action- value function, denoted as \(Q(s,a)\) represents the expected cumulative reward that the agent can obtain from being in state \(s\), taking action \(a\) and following the given policy \(\pi\).

Mathematically,
$$V_{\pi}(s) = Q_{\pi}(s,\pi(s))$$

$$Q_{\pi}(s,a) = \mathbb{E}_{\pi}[G_t|S_t = s, A_t = a] = R(s,a) + \gamma E_{s' \sim P(s,a)}[V^{\pi}(s')]$$

These equations are called Bellman Equation. When \(\pi\) is nondeterministic, the first equation can also expressed as

$$V_{\pi}(s) = \sum_{a\in A} Q_{\pi}(s,a)\pi(a|s)$$


</p>{{</ math.inline >}}

### Optimal Policy and Value Function
{{< math.inline >}} <p>
The optimal value function, denoted as \(V^{*}(s)\) represent the maximum expected cumulative reward that an agent can achieve from a given state \(s\) by following the optimal policy \(\pi^{*}\). Similarly, the optimal Q-function \(Q^{*}(s,a)\) represents the maximum expected cumulative reward that an agent can achieve from taking action \(a\) in the state \(s\) and then following the optimal policy thereafter.
</p>{{</ math.inline >}}

## Policy Iteration vs Value Iteration
{{< math.inline >}} <p>
How can we get the optimal policy \(\pi^{*}\)? One way might be explore all possible policies \(pi\) and choose the one making the best rewards.  However, this exhaustive search is computationally expensive and often impractical, especially in environments with large state and action spaces. Iteration methods offer a smarter and more efficient alternative to finding the optimal policy. There are two main iteration approaches: Policy Iteration and Value Iteration.
</p>{{</ math.inline >}}

### Policy Iteration
{{< math.inline >}} <p>
1. set \(i\) = 0
</p>{{</ math.inline >}}
{{< math.inline >}} <p> 
2. Initialize \(\pi_0(s)\) as the uniformly random policy over all \(a \in A\)
</p>{{</ math.inline >}}
{{< math.inline >}} 
3. While \(|\pi_i - \pi_{i-1}| > 0\)
{{</ math.inline >}}
- **Policy Evaluation** : Evaluate the value of {{< math.inline >}} \(\pi_i\) by using 
$$V^{\pi_i}(s) = \sum_{s'} p(s'|s,\pi(s))(r + \gamma \cdot V^{\pi_i}(s'))$${{</ math.inline >}} 

$$\pi_i \rightarrow V^{\pi_i}$$

- **Policy Improvement** : Based on the evaluation of{{< math.inline >}} \(\pi_i\), improve \(\pi_i\) to \(\pi_{i+1}\){{</ math.inline >}}

$$
\pi_{i+i}(s) = \argmax_{a}  \big[\sum_{s'}  p(s'|s,a)(r + \gamma \cdot V^{\pi_i}(s') )\big]
$$

or 

$$ \pi_{i+1}(s) = \argmax_{a} Q^{\pi_i}(s,a) \forall s \in S$$

$$ V^{\pi_i} \rightarrow \pi_{i+1}$$

- {{< math.inline >}} \(i+=1\){{</ math.inline >}}

### Value Iteration

Policy iteration computes the infinite horizon value of a policy and then improves that policy. However, in some cases, we do not have to maintain the policies. Value iteration is another technique idea for this. 

{{< math.inline >}} <p>
1. set \(i\) = 0
</p>{{</ math.inline >}}
{{< math.inline >}} <p> 
2. Initialize \(\Q_0(s,a) = 0\) for all \(s \in S\) and \(a \in A\)
</p>{{</ math.inline >}}
{{< math.inline >}} 
3. While \(|Q_i - Q_{i-1}| > 0\)
{{</ math.inline >}}
- {{< math.inline >}} \( Q_{i+1} = R(s,a) + \gamma \mathbb{E}_{s' \sim P(s,a)} V_Q(s') \), where {{</ math.inline >}}

$$
V_Q(s') = \max_a \big[ \sum_{s''}  p(s''|s',a)(r + \gamma*V(s'') \big]
$$

So it is like assuming {{< math.inline >}}\( Q(s,a)\) by summing the immediate reward \(R(s,a)\) and the maximum cummulative rewards of \(V(s')\) based on current assumption. {{</ math.inline >}}


Example code for Value iteration and policy iteration : [https://colab.research.google.com/drive/1JbYBgZUg74yrfo1VQbJPaWkDREbhuDsW?usp=sharing#scrollTo=gg97TU1j2ED5](https://colab.research.google.com/drive/1JbYBgZUg74yrfo1VQbJPaWkDREbhuDsW?usp=sharing#scrollTo=gg97TU1j2ED5)