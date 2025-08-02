---
layout: page
title: "Evaluating Foundation Model Robot Pose Estimation with Synthetic Data Generation"
collection: projects
category: projects
image: /images/fpose/FposePanda100.gif
order: 1
math: true
---

<div style="max-width: 900px; margin: 0 auto; padding: 1rem;">
  <div class="card">
    <h1>Evaluating Foundation Model Robot Pose Estimation with Synthetic Data Generation</h1>
      Position and Orientation or "Pose" is a 4x4 matrix that defines the translation or "position" and rotation or "orientation" of an object. In this project, Robot Pose Estimation is useful because if you can accurately predict the two pose matrices for the robot and an object, you should be able to calculate a "relative grasp" transform that describes how the robot should position itself to grasp the object successfully.<br>
      
      <img src="/images/fpose/fp_block.JPG" alt="Block Diagram" style="width: 900px; height: auto;">

      $$T_R^O = T_C^O \times T_R^C$$

      $${T_C^R}^{-1} = T_R^C$$

      If you can perform accurate robot pose estimation using a foundation model that wasn't explicitly trained on your robot, you should be able to grasp items that the model wasn't trained on with robots the model wasn't trained on. The team that built <strong>FoundationPose</strong> had already proven it could work on household objects such as a mustard bottle and a driller. Proving that the foundation model, <strong>FoundationPose</strong> has this "Open-Vocabulary" capability on robot data it hadn't seen was my goal. If you are curious about how FoundationPose was trained and other details please refer to the original work: <a href="https://nvlabs.github.io/FoundationPose/" target="_blank">FoundationPose</a>
  </div>


  <div class="card">
    <h2>Synthetic Robot Data Generation</h2>
    <p>
    In order to predict pose correctly, FoundationPose needs several data inputs:
    </p>
    <ul>
      <li>RGB, Depth, Binary Mask Frames</li>
      <li>CAD Model <code>.obj</code></li>
      <li>Camera Intrinsics Matrix</li>
    </ul>
  
    <p>
    In addition, for evaluation purposes we also need:
    </p>
    <ul>
      <li>Camera Frame Pose Annotations (Ground Truth)</li>
    </ul>

    <p>
      I generated this data inside Pybullet by setting up the robot and a virtual camera inside Pybullet. I defined the virtual camera through a view matrix and a projection amtrix. The view matrix defines the world coordinates to camera coordinates transform while the projection matrix defines the 3D camera coordinates to 2D image coordinates transform. I then took photos of the robot rotating around a sphere. Next, I calculated the grouth truth robot pose annotations by getting the world frame pose, and using the view matrix to transform to camera frame pose. I also used the projection matrix to transform to image coordinates in order to actually visualize the ground truth pose annotations on our image data.
    </p>

    <ol>
      <li>Rendering a Robot inside of Pybullet:<br>
        <code>robot_id = p.loadURDF(robot.urdf)</code>
      </li>
      <li>Setting up a Virtual Camera and taking Images of the Robot: <br>
        <code>view_matrix = p.computeViewMatrix(camera_position, target_point, up_direction)</code><br>
        <code>projection_matrix = p.computeProjectionMatrixFOV(fov=60, aspect=(w/h), nearclip, farclip)</code><br>
        <code>image = p.getCameraImage(w, h, view_matrix, projection_matrix)</code>
      </li>
      <li>Getting Grouth Truth Pose Annotations:<br>
        <code>robot_world_pose = p.getLinkState(robot_id, link_index)</code><br>
        <code>robot_camera_pose = view_matrix.T @ robot_world_pose</code><br>
        <code>pose_image_coordinates = projection_matrix.T @ robot_camera_pose</code>
      </li>
    </ol>

    
    <h3>PyBullet Virtual Camera Frames</h3>
    <div style="display: flex; gap: 1rem; flex-wrap: wrap;">
      <img src="/images/fpose/7.png" alt="RGB" style="width: 22%;">
      <img src="/images/fpose/7m.png" alt="Mask" style="width: 22%;">
      <img src="/images/fpose/7d.png" alt="Depth" style="width: 22%;">
      <img src="/images/fpose/7gt.png" alt="GT Pose" style="width: 22%;">
    </div>
  </div>



  <div class="card">
    <h2>Evaluation</h2>
      Now, with my Synthetic Data, all that was left to do was to run FoundationPose on and get the robot pose estimates for my synthetic data. Once I had these predictions, I then evaluated against the pose annotations I generated earlier. However, there was one last additional transform I needed to perform here to make the poses line up reasonably. After much searching, I found that Pybullet follows the OpenGL coordinate system which defines the Y and Z axes to the inverse of how OpenCV defines them. Our foundation model or FoundationPose follows the OpenCV system while our synthetic data follows the OpenGL system. I therefore had to run my annotations through one last transform where I inversed the Y and Z axes so our pose predictions and annotations lined up reasonably well. Finally, I evaluated the Translation component of the pose with Euclidean Distance and the Rotation component with Angular/Geodesic Error. I got reasonably good results with translation error being less than 1mm off and rotation being less than 1 degree off.<br>
      
      <img src="/images/fpose/FposePanda100.gif" alt="Franka Panda Demo"><br>

      Rotation Error: <strong>0.674°</strong><br>
      Translation Error: <strong>0.655 mm</strong>
  </div>
</div>