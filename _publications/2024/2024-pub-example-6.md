---
title:          "3D Reconstruction with Generalizable Neural Fields using Scene Priors"
date:           2024-10-12 00:01:00 +0800
pub:            "International Conference on Learning Representations (ICLR)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
#pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2024"

abstract: >-
  High-fidelity 3D scene reconstruction has been substantially advanced by recent progress in neural fields. However, most existing methods train a separate network from scratch for each individual scene. This is not scalable, inefficient, and unable to yield good results given limited views. While learning-based multi-view stereo methods alleviate this issue to some extent, their multi-view setting makes it less flexible to scale up and to broad applications. Instead, we introduce training generalizable Neural Fields incorporating scene Priors (NFPs). The NFP network maps any single-view RGB-D image into signed distance and radiance values. A complete scene can be reconstructed by merging individual frames in the volumetric space WITHOUT a fusion module, which provides better flexibility. The scene priors can be trained on large-scale datasets, allowing for fast adaptation to the reconstruction of a new scene with fewer views. NFP not only demonstrates SOTA scene reconstruction performance and efficiency, but it also supports single-image novel-view synthesis, which is underexplored in neural fields.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Yang Fu
  - Shalini De Mello
  - Xueting Li
  - Amey Kulkarni
  - Jan Kautz
  - Xiaolong Wang
  - Sifei Liu
links:
  Arxiv: https://arxiv.org/abs/2309.15164v2
---
