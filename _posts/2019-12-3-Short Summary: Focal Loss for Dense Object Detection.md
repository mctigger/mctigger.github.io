---
layout: post
title:  "Short Summary: Focal Loss for Dense Object Detection (2017)"
author: "Tim Joseph"
tags: ["2d-detection", "instance segmentation", "single-shot"]
---

**Authors**: Tsung-Yi Lin, Priya Goyal, Ross Girshick, Kaiming He,  Piotr Dollar


Link to paper: [https://arxiv.org/pdf/1708.02002.pdf](https://arxiv.org/pdf/1708.02002.pdf) 

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

$$FL(p_t) = -\alpha_t (1-p_t)^{\gamma} \log(p_t) $$

Gamma controls how much easily classified samples contribute to the loss. High gamma means less contribution and vice versa. Alpha is similar as in weighted cross-entropy and is a constant weighting factor for background-/foreground-samples.