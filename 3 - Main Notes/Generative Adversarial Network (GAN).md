
2026-04-08

Tags: [[Data Mining and Machine Learning]]
# Generative Adversarial Network (GAN)
## Basic
GAN's really don't fit into the supervised/unsupervised binary. Like Supervised Learning models, they learn to classify data based on labeled data. Instead of being used to classify unknown data, they are used to generate synthetic data that can pass for real data. Some example of self supervised learning models include wav2vec, Bidirectional Encoder Representations from Transformers (BERT), and OpenAI's GPT-3.

Generative adversarial networks (GANs) are machine learning models that use two neural networks, pitting one against the other (thus the “adversarial”) in order to generate new synthetic instances of data that can pass for real data. They are used widely in image generation, video generation, and voice generation.

![[Pasted image 20260408205314.png]]

## Discriminator Ex
One example of what a discriminator might look like in an image generation scenario is a Convolutional Neural Network. For the GAN Discriminator, the final layers are modified to make a binary decision of Real or Fake, or to output the probability that the input is $Real, p(Real) \in \{0,1\}$.

## Generator Ex
In the generator example within an image generation framework it might look like a deconvolutional network. A Deconvolutional Network takes a vector of random noise and up-samples it to an image. Before looking at how deconvolution works, let’s review how convolution works. Basically, normal convolution slides a kernel over an (blue) input space to produce a (green) smaller output space.
![[Pasted image 20260408210719.png]]
In this example we're scaling up a `3x3` image to a `5x5` by filling in the gaps.

As a sidenote there are a lot of terms for this process including Deconvolution, Transposed convolution , Full convolution , In-network upsampling , Fractionally-strided convolution , Backwards convolution , Upconvolution.


# References
- [[Supervised Learning*]]
- [[Neural Networks]]
- [[Clustering and Clustering Analysis*]]
- [[Convolutional Neural Networks]]