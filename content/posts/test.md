---
author: ["Munjung Kim"]
title: "Temporal Difference Learning"
date: "2024-03-16"
description: "A lecture note of RL course by Dongrou Zhou and David Silver"
summary: "Temporal difference learning"
tags: ["lecture-note", "reinforcement-learning", "TD-learning"]
categories: ["lecture-note", "reinforcement-learning"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
math: true
---


In the last [post](https://welcome-mj-blog.netlify.app/posts/introduction_to_rl/), I explored foundational concepts of reinforcement learning, including policy iteration and value iteration methods. These iteration approaches provide tools for finding optimal policies in Markov Decision Processes (MDPs). One essential step during these iteration approaches is policy evaluation. We can estimate the value of the current policy by using Bellman equation. 

$$ V^{\pi}(s) = Q^{\pi}(s,\pi(s))$$
$$  Q^{\pi}(s,\pi(s)) = R(s,a) + \gamma \mathbb{E}_{s' \sim P(s,a)} [V^{\pi}(s')]$$.

To calculate this, we still need to know{{< math.inline >}} \(R(s,a)\)  and  \(P(s,a)\). {{</ math.inline >}} In real world, it is hard to get the real {{< math.inline >}} \(R(s,a)\)  and  \(P(s,a)\) for all possible actions and states directly. {{</ math.inline >}} Instead, what we can get is trajectories of interaction. 


## Monte Carlo (MC) On Policy Evaluation

{{< math.inline >}} <p>
1. Initialize \(N(s) = 0, G(s) = 0 \)
</p>{{</ math.inline >}}
{{< math.inline >}} 
2. Loop
{{</ math.inline >}}
- sample episode {{< math.inline >}} \(i = s_i1, a_i1,..., s_iT_i \){{</ math.inline >}} 

- Get return {{< math.inline >}} \(G_{i,t} = r_{i,t } + \gamma r_{i,t+1} + ... + \gamma^{T_i - 1} r_{i,T_i} \) starting from step \(t\){{</ math.inline >}}.

- sample episode {{< math.inline >}} \(i = s_i1, a_i1,..., s_iT_i \){{</ math.inline >}} 

$$\pi_i \rightarrow V^{\pi_i}$$

- **Policy Improvement** : Based on the evaluation of{{< math.inline >}} \(\pi_i\), improve \(\pi_i\) to \(\pi_{i+1}\){{</ math.inline >}}

$$
\pi_{i+i}(s) = \argmax_{a}  \big[\sum_{s'}  p(s'|s,a)(r + \gamma \cdot V^{\pi_i}(s') )\big]
$$

or 
