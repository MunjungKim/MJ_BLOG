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
Policy Gradient is a type of reinforcement learning techniques that rely upon optimizing parametrized policies with respect to the expected return (long-term cumulative reward) by gradient descent. Instead of estimating value functions and deriving policies from them, as in value-based methods, PG methods focus on improving the policy itself. This direct optimization approach can lead to more efficient learning and better performance in certain scenarios. For instance, PG methods can handle high-dimensional state spaces effectively, especially when combined with function approximation techniques like neural networks.</p>{{</ math.inline >}}




{{< math.inline >}}
We can first define the dependence of the value on the policy parameters $$V^{\pi_\theta} = V(s_0,\theta)$$ Then policy gradient algorithms search for a local maximum in \(V(s_0,\theta)\) by ascending the gardient of the policy, w.r.t. parameters \(\theta\). The policy parameters \(\theta\) are updated iteratively using the formula \(\Delta \theta = \alpha \cdot \nabla_\theta V(S_0, \theta)\), where \( \nabla_\theta V(S_0, \theta)\) is policy gradient and \(\alpha\) is the step size. {{</ math.inline >}}





### Different types of {{< math.inline >}} \(\pi_\theta\) {{</ math.inline >}}

#### Assumptions on the Policy Function:

* {{< math.inline >}}Differentiability: We assume that the policy function \(\pi_\theta\) is differentiable whenever it is non-zero. This assumption ensures that we can compute gradients of the oplicy function with respect to its parameters for all state-action pairs.
 {{</ math.inline >}}


 * Analytical Gradient: We assume that we can calculate the gradient of the policy function analytically for all state-action pairs. 


 #### Softmax Policy
{{< math.inline >}}Softmax policy weight actions using linear combination of features \(\phi(s,a)^\intercal\theta\). The probability of action is then, calculated by normalized value of the exponentiated weight \(\pi_\theta(s,a) = e^{\phi(s,a)^\intercal\theta} / Z\). Then the score function (the gradient of the log probability) becomes \( \nabla_\theta \log \pi_\theta(s,a) = \phi(s,a) - \)
 {{</ math.inline >}}

 #### Gaussian Policy 
Gaussian policies model the action distribution as a Gaussian distribution parameterized by mean and variance. They are suitable for continuous action spaces and offer tractable analytical gradients.

 #### Neural Network Policy


## Importance Weight






## Baseline 

## Natural Policy Gradient

Natural Policy Gradient (NPG) is an advanced technique used in reinforcement learning (RL) to optimize policy parameters more efficiently. It addresses some of the limitations of traditional policy gradient methods, particularly regarding the choice of step size and the sensitivity of optimization to the parameterization of the policy.



