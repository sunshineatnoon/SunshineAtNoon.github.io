---
title:          "TUVF: Learning Generalizable Texture UV Radiance Fields"
date:           2024-05-12 00:01:00 +0800
pub:            "International Conference on Learning Representations (ICLR)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
#pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2024"

abstract: >-
  Textures are a vital aspect of creating visually appealing and realistic 3D models. In this paper, we study the problem of generating high-fidelity texture given shapes of 3D assets, which has been relatively less explored compared with generic 3D shape modeling. Our goal is to facilitate a controllable texture generation process, such that one texture code can correspond to a particular appearance style independent of any input shapes from a category. We introduce Texture UV Radiance Fields (TUVF) that generate textures in a learnable UV sphere space rather than directly on the 3D shape. This allows the texture to be disentangled from the underlying shape and transferable to other shapes that share the same UV space, i.e., from the same category. We integrate the UV sphere space with the radiance field, which provides a more efficient and accurate representation of textures than traditional texture maps. We perform our experiments on synthetic and real-world object datasets where we achieve not only realistic synthesis but also substantial improvements over state-of-the-arts on texture controlling and editing.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - An-Chieh Cheng
  - Xueting Li
  - Sifei Liu
  - Xiaolong Wang
links:
  Code: https://github.com/AnjieCheng/TUVF
---
