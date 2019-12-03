---
layout: post
title:  "Short Summary: Box2Pix: Single-Shot Instance Segmentation by Assigning Pixels to Object Boxes"
author: "Tim Joseph"
tags: ["2d-detection", "instance segmentation", "single-shot", "short-summary"]
---

Jonas Uhrig, E. Rehder, B. Fröhlich, U. Franke, Thomas Brox (2018)

https://lmb.informatik.uni-freiburg.de/Publications/2018/UB18/paper-box2pix.pdf

## Problem

2D-Detection, Instance Segmentation

## Improvement over previous methods

* No post-processing necessary.

## Method 
Their method is similar to Single-Shot Multibox Detector with an extension for instance segmentation. They create bounding-box predictions with SSD, but add additionally deconvolution layers after the network (creating a U-Net) with a semantic segmentation output. Furthermore, they also predict a vector for each pixel that points to the center of that pixel's associated bounding-box. Each pixel that points sufficiently close to an object's bounding box center is assigned to this object resulting in the mask of the object.

![Visualization of different modalities.](/assets/images/box2pix.png)


## Implementation
They use GoogLeNet as backbone and make it a U-Net. For loss they punish the pixel-wise vector that points to the object center with the offset from the center. If a pixel lies outside of a predicted boy it is additionally punished with the with the distance to the closest bounding box. 

![Visualization of different modalities.](/assets/images/box2pix-architecture.png)
