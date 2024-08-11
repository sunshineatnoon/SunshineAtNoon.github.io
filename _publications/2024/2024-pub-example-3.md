---
title:          "A unified approach for text-and image-guided 4d scene generation"
date:           2024-06-12 00:01:00 +0800
pub:            "Conference on Computer Vision and Pattern Recognition (CVPR)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
#pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2024"

abstract: >-
  Large-scale diffusion generative models are greatly simplifying image video and 3D asset creation from user provided text prompts and images. However the challenging problem of text-to-4D dynamic 3D scene generation with diffusion guidance remains largely unexplored. We propose Dream-in-4D which features a novel two-stage approach for text-to-4D synthesis leveraging (1) 3D and 2D diffusion guidance to effectively learn a high-quality static 3D asset in the first stage;(2) a deformable neural radiance field that explicitly disentangles the learned static asset from its deformation preserving quality during motion learning; and (3) a multi-resolution feature grid for the deformation field with a displacement total variation loss to effectively learn motion with video diffusion guidance in the second stage. Through a user preference study we demonstrate that our approach significantly advances image and motion quality 3D consistency and text fidelity for text-to-4D generation compared to baseline approaches. Thanks to its motion-disentangled representation Dream-in-4D can also be easily adapted for controllable generation where appearance is defined by one or multiple images without the need to modify the motion learning stage. Thus our method offers for the first time a unified approach for text-to-4D image-to-4D and personalized 4D generation tasks.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Yufeng Zheng
  - Xueting Li
  - Koki Nagano
  - Sifei Liu
  - Otmar Hilliges
  - Shalini De Mello
links:
  Code: https://github.com/NVlabs/dream-in-4d
---
