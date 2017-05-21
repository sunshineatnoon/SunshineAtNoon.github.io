---
title: 'A Brief Summary on Neural Style Transfer'
date: 2017-05-19
permalink: /posts/2017/05/blog-post-1/
comments: true
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

One issue about neural style transfer is that it needs many optimization iterations to generate a transferred image. [Johnson et al](https://arxiv.org/pdf/1603.08155.pdf). tackled this problem by training a network to complete the style transfer task. Their network architecture is shown in Figure 3. Using the same style and content loss as the opening paper, their transformer network receives a content image $$x$$ and generates a target image $$\hat{y}$$, $$\hat{y}$$ as well as the style image $$y_s$$ and content image $$y_c$$ are then fed into the pre-trained VGG net to compute the style and content losses. Gradients from these two losses are back-propagated into the generated image and then used to train the transformer network. When testing, one only needs to feed the content image into the transformer network to get a transferred image. Thus the transfer task can be completed within one feed forward other than many feed-forward and backward iterations.

## Demystify Neural Style Transfer
Why does Gram Matrix work? [Li et al.](https://arxiv.org/pdf/1701.01036.pdf) proved that minimizing the style loss based on Gram Matrix is equivalent to minimizing the Maximum Mean Discrepancy with the second order polynomial kernel. Thus the essence of neural style transfer is to match the feature distributions between the style images and the generated images. Other than the Maximum Mean Discrepancy with the second order polynomial kernel, the optimization can also achieved by other kernels such as the linear kernel and Gaussian kernel.

Additionally, they also proposed a style loss by aligning the BN statistics (mean and standard deviation) of two feature maps between the style images and the generated images.

$$L_{style}^l = \frac{1}{N_l}((\mu_{F^l}^i - \mu_{S^l}^i)^2 - (\sigma_{F^l}^i - \sigma_{S^l}^i)^2)$$

where $$\mu_{F^l}^i$$ and $$\sigma_{F^l}^i$$ are the mean and standard deviation of the $$i^{th}$$ feature channel among all the positions of the feature map in the layer l for the generated image, while $$\mu_{S^l}^i$$ and $$\sigma_{S^l}^i$$ correspond to the style image. Image generated by minimizing the BN statistics based loss is shown in Figure 4. It has comparable performance with the Gram Matrix based loss.

<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/BN.png"  />
    <figcaption>Figure 4 Image generated by aligning the BN statistics.</figcaption>
</figure>

## Multi-style Transfer
Although fast neural style transfer accelerate the speed of Neural Style Transfer, one has to train a transformer network for each style. [Dumoulin et al.](https://arxiv.org/pdf/1610.07629.pdf) observed that the parameters $$\gamma$$ and $$\beta$$ in the [Instance Normalization](https://arxiv.org/abs/1607.08022) layer can shift and scale an activation $$z$$ specific to painting style $$s$$. Conventional Instance Normalization can be represented as :

$$z = {\gamma}(\frac{x - \mu}{\sigma}) + {\beta}$$

where $$x$$ is the feature map of the input content image from layer l, $$\mu$$ and $$\sigma$$ are $$x$$'s mean and standard deviation taken across spatial axes. $$\gamma$$ and $$\beta$$ are learned parameters to shift and scale this feature map.

While in the proposed method which was called Conditional Instance Normalization, $$\gamma$$ and $$\beta$$ are expanded to $$N \times C$$ matrix, with $$N$$ represents the number of styles and $$C$$ represents the channel number. To normalize $$x$$ to a specific style $$s$$, one just normalize $$x$$ as:

$$z = {\gamma}_s(\frac{x - \mu}{\sigma}) + {\beta}_s$$

where $${\gamma}_s$$ and $${\beta}_s$$ is the $$s^{th}$$ row of $$\gamma$$ and $$beta$$, specializing to represent style $$s$$. The process can be figured below:

<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/CIN.png"  />
    <figcaption>Figure 5 Conditional Instance Normalization.</figcaption>
</figure>

This paper confirms the observation from [Demystify Neural Style Transfer](#demystify-neural-style-ransfer) that the the Instance Normalization (A specific process of Batch Normalization when batch size equals to 1) statistics can indeed represent a style.

Another interesting paper is by [Chen et al.](https://arxiv.org/abs/1703.09210). They trained a feed-forward style transfer network on multiple styles by using Styles Bank. A style bank is a composition of multiple convolutional filters, with each corresponds explicitly to a style. To transfer an image into a specific style, the corresponding filter bank is operated on top of the intermediate feature embedding produced by a single auto-encoder. Their network architecture is shown in Figure 6:

<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/styleBank.png"  />
    <figcaption>Figure 6 Network Architecture of Styles Bank.</figcaption>
</figure>
## Arbitrary Style Transfer

A farther step towards Multi-style transfer is arbitrary style transfer. Although conditional instance normalization can enable a transformer network to learn multiple styles, the transformer network's capability has to increase as the number of styles it captures. A super goal of style transfer is that given a content image as well as a style image, one can get the transferred image within a single feed-forward process without a pre-trained transformer network on this style. [Xun et al.](https://arxiv.org/abs/1703.06868) proposed Adaptive Instance Normalization to achieve this. What we know from [Multi-style Transfer](#multi-style-transfer) is that the $$\gamma$$ and $$\beta$$ in the Instance Normalization layer can shift and scale an activation $$z$$ specific to painting style $$s$$. So why not just shift and scale the content image's feature map to align with the style image in the training process ? This Adaptive Instance Normalization does exactly this:

$$AdaIN(x,y) = \sigma(y)(\frac{x-\mu(x)}{\sigma(x)}) + \mu(y)$$

where $$x$$ is the feature map of the input content image. $$\mu(x)$$, $$\mu(y)$$ and $$\sigma(x)$$, $$\sigma(y)$$ are the mean and standard deviation of $$x$$ and style image $$y$$.

Their network architecture is slightly different from the feed-forward style transfer and multi-style-transfer transfer. The encoder is composed of few layers of a fixed VGG-19 network. An AdaIN layer is used to perform style transfer in the feature space. A decoder is learned to invert the AdaIN output to the image spaces.

<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/AdaIN.png"  />
    <figcaption>Figure 6 Network Architecture of Arbitrary Style Transfer.</figcaption>
</figure>

## Controllable Style Transfer

The last line of style transfer I would like to go through is style transfer that preserving color or other controllable factors such as brush stroke. I will mainly talk about color preserving, details about other controllable factors can be found in [Preserving color in neural artistic style transfer](https://arxiv.org/abs/1611.07865). Color preserving style transfer means to preserve the color in content image while transfer the texture style from the style image to the content image. There are two approaches proposed by [Gatys et al.](https://arxiv.org/abs/1606.05897). The first one is that for the style image $$S$$ , first use color histogram matching algorithm to generate a new style image $$S'$$ which matches the color histogram of the content image. Then use $$S'$$ as the style image and perform conventional neural style transfer algorithm with content image $$C$$. The other approach is to perform style transfer only in the luminance channel, then concatenate generated luminance channel with I and Q channel from the content image. Results are shown in Figure 7. From my own experience, the luminance-only style transfer performs better than the histogram matching algorithm since the latter one relies on how histogram matching algorithm works.

<figure>
    <img src="/assets/posts/2017-05-19-a-brief-summary-on-neural-style-transfer/colorPreserving.png"  />
    <figcaption>Figure 7 Results of Color Preserving Style Transfer.</figcaption>
</figure>

## References
1. Gatys L A, Ecker A S, Bethge M. A neural algorithm of artistic style[J]. arXiv preprint arXiv:1508.06576, 2015.
2. Johnson J, Alahi A, Fei-Fei L. Perceptual losses for real-time style transfer and super-resolution[J]. arXiv preprint arXiv:1603.08155, 2016.
3. Li, Yanghao, et al. "Demystifying Neural Style Transfer." arXiv preprint arXiv:1701.01036 (2017).
4. Gatys, Leon A., et al. "Preserving color in neural artistic style transfer." arXiv preprint arXiv:1606.05897 (2016).
5. Gatys, Leon A., et al. "Controlling Perceptual Factors in Neural Style Transfer." arXiv preprint arXiv:1611.07865 (2016).
6. Dumoulin, Vincent, Jonathon Shlens, and Manjunath Kudlur. "A learned representation for artistic style." (2017).
7. Huang, Xun, and Serge Belongie. "Arbitrary Style Transfer in Real-time with Adaptive Instance Normalization." arXiv preprint arXiv:1703.06868 (2017).
