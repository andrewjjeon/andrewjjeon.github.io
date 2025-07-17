---
title: "Synthetic Data Generation for Foundation Model Pose Estimation"
collection: projects
image: /images/fpose/FposePanda100.gif
order: 1
math: true
---




<style>
/* Add at the top of your Markdown */
body {
  background-color: #0e0e0e;
  color: #dcdcdc;
  font-family: 'Inter', sans-serif;
}

.card {
  background: rgba(30, 30, 30, 0.85);
  border-radius: 16px;
  padding: 2rem;
  margin-bottom: 2rem;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.6);
  border: 1px solid rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(12px);
}

.card img {
  border-radius: 12px;
  max-width: 100%;
  margin-top: 1rem;
}

h2, h3 {
  color: #ffffff;
  margin-top: 1.5rem;
}

ul {
  padding-left: 1.2rem;
}

code {
  background: #1e1e1e;
  padding: 0.2rem 0.4rem;
  border-radius: 4px;
  color: #ffd700;
}
</style>

<div class="card">
  <h2>Evaluating Foundation Model Robot Pose Estimation with Synthetic Data Generation</h2>

  <p>
    Position and Orientation or "Pose" is a 4x4 matrix that defines the translation or "position" and rotation or "orientation" of an object. Robot Pose Estimation is useful because if you can accurately predict where a robot and an object are and how they are oriented. In robotics this is useful, because if you have the two pose matrices for the robot and object, you should be able to calculate a "relative grasp" transform that describes how the robot should position itself to grasp the object successfully. 

    Moreso if you can perform accurate robot pose estimation using a foundation model that wasn't explicitly trained on your robot, you should be able to grasp items that the model wasn't trained on with robots the model wasn't trained on. The system uses <code>.urdf</code> and <code>.obj</code> files 
    to load robotic models, then renders <strong>RGB</strong>, <strong>Depth</strong>, and <strong>Binary Mask</strong> frames via virtual cameras. These serve as inputs to FoundationPose.
  </p>

  $$
  T_R^O = T_C^O \times T_R^C
  $$

  $$
  {T_C^R}^{-1} = T_R^C
  $$

  <p>
    By using a <strong>foundation model</strong> like <code>FoundationPose</code> on synthetic data (rendered from <code>.urdf</code> and <code>.obj</code> files), we can estimate 6D poses without requiring real-world training data — enabling generalization across unseen robots and objects.
  </p>

  <p><strong>Goal:</strong> Run FoundationPose on both robot and object models to obtain precise 6D poses for grasp planning.</p>

  <ul>
    <li>🔁 Rotation Error: <strong>0.674°</strong></li>
    <li>📍 Translation Error: <strong>0.655 mm</strong></li>
  </ul>
</div>

<div class="card">
  <h3>🔧 Block Diagram</h3>
  <img src="/images/fpose/fp_block.JPG" alt="Block Diagram">
</div>

<div class="card">
  <h3>🦾 Franka Panda + FoundationPose (Synthetic Data)</h3>
  <img src="/images/fpose/FposePanda100.gif" alt="Franka Panda Demo">
</div>

<div class="card">
  <h3>🍅 HOPE Dataset (Ketchup)</h3>
  <img src="/images/fpose/fp_ketchup.gif" alt="Ketchup Demo">
</div>

<div class="card">
  <h3>🧪 PyBullet Synthetic Outputs</h3>
  <div style="display: flex; gap: 1rem; flex-wrap: wrap;">
    <img src="/images/fpose/7.png" alt="RGB" style="width: 22%;">
    <img src="/images/fpose/7m.png" alt="Mask" style="width: 22%;">
    <img src="/images/fpose/7d.png" alt="Depth" style="width: 22%;">
    <img src="/images/fpose/7gt.png" alt="GT Pose" style="width: 22%;">
  </div>
</div>







<!-- <div class="Project-Header">
  <h2>Evaluating Foundation Model Robot Pose Estimation with Synthetic Data Generation</h2>
</div>

<div class="Introduction">
  <p>
    Position and Orientation or "Pose" is a 4x4 matrix that defines the translation or "position" and rotation or "orientation" of an object. Robot Pose Estimation is useful because if you can accurately predict where a robot and an object are and how they are oriented. In robotics this is useful, because if you have the two pose matrices for the robot and object, you should be able to calculate a "relative grasp" transform that describes how the robot should position itself to grasp the object successfully. 
    
    $$
    T_R^O = T_C^O \times T_R^C
    $$

    $$
    {T_C^R}^{-1} = T_R^C
    $$

    Moreso if you can perform accurate robot pose estimation using a foundation model that wasn't explicitly trained on your robot, you should be able to grasp items that the model wasn't trained on with robots the model wasn't trained on. The system uses <code>.urdf</code> and <code>.obj</code> files 
    to load robotic models, then renders <strong>RGB</strong>, <strong>Depth</strong>, and <strong>Binary Mask</strong> frames via virtual cameras. These serve as inputs to FoundationPose.
  </p>

  <p>
    The pipeline also supports ground truth visualization and mesh conversion (thanks to a script by Stan Birchfield) that converts 
    a <code>.urdf</code> descriptor into a unified <code>.obj</code> mesh.
  </p>

  <p>
    <strong>Goal:</strong> Run FoundationPose instances on both robot and object models to obtain precise 6D poses for grasp planning.
  </p>

  <ul>
    <li>Rotation Angle Error: <strong>0.674°</strong></li>
    <li>Translation Error: <strong>0.655 mm</strong></li>
  </ul>
</div>

---

<h3>🔧 Block Diagram of Proposed Approach</h3>
<div class="img-container">
  <img src="/images/fpose/fp_block.JPG" alt="Block Diagram" class="img-fluid rounded shadow" style="max-width: 80%;">
</div>

---

<h3>🤖 FoundationPose on Franka Panda Synthetic Data</h3>
<div class="img-container">
  <img src="/images/fpose/FposePanda100.gif" alt="Franka Panda Demo" class="img-fluid rounded shadow" style="max-width: 70%;">
</div>

---

<h3>🍅 FoundationPose on HOPE Dataset (Ketchup)</h3>
<div class="img-container">
  <img src="/images/fpose/fp_ketchup.gif" alt="HOPE Ketchup Demo" class="img-fluid rounded shadow" style="max-width: 40%;">
</div>

---

<h3>🧪 Synthetic Data Outputs via PyBullet</h3>
<div class="row">
  <div class="col-sm-3"><img src="/images/fpose/7.png" class="img-thumbnail" alt="rgb"></div>
  <div class="col-sm-3"><img src="/images/fpose/7m.png" class="img-thumbnail" alt="mask"></div>
  <div class="col-sm-3"><img src="/images/fpose/7d.png" class="img-thumbnail" alt="depth"></div>
  <div class="col-sm-3"><img src="/images/fpose/7gt.png" class="img-thumbnail" alt="gt pose"></div>
</div> -->


<!-- 
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
</div> -->