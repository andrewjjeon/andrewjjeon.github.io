---
layout: page
title: "Image Processing for Fisheye Camera Image Object Detection"
collection: projects
category: projects
image: /images/yolo/after2.png
order: 4
math: true
---

<div style="max-width: 1200px; margin: 0 auto; padding: 1rem;">
  <div class="card">
    <h1>Image Processing for Fisheye Camera Image Object Detection</h1>
    <h2>1. Introduction</h2>
      I participated in the 2024 AI City Challenge as part of a team from UW. Our team followed an ensemble learning approach where each person performed individual experiments and trained separate detectors. One person focused on finding additional fisheye camera image data, another focused on data augmentation, and I focused on image color transformation to improve detection. Specifically, a subset of the data was black&white images, and my job was to improve performance on them. I transformed my entire dataset to black&white images and trained yolov8 detectors on my transformed data. This resulted in performance improvements on the black&white validation data.
  </div>

  <div class="card">
    <h2>2. Image Transformation</h2>
      I followed a simple three step pipeline using OpenCV to transform my images to black & white.
      <ol>
        <li>Convert images to HSV</li>
        <li>Perform KMeans Clustering on HSV Images to split into colored vs black&white</li>
        <li>Transform Colored Images to Grayscale/Black&White</li>
      </ol>
  </div>

  <div class="card">
    <h2>3. Training and Evaluation of YOLO Detector</h2>
      I then use the Ultralytics package to load and train a yolov8m detector on the original dataset and my transformed dataset. I then trained and compared the validation set performance of the detector trained on the original data and the detector trained on my transformed data. There was a 10% improvement in mAP50-95 for all classes and a 6% improvement in mAP50 in model performance.

      <div align="center">
        <img src="images/yolo/yolo_results.png" width="400" />
        <p><em>Above: Performance of detector trained on original data. Below: Performance of detector trained on my transformed data.</em></p>
      </div>

      <div style="display: flex; justify-content: center; gap: 20px;">
        <div style="text-align: center;">
          <img src="images/yolo/before1.png" width="500"/>
          <p><em>Detector Trained on Original Data Inference</em></p>
        </div>

        <div style="text-align: center;">
          <img src="images/yolo/after1.png" width="500"/>
          <p><em>Detector Trained on Transformed Data Inference</em></p>
        </div>
      </div>

      <div style="display: flex; justify-content: center; gap: 20px;">
        <div style="text-align: center;">
          <img src="images/yolo/before2.png" width="500"/>
          <p><em>Detector Trained on Original Data Inference</em></p>
        </div>

        <div style="text-align: center;">
          <img src="images/yolo/after2.png" width="500"/>
          <p><em>Detector Trained on Transformed Data Inference</em></p>
        </div>
      </div>
  </div>
</div>