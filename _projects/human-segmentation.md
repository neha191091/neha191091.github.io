---
title: "Semantic Segmentation of human depth images"
collection: projects
permalink: /projects/human-segmentation
type: "Inter Disciplinary Project"
venue: "Chair of Computer Aided Medical Procedures, TUM"
location: "Munich"
code: https://github.com/neha191091/human-segmentation
report: http://neha191091.github.io/files/Semantic_Segmentation_IDP_Report.pdf
---

This project is the consequence of an internal course requirement during my masters. 
The goal of this project, on its own, is to segment human body parts from depth images. 
Results from several different U-Net based models are compared in this work, with 
particular focus on high speed and accuracy.

Provided in this project are functions to obtain and preprocess the training data, 
train the segmentation graph, and freezes the graph to a protobuf file for later 
inference in C++.

Further development of this work (not included in this repository) focuses on combining 
the segmented depth maps using KinectFusion to provide a segmented 3D point cloud/mesh. 
This segmented 3D model of the human body was used in collaboration with some other techniques
to provide a view into a patient's body.

A detailed report on this work can be found in the link below.