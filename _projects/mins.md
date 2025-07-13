---
title: "Evaluating Sensor Fusion Visual-Inertial SLAM Algorithms"
collection: projects
category: manuscripts
permalink: /projects/foundation-pose-synthetic-data/
image: /images/MINSurban28.gif
---

<h2>Evaluating Sensor Fusion Visual-Inertial SLAM Algorithms</h2>

<p>
  I am leading the testing and evaluation of a sensor fusion inertial navigation system with 5 sensing modalities on a Rover with a solid-state LiDAR system.
  I tuned navigation system and sensor parameters to achieve an Absolute Trajectory Error of 9.12091m across multi-kilometer trajectories. 

  MINs is a Multisensor-aided Inertial Navigation System that can fuse up to 5 sensing modalities (IMU, wheel encoders, camera, GNSS, and LiDAR) 
  in a Kalman Filter.<a href="https://github.com/rpng/mins" target="_blank">MINs</a> I have tuned MINs on public datasets such as the 
  <a href="https://sites.google.com/view/complex-urban-dataset" target="_blank">KAIST Urban Dataset</a> as well as our labs rover runs.
</p>


<div style="display: flex; justify-content: center; gap: 5px; text-align: center;">
  <div>
    <img src="/images/MINSurban28.gif" alt="MINs on KAIST dataset" style="max-width: 80%; height: auto;">
    <p>MINs on KAIST car dataset</p>
  </div>
  <div>
    <img src="/images/rover0824.gif" alt="MINs on our rover data" style="max-width: 80%; height: auto;">
    <p>MINs on actual rover</p>
  </div>
</div>
