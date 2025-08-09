---
layout: page
title: "Image-Captioning Tactical Advisor Model (ICTAM)"
collection: projects
category: projects
image: /images/ictam/blip-finetuned-model_image_caption.png
order: 5
math: true
---



<div style="max-width: 1200px; margin: 0 auto; padding: 1rem;">
  <div class="card">
    <h1>Image-Captioning Tactical Advisor Model (ICTAM)</h1>
    <h2>1. Introduction</h2>
      ICTAM was my first attempt at applying pretrained LLMs to tactical analysis and advisory tasks. This work was inspired by [CICERO](https://www.science.org/doi/10.1126/science.ade9097) and [LLMs play sc2](https://arxiv.org/abs/2312.11865). I primarily wanted to test the pretrained capabilities of image captioning models and see if they could make accurate tactical judgements with minimal supervised finetuning.
  </div>

  <div class="card">
    <h2>2. Data Processing</h2>
      My data pipeline consists of starcraft youtube video downloads from yt-dlp which feeds into image sampling and cropping using ffmpeg. I sample one image per minute (1/60 fps) as 1 frame should loosely describe the tactical state of the minimap for a minute although more sampling would be good. I crop the bottom left of the screen as that is where the minimap is. I then generate a .json caption file that stores a dictionary per image-caption pair. In order to enable tactical judgement evaluation, the captions were structured to start with "Winner. Followed by the rest of the caption."

      <div style="display: flex; justify-content: center; gap: 20px;">
        <div style="text-align: center;">
          <img src="images/ictam/art11_016.jpg" width="400" />
          <p><em>Sample Frame</em></p>
        </div>

        <div style="text-align: center;">
          <img src="images/ictam/example_caption.png" width="400" />
          <p><em>Sample Caption</em></p>
        </div>
      </div>
  </div>

  <div class="card">
    <h2>3. Training and Validation</h2>
      I did an 80-10-10 train-val-test split on my image-caption pairs. I then trained the BLIPConditionalGeneration model with the HuggingFace Trainer. This model was trained with a cross-entropy loss that compares a sequence of tokens against that same sequence shifted forward.

      <div align="center">
        <img src="images/TrainingLossCurve.png" width="400" />
        <p><em>Train-Validation Loss Curves (validation only starts after the first epoch)</em></p>
      </div>
  </div>

  <div class="card">
    <h2>4. Evaluation</h2>
      I evaluated the % of correct tactical judgement from BLIP by parsing the caption string, and creating a list of just the winner prediction before the ".". I then compared this list against the same list from the actual captions. ICTAM successfully identifies the "winning player color" 80% of the time across multiple test trials with the test dataset which ICTAM had not been trained on.
      <div style="display: flex; justify-content: center; gap: 20px;">
        <div style="text-align: center;">
          <img src="images/ictam/blip-image-captioning-base_image_caption.png" width="400" />
          <p><em>blip-base caption inference result</em></p>
        </div>

        <div style="text-align: center;">
          <img src="images/ictam/blip-finetuned-model_image_caption.png" width="400" />
          <p><em>blip-finetuned caption inference result</em></p>
        </div>
      </div>

      <div style="text-align: center;">
        <img src="images/ictam/ictam_eval.png" width="400" />
        <p><em>ICTAM Tactical Judgement Accuracy</em></p>
      </div>

  </div>
</div>