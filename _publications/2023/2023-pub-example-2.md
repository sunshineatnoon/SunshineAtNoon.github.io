---
title:          "Affordance Diffusion: Synthesizing Hand-Object Interactions"
date:           2023-06-05 00:01:00 +0800
#selected:       true
pub:            "Computer Vision and Pattern Recognition (CVPR)"
pub_date:       "2023"
abstract: >-
  Recent successes in image synthesis are powered by large-scale diffusion models. However, most methods are currently limited to either text- or image-conditioned generation for synthesizing an entire image, texture transfer or inserting objects into a user-specified region. In contrast, in this work we focus on synthesizing complex interactions (ie, an articulated hand) with a given object. Given an RGB image of an object, we aim to hallucinate plausible images of a human hand interacting with it. We propose a two-step generative approach: a LayoutNet that samples an articulation-agnostic hand-object-interaction layout, and a ContentNet that synthesizes images of a hand grasping the object given the predicted layout. Both are built on top of a large-scale pretrained diffusion model to make use of its latent representation. Compared to baselines, the proposed method is shown to generalize better to novel objects and perform surprisingly well on out-of-distribution in-the-wild scenes of portable-sized objects. The resulting system allows us to predict descriptive affordance information, such as hand articulation and approaching orientation. 
#cover:          /assets/images/covers/cover1.jpg
authors:
- Yufei Ye
- Xueting Li
- Abhinav Gupta
- Shalini De Mello
- Stan Birchfield
- Jiaming Song
- Shubham Tulsiani
- Sifei Liu
links:
  Code: https://github.com/NVlabs/affordance_diffusion
---