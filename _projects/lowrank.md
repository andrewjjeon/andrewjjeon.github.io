---
title: "Regularization, Hyperparameter Tuning on Low Rank Autoregressive Models"
collection: projects
category: manuscripts
image: /lowrank/lowrank_reg.png
order: 5
---

### Low Rank Autoregressive Model Regularization and Hyperparameter Tuning

I conducted Regularization and Hyperparameter Tuning Experiments on the Low Rank Autoregressive Models used in this paper:
[<b>Active Learning of Neural Population Dynamics using two-photon holographic optogenetics</b>](https://arxiv.org/abs/2412.02529)

Some motivation for why is that there is a strong need for techniques that minimize the amount of data needed to learn neural population dynamics due to experimental time and resource constraints. The long-term goal that the above paper is working towards is for a model to be able to actively learn the patterns of neurons that have the most informative neural responses to quickly learn the neural population dynamics (brain activity).

This project used experimental data where a region of a mice brain was photostimulated with a laser. Specifically, patterns of neurons were photostimulated and the rest of region neuron's response (spikes) to that stimulation was recorded. 

<img src="lowrank/spikes_detected.png" width="400" />
<p>Spikes were determined as signal responses that were 6x greater than the baseline noise of the signal.</p>

<img src="lowrank/photostim_neurons_map.png" width="400" />
<p>Here you can see an example pattern of neurons being photostimulated by the neuron.</p>

The project’s active learning technique takes advantage of the low-rank structure of the neural population dynamics to determine the most informative photostimulation patterns. It uses SVD to create low rank autoregressive models that predict neural activity (spikes). These are the models I was tasked with experimenting on. I tuned hyperparameters such as Lambda (L2 Regularization strength), Epochs, Learning Rate, Weight Initialization, k (number of autoregressive time steps used) with cross-validation loops. My best model resulted in a 25% improvement in performance (MSE) over the baselines the team had before I came on.

<div style="text-align:center">
  <img src="lowrank/mse_improvement.png" width="250" style="vertical-align: top; margin-right:20px;" />
  <img src="lowrank/roc_curves.png" width="250" style="vertical-align: top; margin-right:20px;" />
</div>


<img src="lowrank/lowrank_reg.png" width="500" style="vertical-align: top;" />
<p>A comparison of the spike predictions of the closed-form, full-rank model, and low-rank model.</p>