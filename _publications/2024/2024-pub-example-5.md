---
title:          "Pyramid Diffusion for Fine 3D Large Scene Generation"
date:           2024-10-12 00:01:00 +0800
pub:            "European Conference on Computer Vision (ECCV)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
#pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2024"

abstract: >-
  Diffusion models have shown remarkable results in generating 2D images and small-scale 3D objects. However, their application to the synthesis of large-scale 3D scenes has been rarely explored. This is mainly due to the inherent complexity and bulky size of 3D scenery data, particularly outdoor scenes, and the limited availability of comprehensive real-world datasets, which makes training a stable scene diffusion model challenging. In this work, we explore how to effectively generate large-scale 3D scenes using the coarse-to-fine paradigm. We introduce a framework, the Pyramid Discrete Diffusion model (PDD), which employs scale-varied diffusion models to progressively generate high-quality outdoor scenes. Experimental results of PDD demonstrate our successful exploration in generating 3D scenes both unconditionally and conditionally. We further showcase the data compatibility of the PDD model, due to its multi-scale architecture: a PDD model trained on one dataset can be easily fine-tuned with another dataset.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Yuheng Liu
  - Xinke Li
  - Xueting Li
  - Lu Qi
  - Chongshou Li
  - Ming-Hsuan Yang
links:
  Code: https://github.com/yuhengliu02/pyramid-discrete-diffusion
---
