---
layout: page
title: "Regularization, Hyperparameter Tuning on Low Rank Autoregressive Models"
collection: projects
category: projects
image: /images/lowrank/lowrank_reg.png
order: 5
math: true
---



<div style="max-width: 1200px; margin: 0 auto; padding: 1rem;">
  <div class="card">
    <h1>Regularization, Hyperparameter Tuning of Low Rank Autoregressive Models</h1>
    <h2>1. Introduction</h2>
      I conducted Regularization and Hyperparameter Tuning Experiments on the Low Rank Autoregressive Models used in this paper:
      [<b>Active Learning of Neural Population Dynamics using two-photon holographic optogenetics</b>](https://arxiv.org/abs/2412.02529)

      Some motivation for why is that there is a strong need for techniques that minimize the amount of data needed to learn neural population dynamics due to experimental time and resource constraints. The long-term goal that the above paper is working towards is for a model to be able to actively learn the patterns of neurons that have the most informative neural responses to quickly learn the neural population dynamics (brain activity).

      This project used experimental data where a region of a mice brain was photostimulated with a laser. Specifically, patterns of neurons were photostimulated and the rest of region neuron's response (spikes) to that stimulation was recorded.<br>

      <img src="/images/lowrank/spikes_detected.png" width="600" />
      <p>Spikes were determined as signal responses that were 6x greater than the baseline noise of the signal.</p>

      <img src="/images/lowrank/photostim_neurons_map.png" width="600" />
      <p>Here you can see an example pattern of neurons being photostimulated by the neuron.</p>

      The project’s active learning technique takes advantage of the low-rank structure of the neural population dynamics to determine the most informative photostimulation patterns. It uses SVD to create low rank autoregressive models that predict neural activity (spikes).
  </div>

  <div class="card">
    <h2>2. L2 Regularization and Hyperparameter Tuning</h2>
      These Low Rank Models are the models I was tasked with experimenting on. I used cross validation loops to tune hyperparameters such as... 
      <ul>
        <li>Lambda (L2 Regularization strength)</li>
        <li>Epochs</li>
        <li>Learning Rate </li>
        <li>Weight Initialization</li>
        <li>k (number of autoregressive time steps used to make prediction)</li>
      </ul>
      My best model resulted in a 25% improvement in performance (MSE) over the baselines the team had before I came on.

    <div style="display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center;">
      <img src="/images/lowrank/mse_improvement.png" alt="MSE" style="width: 49%;">
      <img src="/images/lowrank/roc_curves.png" alt="ROC" style="width: 49%;">
    </div>

    <p>Best Model Performances</p>

    <img src="/images/lowrank/lowrank_reg.png" width="700" />>
    <p>A comparison of the spike predictions of the closed-form, full-rank model, and low-rank model.</p>
  </div>


</div>