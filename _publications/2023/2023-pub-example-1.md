---
title:          "Zero-shot Pose Transfer for Unrigged Stylized 3D Characters"
date:           2023-06-05 00:01:00 +0800
#selected:       true
pub:            "Computer Vision and Pattern Recognition (CVPR)"
pub_date:       "2023"
abstract: >-
  Transferring the pose of a reference avatar to stylized 3D characters of various shapes is a fundamental task in computer graphics. Existing methods either require the stylized characters to be rigged, or they use the stylized character in the desired pose as ground truth at training. We present a zero-shot approach that requires only the widely available deformed non-stylized avatars in training, and deforms stylized characters of significantly different shapes at inference. Classical methods achieve strong generalization by deforming the mesh at the triangle level, but this requires labelled correspondences. We leverage the power of local deformation, but without requiring explicit correspondence labels. We introduce a semi-supervised shape-understanding module to bypass the need for explicit correspondences at test time, and an implicit pose deformation module that deforms individual surface points to match the target pose. Furthermore, to encourage realistic and accurate deformation of stylized characters, we introduce an efficient volume-based test-time training procedure. Because it does not need rigging, nor the deformed stylized character at training time, our model generalizes to categories with scarce annotation, such as stylized quadrupeds. Extensive experiments demonstrate the effectiveness of the proposed method compared to the state-of-the-art approaches trained with comparable or more supervision. 
#cover:          /assets/images/covers/cover1.jpg
authors:
- Jiashun Wang
- Xueting Li
- Sifei Liu
- Shalini De Mello
- Orazio Gallo
- Xiaolong Wang
- Jan Kautz
links:
  Arix: https://arxiv.org/abs/2306.00200
---