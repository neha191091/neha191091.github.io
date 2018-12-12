---
title: "human-segmentation"
collection: projects
permalink: /projects/human-segmentation
type: "Inter Disciplinary Project"
venue: "Chair of Computer Aided Medical Procedures, TUM"
location: "Munich"
---

This project is a consequence of an internal course requirement during my masters. Its goal is to segment human body parts from depth images. I compared my results on several different U-Net based models, with particular focus on high speed and accuracy.

This project obtains and preprocess the training data, trains the segmentation graph, and freezes the graph to a protobuf file for later inference in C++.


Further development of this work (not included in this repository) focused on combining the segmented depth maps using KinectFusion to provide a segmented 3D point cloud/mesh.
You can read a detailed report on this work [here](http://neha191091.github.io/files/Semantic_Segmentation_IDP_Report.pdf)

Find the project [here](https://github.com/neha191091/human-segmentation) on github.