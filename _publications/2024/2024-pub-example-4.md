---
title:          "Gavatar: Animatable 3d gaussian avatars with implicit mesh learning"
date:           2024-03-12 00:01:00 +0800
selected:       true
pub:            "Conference on Computer Vision and Pattern Recognition (CVPR)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
#pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2024"

abstract: >-
  Gaussian splatting has emerged as a powerful 3D representation that harnesses the advantages of both explicit (mesh) and implicit (NeRF) 3D representations. In this paper we seek to leverage Gaussian splatting to generate realistic animatable avatars from textual descriptions addressing the limitations (eg efficiency and flexibility) imposed by mesh or NeRF-based representations. However a naive application of Gaussian splatting cannot generate high-quality animatable avatars and suffers from learning instability; it also cannot capture fine avatar geometries and often leads to degenerate body parts. To tackle these problems we first propose a primitive-based 3D Gaussian representation where Gaussians are defined inside pose-driven primitives to facilitate animations. Second to stabilize and amortize the learning of millions of Gaussians we propose to use implicit neural fields to predict the Gaussian attributes (eg colors). Finally to capture fine avatar geometries and extract detailed meshes we propose a novel SDF-based implicit mesh learning approach for 3D Gaussians that regularizes the underlying geometries and extracts highly detailed textured meshes. Our proposed method GAvatar enables the large-scale generation of diverse animatable avatars using only text prompts. GAvatar significantly surpasses existing methods in terms of both appearance and geometry quality and achieves extremely fast rendering (100 fps) at 1K resolution.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Ye Yuan*
  - Xueting Li*
  - Yangyi Huang
  - Shalini De Mello
  - Koki Nagano
  - Jan Kautz
  - Umar Iqbal
links:
  Arxiv: https://arxiv.org/abs/2312.11461
---
