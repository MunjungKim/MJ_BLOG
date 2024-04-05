---
author: ["Munjung Kim"]
title: "Computational Philosophy"
date: "2024-03-18"
description: "Šešelja, D. (2022). Agent‐based models of scientific interaction. Philosophy Compass, 17(7), e12855."
summary: ""
tags: ["paper-review","paper-summary"]
categories: [ "paper"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
math: true
---


## Modelling the Structure of a Communication Network

1) How to represent rival scientific theories and their ideal or objective epistemic success (Sytem)
2) How to represent evidence gathering, that is, inforamtion in view of which scientists assess theories (Experiment strategy)
3) How to represent exchange of information (Social Learning)
4) How scientists in the model reason and evaluate theories (Scientists)


### Zollman's model
Scientists : Bayesian reasoners assigned random prior probabilities for two rival hypotheses, each of which has a designated objective probability of success (OPS) Agents always choose to pursue a theory which they believe to be better. 

Social Learning:  they update their beliefs in view of their own findings and the information they receive from other agents with whom they are linked in a social network.

### Grim, Singer's model
simulation agents are randomly positioned on the x-axis of the landscape.
in case of landscapes with a hidden peak the complete graph tends to
prematurely abandon exploration, converging onto a local maximum.

### ABMs based on argumentative dynamics

‘argumentative landscape’: nodes are arguments and edges are discovery relationship

scientists gradually explore the landscape, discovering arguments and attacks between them.

they aim to determine which theory is the best one from an argumentative point of
view, for example, due to having more defended arguments than its rivals

Theories are modeled in such a way that
only one of them is fully defensible from all the attacks. (maybe like Lakatos)

they (i) explore the landscape, (ii) exchange information
within their social network and (iii) update their assessment of the given theories. By exploring the landscape, agents
occasionally encounter defeating evidence, represented as attacks coming from arguments in a rival theory. 

They may
also encounter arguments that defend their attacked hypotheses (by attacking their attackers), thereby reinstating
them. Roughly, an argument a is defended in the theory if it is not attacked or if each attacker b from another theory
is itself attacked by some defended argument c in the current theory


Conclusion: The more connected a scientific community is, the higher its chances of convergin on the best theory. 
* when
agents explore a theory, they also gain information about the rival theories: for example, by learning an argument in
one theory which attacks the rival theory, a scientist learns of a potential problem in the latter

## THE CONTRIBUTION OF ABMs OF SCIENTIFIC INTERACTION TO THE PHILOSOPHY OF SCIENCE

* network effects on the efficiency
of scientific inquiry, and their applications to the study of bias and deception in science

* Problem is that they are highly idealized. 
    - What exactly is the epsitemic function of these models?
    - Can we say that the findings actually facilitate the understanding of certain causal dependencies or regulariteis that hold between network effects and the efficiency of inquiry?
     - **Can we use them to provide potential explanations of certain episodes from the history of science?**
     - **Can we use them to formulate recommendations to scienctists concerning an optimal structure of scientific interaction in a given scientific community, given specific constraints on inquiry?**







# Reference

Šešelja, D. (2022). Agent‐based models of scientific interaction. Philosophy Compass, 17(7), e12855.

Mayo-Wilson, C., & Zollman, K. J. (2021). The computational philosophy: simulation as a core philosophical method. Synthese, 199(1), 3647-3673.

