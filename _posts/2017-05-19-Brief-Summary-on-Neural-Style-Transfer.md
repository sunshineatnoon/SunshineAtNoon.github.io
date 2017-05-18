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

**Capturing Image Content.** CNNs are known as brilliant feature extractors. It captures low-level pixel information in shallow layers as well as high-level semantic information in deep layers. So to capture the image content information, it's sufficient to use the feature maps by CNNs to represent image content. Thus we define the content loss as the mean square distance between the feature maps:

$$L_{content}(\vec(p),\vec(x),l) = \frac{1}{2}\sum_{i,j}(F_{ij}^2 - P_{ij}^2)^2$$

In which $$\vec{p}$$ and $$\vec{x}$$ are the original image and the generated image. $$F$$ and $$P$$ are their feature maps from the pre-trained VGG net in layer $$l$$.

**Capturing Image Style.** Image style is a ill-posed definition. It's even hard to give a specific definition verbally. An intuition is that the style of a painting(or a painter) should be irrelevant to content as well as location, so one might use a statistics over the whole feature map to represent the style of an image. This introduces the Gram Matrix which is defined as:

$$G_{ij}^l = \sum_{k}F_{ik}^lF_{jk}^l$$

Given a $C \times H \times W$ feature map. Its corresponding Gram Matrix is a $$C \times C$$ matrix, with $$C_{ij}$$ computed as the element-wise product and summation across feature map in channel $$i$$ and channel $$j$$. So it can be interpreted as the correlation between feature map $$F_i$$ and $$F_j$$.

We define the style loss between two images as a weighted sum of the mean square errors between their Gram Matrix computed in layer $$l_1, l_2, ..., l_n$$.

$$E_l = \frac{1}{4N_l^2M_l^2}\sum_{i,j}(G_{ij}^l - A_{ij}^l)^2$$
$$L_{style}(\vec{a},\vec{x}) = \sum_{l=0}{l}w_lE_l$$
