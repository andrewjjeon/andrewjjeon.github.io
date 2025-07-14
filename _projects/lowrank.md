---
title: "Regularization, Hyperparameter Tuning on Low Rank Autoregressive Models"
collection: projects
category: manuscripts
permalink: /projects/lowrank/
image: /images/lowrankreg.png
---


<h2>Regularization, Hyperparameter Tuning on Low Rank Autoregressive Models</h2>

<p>
  There is a strong need for techniques that minimize the amount of data needed to learn neural population dynamics due to experimental time and resource constraints. "Active learning of neural population dynamics using two-photon holographic optogenetics" is a NeurIPS 2024 paper that attempts to determine the most effective photostimulation patterns for identifying neural population dynamics. The goal is to select the neurons that have the most informative neural responses to inform a dynamical model of the neural population activity. 
</p>
<p>
  The project’s active learning technique takes advantage of the low-rank structure of the neural population dynamics to determine the most informative photostimulation patterns. It uses SVD to create low rank autoregressive models that predict neural activity. I conducted various regularization and tuning experiments on these models. This resulted in 15-18% improvements (MSE) in model performance. 

  Further details can be found in the paper <a href="https://arxiv.org/abs/2412.02529" 
  target="_blank">Active learning of neural population dynamics</a>
</p>


<div style="text-align: center;">
  <img src="/images/lowrankreg.png" alt="Full Rank, Low Rank, Low Rank w/ L2 Reg " style="max-width: 60%; height: auto;">
  <p>Low Rank Stimulation Responses highlight the low latent dynamics of neural populations.</p>
</div>
