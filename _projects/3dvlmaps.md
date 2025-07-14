---
title: "3D Open Vocabulary Semantic Segmentation for Robot Navigation"
collection: projects
category: manuscripts
permalink: /projects/3dvlmaps/
image: /images/segresult.png
---


<h2>3D Open Vocabulary Semantic Segmentation for Robot Navigation</h2>

<p>
  VLMaps is a spatial map representation that embeds pretrained visual-language features with a 3D reconstruction and projects to a top-down 2D map. VLMaps embeds visual features from an LSeg visual encoder to points in a point cloud. These points are then projected to a top-down navigation map where only the point with the highest height is kept. After this, the visual features are compared through cosine similarity to textual features from a LSeg text encoder to determine the semantic label of the point. Due to the top-down projection, the robot wouldn't be capable of 3D navigation such as “go to the plant below the table.” 
  
  Further details can be found in <a href="https://vlmaps.github.io/" target="_blank">VLMaps</a>
</p>

<p>
  To address this limitation, I implemented a voxel grid projection by populating the voxel grid cells with their corresponding 
  points. When multiple points fall in the same voxel cell I average all their embeddings to generate a singular embedding. 
  This resulted in a best class segmentation accuracy of 0.907 and the robot being able to navigation in 3D as opposed to 2D.

</p>

<div style="text-align: center;">
  <img src="/images/3dvlmaps_block.jpg" alt="Block Diagram" style="max-width: 100%; height: auto;">
  <p>Block diagram of 3DVLMaps.</p>
</div>


<div style="text-align: center;">
  <div style="display: flex; justify-content: center; gap: 10px;">
    <img src="/images/segresult.png" alt="House 3D Segmentation Result" style="max-width: 49%; height: auto;">
    <img src="/images/3dvlmaps_key.png" alt="House 3D Segmentation Key" style="max-width: 49%; height: auto;">
  </div>
  <p>3D segmentation demonstration of household scene.</p>
</div>


<div style="text-align: center;">
  <div style="display: flex; justify-content: center; gap: 10px;">
    <img src="/images/realsofa.png" alt="Real Sofa" style="max-width: 49%; height: auto;">
    <img src="/images/seg_sofa.png" alt="Segmented Sofa" style="max-width: 49%; height: auto;">
  </div>
  <p>3D segmentation demonstration of sofa, comparison with real world point cloud</p>
</div>


<div style="text-align: center;">
  <div style="display: flex; justify-content: center; gap: 10px;">
    <img src="/images/table.png" alt="Table" style="max-width: 49%; height: auto;">
    <img src="/images/tableseg.png" alt="Segmented Table" style="max-width: 49%; height: auto;">
  </div>
  <p>3D segmentation demonstration of Table, comparison with real world point cloud</p>
</div>

<p>
  The couch segmentation had an accuracy of 0.827, the table had an accuracy of 0.832
</p>