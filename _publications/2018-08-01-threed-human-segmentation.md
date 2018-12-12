---
title: "3D Human Body Segmentation"
collection: publications
permalink: /publication/2018-08-01-threed-human-segmentation
excerpt: 'The work presented in this report is a part of an effort towards a tool that allows a real-time view into a patient's body for inter-operative guidance.'
date: 2018-08-01
paperurl: 'http://neha191091.github.io/files/Semantic_Segmentation_IDP_Report.pdf'
---
*Abstract*

Development of systems that are equipped to provide a view into a patient’s body
form an essential part of the technological advancements needed to improve medical 
diagnosis and reduce invasive surgery. While volumetric imaging of a patient’s
anatomy via Computed Tomography or Magnetic Resonance Imaging have achieved
this goal to an extent, there is a growing need for combining such medical data via
Augmented Reality Systems and Head Mounted Displays with the real-time view of
the patient’s form. Applications of such an implementation include surgery planning
and inter-operative guidance systems.

An essential component of an implementation of the aforementioned Medical Augmented Reality 
(MAR) System, would be a module that could segment patient’s form (obtained as a 3D Model) 
into its constituent body parts and identify the body part that corresponds to the volumetric
medical data so that the 2 models may be registered.

The implementation of this segmentation module is the main goal of this InterDisciplinary
Project. This is accomplished via first segmentating the depth maps obtained in the process 
of creating the patient’s 3D model using a Deep Convolutional Neural Network and then combining 
the labelled images via KinectFusion to obtain a segmented 3D Model.

[Download report here](http://neha191091.github.io/files/Semantic_Segmentation_IDP_Report.pdf)

Recommended citation: Das, Neha. (2018). Development of a system that allows for the semantic segmentation of a 3D model of a human body into its constituent parts.