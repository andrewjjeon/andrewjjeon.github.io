---
title: "Synthetic Data Generation for Foundation Model Pose Estimation"
collection: projects
category: manuscripts
permalink: /projects/fposepanda/
image: /images/FposePanda100.gif
---

<h2>Synthetic Data Generation for Foundation Model Pose Estimation</h2>

<p>
  FoundationPose is a Unified foundation model for 6D pose estimation and tracking, 
  Further details can be found in <a href="https://nvlabs.github.io/FoundationPose/" target="_blank">FoundationPose</a>
</p>

<p>
  I developed a synthetic data generation pipeline in Pybullet that processes the world to camera transformations, coordinate space transformations, 
  and calculates the correct ground truth robot pose matrices. The pipeline uses robot (.urdf) and (.obj) files to load the robot or whichever link we want.
  I then setup a virtual camera to take frames (rgb, depth, binary mask) which are all inputs the foundation model, foundationpose, needs to run successfully.
  There is also code for ground truth visualizations and I also modified a script (graciously provided by Stan Birchfield of Nvidia) to 
  transform a (.urdf) robot descriptor file to 1 whole (.obj) mesh file.

  The ultimate goal of the project is to run multiple instances of the foundation model, one on the object to grasp and one on the robot. We then would use
  the corresponding pose matrices to enable precise grasping.
  
  Achieved following competitive errors on robot hand pose estimation
  - Rotation Angle Error of 0.674 degrees
  - Translation Error of 0.655 mm
</p>

<h3>Block Diagram of Proposed Approach</h3>
<div>
  <img src="/images/fp_block.JPG" alt="Block Diagram" style="max-width: 60%; height: auto;">
</div>

<h3>FoundationPose Robot Instance Demo on Franka Panda Synthetic Data</h3>
<div>
  <img src="/images/FposePanda100.gif" alt="FoundationPose robot hand instance" style="max-width: 60%; height: auto;">
</div>

<h3>FoundationPose Object Instance Demo on HOPE Dataset Ketchup</h3>
<div>
  <img src="/images/fp_ketchup.gif" alt="FoundationPose object instance" style="max-width: 40%; height: auto;">
</div>

<h3>Synthetic Robot Pose Data Generation using Pybullet</h3>
<div>
  <img src="/images/7.png" alt="robotgt" style="max-width: 25%; height: auto;">
  <img src="/images/7m.png" alt="handgt" style="max-width: 25%; height: auto;">
  <img src="/images/7d.png" alt="handgt" style="max-width: 25%; height: auto;">
  <img src="/images/7gt.png" alt="handgt" style="max-width: 25%; height: auto;">
</div>