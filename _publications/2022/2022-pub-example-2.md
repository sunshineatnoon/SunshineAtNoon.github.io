---
title:          "Scraping Textures from Natural Images for Synthesis and Editing"
date:           2022-10-12 00:01:00 +0800
pub:            "European Conference on Computer Vision (ECCV)"
# pub_pre:        "Submitted to "
# pub_post:       'Under review.'
pub_date:       "2022"

abstract: >-
  Existing texture synthesis methods focus on generating large texture images given a small texture sample. But such samples are typically assumed to be highly curated: rectangular, clean, and stationary. This paper aims to scrape textures directly from natural images of everyday objects and scenes, build texture models, and employ them for texture synthesis, texture editing, etc. The key idea is to jointly learn image grouping and texture modeling. The image grouping module discovers clean texture segments, each of which is represented as a texture code and a parametric sine wave by the texture modeling module. By enforcing the model to reconstruct the input image from the texture codes and sine waves, our model can be learned via self-supervision on a set of cluttered natural images, without requiring any form of annotation or clean texture images. We show that the learned texture features capture many natural and man-made textures in real images, and can be applied to tasks like texture synthesis, texture editing and texture swapping.
#cover:          /assets/images/covers/cover3.jpg
authors:
  - Xueting Li
  - Xiaolong Wang
  - Ming-Hsuan Yang
  - Alexei A. Efros
  - Sifei Liu
links:
  PDF: https://www.ecva.net/papers/eccv_2022/papers_ECCV/papers/136750389.pdf
---
