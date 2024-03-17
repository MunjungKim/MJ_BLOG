---
author: ["Munjung Kim"]
title: "Policy Gradient"
date: "2024-03-16"
description: "A lecture note of RL course by Dongrou Zhou and David Silver"
summary: "Policy Gradient,TRPO,PPO "
tags: ["lecture-note", "reinforcement-learning", "TD-learning"]
categories: ["lecture-note", "reinforcement-learning"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
math: true
---

## Policy Gradient
{{< math.inline >}} <p>
Policy Gradient is a type of reinforcement learning techniques that rely upon optimizing parametrized policies with respect to the expected return (long-term cumulative reward) by gradient descent. </p>{{</ math.inline >}}


{{< math.inline >}}
We can first define the dependence of the value on the policy parameters $$V^{\pi_\theta} = V(s_0,\theta)$$ Then policy gradient algorithms search for a local maximum in \(V(s_0,\theta)\) by ascending the gardient of the policy, w.r.t. parameters \(\theta\).{{</ math.inline >}}

### Different types of {{< math.inline >}} \(\pi_\theta\) {{</ math.inline >}}

Assume 

## Baseline 

## Natural Policy Gradient

Natural Policy Gradient (NPG) is an advanced technique used in reinforcement learning (RL) to optimize policy parameters more efficiently. It addresses some of the limitations of traditional policy gradient methods, particularly regarding the choice of step size and the sensitivity of optimization to the parameterization of the policy.



