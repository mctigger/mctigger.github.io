---
layout: post
title:  "Short Summary: Focal Loss for Dense Object Detection"
author: "Tim Joseph"
tags: ["2d-detection", "instance segmentation", "single-shot"]
---

Tsung-Yi Lin, Priya Goyal, Ross Girshick, Kaiming He,  Piotr Dollar (2017)

https://arxiv.org/pdf/1708.02002.pdf

## Problem

2D-Detection, Background-foreground class imbalance

## Improvement over previous methods

* State of the art on Coco2017 detection.
* New loss function for more efficient training.

## Method 

Single-stage detectors such as SSD lack a first stage in which a lot of proposals are discarded (e.g. non-maximum suppression after RPN in Faster-RCNN). Therefore, background examples dominate the training and make it inefficient. While techniques such as hard example mining are often used to mitigate this imbalance, in this paper instead a new loss function is introduced. The loss function is an extension of cross-entropy loss, but gives samples that are easily classified less weight.

## Implementation
The loss function is simply cross-entropy weighted with a term, that decreases exponentially for easily classified samples (i.e. samples that the network classifies correctly with high confidence). 

Focal loss:

![Visualization of different modalities.](/assets/images/focal-loss.png)

Gamma controls how much easily classified samples contribute to the loss. High gamma means less contribution and vice versa. Alpha is similar as in weighted cross-entropy and is a constant weighting factor for background-/foreground-samples.