---
layout: post
title:  "Short Summary: EfficientDet: Scalable and Efficient Object Detection"
author: "Tim Joseph"
tags: ["2d-detection", "multi-scale feature fusion", "short-summary"]
---

Mingxing Tan, Ruoming Pang, Quoc V. Le (2019)

https://arxiv.org/pdf/1911.09070.pdf

## Problem

2D-Detection, Multi-scale feature fusion


## Improvement over previous methods

* State of the art on Coco2017 detection
* Very small model with high accuracy

## Method 
They want to improve upon classical single-stage detectors (e.g. Single Shot Multibox Detector) by

1. efficient multi-scale feature fusion
2. model scaling (comparable to EfficientNet).

Efficient multi-scale feature fusion is achieved by using the BiFPN layer repeatedly. Since different features at different resolutions contribute differently to the new features a learnable channel-wise feature-weighting is introduced. 

For the model scaling they reuse the coefficients from EfficientNet and scale the BiFPN width and depth. They additionally scale the detection heads width similar to the BiFPN width, but scale the depth differently. Finally, input resolution is also scaled.

![Visualization of different modalities.](/assets/images/efficient-det.png)

## Implementation
Similar to SSD with EfficientNet as backbone.


