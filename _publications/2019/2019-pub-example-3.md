---
title:          "Joint-task Self-supervised Learning for Temporal Correspondence"
date:           2019-06-12 00:01:00 +0800
pub:            "Neural Information Processing Systems (NeurIPS)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2019"

abstract: >-
  This paper proposes to learn reliable dense correspondence from videos in a self-supervised manner. Our learning process integrates two highly related tasks: tracking large image regions and establishing fine-grained pixel-level associations between consecutive video frames. We exploit the synergy between both tasks through a shared inter-frame affinity matrix, which simultaneously models transitions between video frames at both the region- and pixel-levels. While region-level localization helps reduce ambiguities in fine-grained matching by narrowing down search regions; fine-grained matching provides bottom-up features to facilitate region-level localization. Our method outperforms the state-of-the-art self-supervised methods on a variety of visual correspondence tasks, including video-object and part-segmentation propagation, keypoint tracking, and object tracking. Our self-supervised method even surpasses the fully-supervised affinity feature representation obtained from a ResNet-18 pre-trained on the ImageNet.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Xueting Li
  - Sifei Liu
  - Shalini De Mello
  - Xiaolong Wang
  - Jan Kautz
  - Ming-Hsuan Yang
links:
  Code: https://github.com/Liusifei/UVC
---
