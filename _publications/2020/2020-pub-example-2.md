---
title:          "Online Adaptation for Consistent Mesh Reconstruction in the Wild"
date:           2020-12-12 00:01:00 +0800
pub:            "Neural Information Processing Systems (NeurIPS)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
pub_date:       "2020"

abstract: >-
  This paper presents an algorithm to reconstruct temporally consistent 3D meshes of deformable object instances from videos in the wild. Without requiring annotations of 3D mesh, 2D keypoints, or camera pose for each video frame, we pose videobased reconstruction as a self-supervised online adaptation problem applied to any incoming test video. We first learn a category-specific 3D reconstruction model from a collection of single-view images of the same category that jointly predicts the shape, texture, and camera pose of an image. Then, at inference time, we adapt the model to a test video over time using self-supervised regularization terms that exploit temporal consistency of an object instance to enforce that all reconstructed meshes share a common texture map, a base shape, as well as parts. We demonstrate that our algorithm recovers temporally consistent and reliable 3D structures from videos of non-rigid objects including those of animals captured in the wild – an extremely challenging task rarely addressed before.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Xueting Li
  - Sifei Liu
  - Shalini De Mello
  - Kihwan Kim
  - Xiaolong Wang
  - Ming-Hsuan Yang
  - Jan Kautz
links:
  Arxiv: https://arxiv.org/abs/2012.03196
---
