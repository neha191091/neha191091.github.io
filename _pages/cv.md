---
layout: archive
title: "Resume"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
### Doctoral Candidate, [Chair of Information Oriented Control, TUM](https://www.tum.de/en/), Oct 2020 - Present
- Supervised by Prof. Sandra Hirche
- Thesis: *Data-Driven Analysis of Human Motor Behavior for Medical Applications*
### MSc. Informatics, [Technical University of Munich](https://www.tum.de/en/), Aug 2019
- Thesis (Conducted at {Volkswagen Group AI Research, Germany}): *Learning State-Space Models of Camera-Based Robots for Intrinsically Motivated Control*
- Passed with High Distinction.
### BTech. Software Engineering, [Delhi Technological University](http://dtu.ac.in/), May 2013
- Final Project: *Tower Defense Game Implementing Bee Colony Algorithm*.
- First Division with Distinction.

Work experience
======
### Research Associate, Technical University of Munich, Germany, Oct 2020 - Present
- **Contributions to Horizon 2020 project [ReHyb](https://www.ce.cit.tum.de/itr/projekte/vergangene-projekte-1/h2020-project-rehyb/)**: 
  - Developed *explainable, data-driven* algorithms for detecting anomalous motion in stroke patients using *unsupervised anomaly detection* techniques and *generative modeling*.
  - Designed *inverse optimal control* methods to mitigate compensatory (abnormal motion by stroke patients) movements via robotic feedback.
  - Implemented a *data-driven* framework for enabling FES-assisted motion through *automatic detection of intended movements* from muscular activity.
  - Led *experimental studies* - protocol design, participant recruitment, and creation of web-based tools for motion data collection and labeling. Acquisition and processing of EMG-based, optical-marker and video-based datasets from healthy and post-stroke participants for model training and validation.
- **Contributions to Horizon 2020 project [ConPDMode](https://www.ce.cit.tum.de/itr/projekte/vergangene-projekte-1/h2020-erc-poc-project-con-pdmode/)**: 
  - Implemented and *compared machine learning models* (e.g., Gaussian Processes, ensemble, and deep networks) for Parkinson's Disease (PD) symptom severity classification from wearable IMU data and *Identified key challenges* in their application, including uncertainty estimation and data imbalance.
  - Proposed a *novel uncertainty quantification approach* for deep learning to detect data gaps via epistemic uncertainty estimation.
  - Designed methods to *address dataset imbalance* in PD symptom classification.
  - Designed the prototype for a web and mobile application for motion data visualization and PD symptom severity classification with interfaces for physicians and patients.
- **Contributions to Horizon 2020 project [CO-MAN](https://www.ce.cit.tum.de/itr/projekte/h2020-erc-consolidator-co-man/)**: 
  - Developed a safe, *user-preference–driven* navigation framework using *Preferential Bayesian Optimization*.
  - Contributed to designing a safe control approach for unknown dynamics with *Control Barrier Functions*.
- **Supervision experience**: 
  - Supervised over 15 undergraduate and graduate student thesis, as well as additional research and engineering practice projects
  - assisted with course organization, teaching, exam design and evaluation for several [courses](/teaching/).

### AI Resident, Meta, U.S.A, Sep 2019 - Oct 2020
- **Representation learning for robot manipulation**: Contributed to the design of an *extended body schema* of a robotic arm to enable manipulation of held tools from visual and proprioceptive inputs.
- **Model-Based Inverse Reinforcement Learning**: Developed an *inverse reinforcement learning* approach inspired by meta-learning, using gradient updates to *efficiently robot behaviors from visual demos by humans*.
- **Learning state-dependent losses for inverse-dynamics learning**: Demonstrated that meta-learning adaptive loss functions improves inverse-dynamics model learning for a robotic arm compared to conventional fixed-loss approaches.

### Software Developer, Epic Systems, U.S.A, Oct 2014 - Sep 2016
- Designed and implemented web-based interfaces for, as well as enhanced backend features of an EHR application supporting medical information summarization and diagnosis assistance.

### Software Developer in Test, Intel Security, India, Jul 2013 - Sep 2014
- Created a framework in C++ for stress testing a whitelisting product for Windows systems.
- White-box tested the whitelisting product.
  
Skills
======
- **Languages**: Python, MATLAB, Simulink, C++, JavaScript, CSS, SQL
- **Libraries**: Pytorch, Tensorflow, Scikit-learn, OpenCV, Pandas, Matplotlib, Blender
- **Tools**: OpenSim, Blender, Visdom, Figma
- **Concepts**: Machine Learning, Explainable AI, Inverse Optimal Control, Reinforcement Learning, Generative AI, Anomaly Detection, Probabilistic Graphical Models, Learning from Feedback, Human-centered AI, Large Language Models


Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

<!---
Talks
======
  <ul>{% for post in site.talks %}
    {% include archive-single-talk-cv.html %}
  {% endfor %}</ul>
--->
  
Teaching
======
  <ul>{% for post in site.teaching %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

  
