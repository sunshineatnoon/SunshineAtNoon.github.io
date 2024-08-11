---
title:          "Physics-based Indirect Illumination for Inverse Rendering"
date:           2024-03-12 00:01:00 +0800
selected:       true
pub:            "International Conference on 3D Vision (3DV)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
#pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2024"

abstract: >-
  We present a physics-based inverse rendering method that learns the illumination, geometry, and materials of a scene from posed multi-view RGB images. To model the illumination of a scene, existing inverse rendering works either completely ignore the indirect illumination or model it by coarse approximations, leading to sub-optimal illumination, geometry, and material prediction of the scene. In this work, we propose a physics-based illumination model that first locates surface points through an efficient refined sphere tracing algorithm, then explicitly traces the incoming indirect lights at each surface point based on reflection. Then, we estimate each identified indirect light through an efficient neural network. Moreover, we utilize the Leibniz's integral rule to resolve non-differentiability in the proposed illumination model caused by boundary lights inspired by differentiable irradiance in computer graphics. As a result, the proposed differentiable illumination model can be learned end-to-end together with geometry and materials estimation. As a side product, our physics-based inverse rendering model also facilitates flexible and realistic material editing as well as relighting. Extensive experiments on synthetic and real-world datasets demonstrate that the proposed method performs favorably against existing inverse rendering methods on novel view synthesis and inverse rendering.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Youming Deng
  - Xueting Li
  - Sifei Liu
  - Ming-Hsuan Yang
links:
  Code: https://github.com/denghilbert/3DV2024-Physics-based-Indirect-Illumination-for-Inverse-Rendering
---
