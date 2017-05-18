---
title: 'A Brief Summary on Neural Style Transfer'
date: 2017-05-19
permalink: /posts/2017/05/blog-post-1/
tags:
  - Computer Vision
  - Neural Style Transfer
---
<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/Development.png"  height="200"/>
    <figcaption>Figure 1 A Brief Sketch about the Development of Neural Style Transfer in Recent Years.</figcaption>
</figure>

Neural Style Transfer is a fascinating yet mysterious area in computer vision. The opening paper by [Leon A. Gatys](https://arxiv.org/pdf/1508.06576.pdf) et al. was published at 2015. Since then, numerous progress has been made in this area, bringing more and more fascinating features as well as enlightenment about how and why it works. In this blog post, I would like to summary several papers on this topic to draw a brief sketch about the developments in recent years as shown in Figure 1.

## Opening Paper

<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/1.png"  />
    <figcaption>Figure 2 Artistic Style Transfer. From left to right: content image, style image, transferred result.</figcaption>
</figure>

The opening paper [A Neural Algorithm of Artistic Style](https://arxiv.org/pdf/1508.06576.pdf) and [Image Style Transfer Using Convolutional Neural Networks](http://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf) were out at 2015. Thanks to the dramatic development on CNNs (Convolutional Neural Networks), Leon A. Gatys et al. were able to separately capture image content and style using pre-trained CNN for object recognition and transfer style from one image to the other.

**Task.** In neural style transfer, one provides two images, a content image (left in Figure 2) and a style image (middle in Figure 2). Then the style transfer algorithm combines the style of the style image and content of the content image to generate a new image(right in Figure 2). This requires the separately capture of image content and style.

**Capturing Image Content.** CNNs are known as brilliant feature extractors. It captures low-level pixel information in shallow layers as well as high-level semantic information in deep layers. So to capture the image content information, it's sufficient to use the feature maps by CNNs to represent image content. Thus we define the content loss as the mean square distance between the feature maps:

$$L_{content}(\vec(p),\vec(x),l) = \frac{1}{2}\sum_{i,j}(F_{ij}^2 - P_{ij}^2)^2$$

In which $$\vec{p}$$ and $$\vec{x}$$ are the original image and the generated image. $$F$$ and $$P$$ are their feature maps from the pre-trained VGG net in layer $$l$$.

**Capturing Image Style.** Image style is a ill-posed definition. It's even hard to give a specific definition verbally. An intuition is that the style of a painting(or a painter) should be irrelevant to content as well as location, so one might use a statistics over the whole feature map to represent the style of an image. This introduces the Gram Matrix which is defined as:

$$G_{ij}^l = \sum_{k}F_{ik}^lF_{jk}^l$$

Given a $$C \times H \times W$$ feature map. Its corresponding Gram Matrix is a $$C \times C$$ matrix, with $$C_{ij}$$ computed as the element-wise product and summation across feature map in channel $$i$$ and channel $$j$$. So it can be interpreted as the correlation between feature map $$F_i$$ and $$F_j$$.

We define the style loss as a weighted sum of the mean square errors between the Gram Matrices computed in layer $$l_1, l_2, ..., l_n$$.

$$E_l = \frac{1}{4N_l^2M_l^2}\sum_{i,j}(G_{ij}^l - A_{ij}^l)^2$$

$$L_{style}(\vec{a},\vec{x}) = \sum_{l=0}^{l}w_lE_l$$

**Training.** The first Neural Style Transfer Algorithm is characterized as an optimization problem. Starting with a noise image, one feeds this image to the pre-train VGG net and calculate the style loss and content loss between this image and the style and content image respectively, then backpropagates the gradient all the way back to this noise image to push it closer to our target image. Repeating this optimization process many iterations, we shall get an image combining the content and style from the content image and style image. An example result is shown in Figure 2.

**Drawbacks.** This opening paper shows the a fantastic application of CNNs. Yet it tackles this problem by an optimization process, so it's inefficient and can't be applied in real world such as a phone APP. Also, why Gram Matrix can capture style of an image is kind of a myth to be revealed.

## Feed-Forward Style Transfer
<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/FeedForward.png"  />
    <figcaption>Figure 3 Network Architecture of Feed-Forward Style Transfer</figcaption>
</figure>

One issue about neural style transfer is that it needs many iterative optimization iterations to generate a transferred image. Johnson et al. tackled this problem by training a network to complete the style transfer task. Their network architecture is shown in Figure 3. Using the same style and content loss as the opening paper, their transformer network receives a content image $$x$$ and generate a target image $$\^{y}$$, $$\^{y}$$ as well as the style image $$y_s$$ and content image $$y_c$$ are then fed into the pre-trained VGG net to compute the style and content losses. Gradients from these two losses are back-propagated into the generated image and then used to train the transformer network. When testing, one only needs to feed the content image into the transformer network to get a transferred image. Thus the transfer task can be completed within one feed forward other than many feed-forward and backward iterations. 

## Reference
1. Gatys L A, Ecker A S, Bethge M. A neural algorithm of artistic style[J]. arXiv preprint arXiv:1508.06576, 2015.
2. Johnson J, Alahi A, Fei-Fei L. Perceptual losses for real-time style transfer and super-resolution[J]. arXiv preprint arXiv:1603.08155, 2016.
3. Li, Yanghao, et al. "Demystifying Neural Style Transfer." arXiv preprint arXiv:1701.01036 (2017).
4. Gatys, Leon A., et al. "Preserving color in neural artistic style transfer." arXiv preprint arXiv:1606.05897 (2016).
5. Gatys, Leon A., et al. "Controlling Perceptual Factors in Neural Style Transfer." arXiv preprint arXiv:1611.07865 (2016).
6. Dumoulin, Vincent, Jonathon Shlens, and Manjunath Kudlur. "A learned representation for artistic style." (2017).
7. Huang, Xun, and Serge Belongie. "Arbitrary Style Transfer in Real-time with Adaptive Instance Normalization." arXiv preprint arXiv:1703.06868 (2017).
