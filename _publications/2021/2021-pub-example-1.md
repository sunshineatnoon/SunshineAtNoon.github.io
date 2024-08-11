---
title:          "Learning 3D Dense Correspondence via Canonical Point Autoencoder"
date:           2020-10-12 00:01:00 +0800
pub:            "Neural Information Processing Systems (NeurIPS)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
pub_last:       ' <span class="badge badge-pill badge-publication badge-success">Spotlight</span>'
pub_date:       "2021"

abstract: >-
  We propose a canonical point autoencoder (CPAE) that predicts dense correspondences between 3D shapes of the same category. The autoencoder performs two key functions: (a) encoding an arbitrarily ordered point cloud to a canonical primitive, e.g., a sphere, and (b) decoding the primitive back to the original input instance shape. As being placed in the bottleneck, this primitive plays a key role to map all the unordered point clouds on the canonical surface and to be reconstructed in an ordered fashion. Once trained, points from different shape instances that are mapped to the same locations on the primitive surface are determined to be a pair of correspondence. Our method does not require any form of annotation or selfsupervised part segmentation network and can handle unaligned input point clouds within a certain rotation range. Experimental results on 3D semantic keypoint transfer and part segmentation transfer show that our model performs favorably against state-of-the-art correspondence learning methods. 
#cover:          /assets/images/covers/cover3.jpg
authors:
  - An-Chieh Cheng
  - Xueting Li 
  - Min Sun
  - Ming-Hsuan Yang
  - Sifei Liu
links:
  Code: https://github.com/AnjieCheng/CanonicalPAE
---
