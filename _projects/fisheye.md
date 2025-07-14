---
title: "Image Processing for Fisheye Camera Image Object Detection"
collection: projects
category: manuscripts
image: /images/after2.png
---


<h2>Image Processing for Fisheye Camera Image Object Detection</h2>

<p>
  My team and I participated in the 2024 AI City Challenge Track 4 Fisheye Camera Object Detection Challenge. Fisheye cameras have a wide field of view, which allows them to capture wider scenes, but comes with image distortion that can impede computer vision tasks. My main contribution to our team ensemble learning solution was using OpenCV image processing to transform the full training set of colored + nighttime images to all black&white and retraining the YOLO model on the transformed dataset. This resulted in 9% improved mAP object detection performance on night-time images in the test set.
</p>

<p>
  Specifically, the images below powerfully show the improvement in performance my black&white image transformation and subsequent retraining achieved.
</p>


  <div style="text-align: center;">
    <div style="display: flex; justify-content: center; gap: 10px;">
      <img src="/images/before1.jpg" alt="Original Model Detections" style="max-width: 40%; height: auto;">
      <img src="/images/after1.jpg" alt="Transformed Image Trained Model Detections" style="max-width: 40%; height: auto;">
    </div>
    <p>Original model detections vs Transformed Image model detections</p>
  </div>
  
  
  <div style="text-align: center;">
    <div style="display: flex; justify-content: center; gap: 10px;">
      <img src="/images/before2.png" alt="Original Model Detections" style="max-width: 40%; height: auto;">
      <img src="/images/after2.png" alt="Transformed Image Trained Model Detections" style="max-width: 40%; height: auto;">
    </div>
    <p>Original model detections vs Transformed Image model detections</p>
  </div>