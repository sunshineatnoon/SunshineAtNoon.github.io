---
title:          "Self-supervised Single-view 3D Reconstruction"
date:           2020-10-12 00:01:00 +0800
selected:       true
pub:            "European Conference on Computer Vision (ECCV)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2020"

abstract: >-
  We learn a self-supervised, single-view 3D reconstruction model that predicts the 3D mesh shape, texture and camera pose of a target object with a collection of 2D images and silhouettes. The proposed method does not necessitate 3D supervision, manually annotated keypoints, multi-view images of an object or a prior 3D template. The key insight of our work is that objects can be represented as a collection of deformable parts, and each part is semantically coherent across different instances of the same category (e.g., wings on birds and wheels on cars). Therefore, by leveraging self-supervisedly learned part segmentation of a large collection of category-specific images, we can effectively enforce semantic consistency between the reconstructed meshes and the original images. This significantly reduces ambiguities during joint prediction of shape and camera pose of an object, along with texture. To the best of our knowledge, we are the first to try and solve the single-view reconstruction problem without a category-specific template mesh or semantic keypoints. Thus our model can easily generalize to various object categories without such labels, e.g., horses, penguins, etc. Through a variety of experiments on several categories of deformable and rigid objects, we demonstrate that our unsupervised method performs comparably if not better than existing category-specific reconstruction methods learned with supervision.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Xueting Li
  - Sifei Liu
  - Kihwan Kim
  - Shalini De Mello
  - Varun Jampani
  - Ming-Hsuan Yang
  - Jan Kautz
links:
  Code: https://github.com/NVlabs/UMR
---
