---
title: 'A Brief Summary on Neural Style Transfer'
date: 2017-05-19
permalink: /posts/2017/05/blog-post-1/
tags:
  - Computer Vision
  - Neural Style Transfer
---

<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/1.png"  />
    <figcaption>Figure 1 Artistic Style Transfer. From left to right: content image, style image, transferred result.</figcaption>
</figure>

Neural Style Transfer is a fascinating yet mysterious area in computer vision. The opening paper by [Leon A. Gatys](https://arxiv.org/pdf/1508.06576.pdf) et al. was published at 2015. Since then, numerous progress has been made in this area, bringing more and more fascinating features as well as enlightenment about how and why it works. In this blog post, I would like to summary several papers on this topic to draw a brief sketch about the developments in recent years.

## Opening Paper

The opening paper [A Neural Algorithm of Artistic Style](https://arxiv.org/pdf/1508.06576.pdf) and [Image Style Transfer Using Convolutional Neural Networks](http://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf) were out at 2015. Thanks to the dramatic development on CNNs (Convolutional Neural Networks), Leon A. Gatys et al. were able to separately capture image content and style using pre-trained CNN for object recognition and transfer style from one image to the other.

**Task.** In neural style transfer, one provides two images, a content image (left in Figure 1) and a style image (middle in Figure 1). Then the style transfer algorithm combines the style of the style image and content of the content image to generate a new image(right in Figure 1). This requires the separately capture of image content and style.

**Capturing Image Content.** CNNs are known brilliant feature extractors. It captures low-level pixel information in shallow layers as well as high-level semantic information in deep layers. So to capture the image content information, it's sufficient to use the feature maps by CNNs to represent image content. So we can define the content loss as:

<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/2.png" height="50">
    <figcaption>Figure 2 Content Loss.</figcaption>
</figure>

In which $$\vec{p}$$ and $$\vec{x}$$ are the original image and the image that is generated.
