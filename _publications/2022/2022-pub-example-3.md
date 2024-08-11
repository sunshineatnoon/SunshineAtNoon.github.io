---
title:          "Autoregressive 3D Shape Generation via Canonical Mapping"
date:           2022-10-12 00:01:00 +0800
pub:            "International Conference on Learning Representations (ICLR)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2022"

abstract: >-
  With the capacity of modeling long-range dependencies in sequential data, transformers have shown remarkable performances in a variety of generative tasks such as image, audio, and text generation. Yet, taming them in generating less structured and voluminous data formats such as high-resolution point clouds have seldom been explored due to ambiguous sequentialization processes and infeasible computation burden. In this paper, we aim to further exploit the power of transformers and employ them for the task of 3D point cloud generation. The key idea is to decompose point clouds of one category into semantically aligned sequences of shape compositions, via a learned canonical space. These shape compositions can then be quantized and used to learn a context-rich composition codebook for point cloud generation. Experimental results on point cloud reconstruction and unconditional generation show that our model performs favorably against state-of-the-art approaches. Furthermore, our model can be easily extended to multi-modal shape completion as an application for conditional shape generation.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - An-Chieh Cheng
  - Xueting Li
  - Sifei Liu
  - Min Sun
  - Ming-Hsuan Yang
links:
  Code: https://github.com/AnjieCheng/CanonicalVAE
---
