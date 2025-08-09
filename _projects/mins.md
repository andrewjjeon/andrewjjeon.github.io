---
layout: page
title: "Evaluating Sensor Fusion SLAM"
collection: projects
category: projects
image: /images/mins/MINSurban28.gif
order: 3
math: true
---

<div style="max-width: 1200px; margin: 0 auto; padding: 1rem;">
  <div class="card">
    <h1>Evaluating Multisensor-aided Inertial Navigation System (MINS)</h1>
    <h2>1. Introduction</h2>
      <a href="https://github.com/rpng/MINS">MINS</a> is a multisensor sensor fusion slam system capable of fusing IMU, camera, LiDAR, GPS, and wheel sensors. My goal was to evaluate it on the <a href="https://sites.google.com/view/complex-urban-dataset">KAIST Urban Dataset</a> as well as my lab's (at University of Washington) suburban rover dataset. I used <a href="https://github.com/tsyxyz/kaist2bag">kaist2bag</a> to convert the separate sensor bag files to one bag.
  </div>

  <div class="card">
    <h2>2. Sensor Calibration</h2>
      I had to calibrate and configure the system to work with the various sensors in the KAIST setup and the rover setup respectively. The main sensor calibration parameters I had to configure were:
      <ul>
        <li>Transformation matrices between sensors T_imu_camera, T_imu-wheel, T_imu_lidar</li>
        <li>Camera intrinsics, resolution</li>
        <li>IMU acceleration and bias, gyroscope acceleration and bias </li>
        <li>Wheel intrinsics (radius, wheel base)</li>
      </ul>
      Additionally, I had to download the segway_msgs and gnss_comm ROS message packages to enable our system to correctly read messages from our rover wheel encoder and gps.
  </div>

  <div class="card">
    <h2>3. Evaluation</h2>
      MINS already had evaluation code that worked with minimal tuning and setup. Absolute Trajectory Error, a formulation of which can be found below, was used to evaluate the SLAM trajectories. I achieved a 9.12m ATE on an 11km KAIST Urban Trajectory and a 1.1m ATE on our 1km Lab rover trajectory.

      $$
      ATE_{RMSE} = \sqrt{ \frac{1}{N} \sum_{i=1}^{N} \left\| P_{i}^{est} - P_{i}^{gt} \right\|^2 }
      $$


      <div style="display: flex; justify-content: center; gap: 20px;">
        <div style="text-align: center;">
          <img src="/images/mins/MINSurban28.gif" width="600"/>
          <p><em>MINS Result on KAIST Urban dataset</em></p>
        </div>

        <div style="text-align: center;">
          <img src="/images/mins/rover0824.gif" width="600"/>
          <p><em>MINS Result on Lab Rover Dataset</em></p>
        </div>
      </div>

      <div style="display: flex; justify-content: center; gap: 20px;">
        <div style="text-align: center;">
          <img src="/images/mins/urban28_complete_trajectory.png" width="600"/>
          <p><em>Complete MINS Trajectory of KAIST Urban28</em></p>
        </div>

        <div style="text-align: center;">
          <img src="/images/mins/urban28_gt_trajectory.png" width="600"/>
          <p><em>Complete Ground Truth Trajectory of KAIST Urban28</em></p>
        </div>
      </div>
  </div>
</div>