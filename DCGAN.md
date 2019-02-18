Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Network (DCGAN) Summary

Contribution
1. This paper introduces a version of GAN called Deep Convolutional Generative Adversarial Networks (DCGAN), which are stable to train in most settings.
2. This paper also showed that the generators have vector arithmetic properties which allows for easy image manipulation.

Background
1. GAN
2. Convolutional Neural Network: A convolutional neural network (CNN) is a class of deep, feed-forward artificial neural networks, most commonly applied to analyzing visual imagery.
3. Batch Normalization: Batch normalization helps stabilize learning by normalizing the inputs to each unit to have zero mean and unit variance.
4. ReLU Activation: ReLU (Rectified Linear Unit) is an activation function where f(x) = 0 for x<0 and f(x) = x for x>=0.
5. LeakyReLU Activation: LeakyReLU is an activation function where f(x)=⍺x for x<0 and f(x)=x for x>=0. Here ⍺ is called leak and it helps increase the range of ReLU function.
6. Dropout: Dropout refers to dropping out units from layers in the neural network. This is done for reducing overfitting in neural networks.

Description
1. Previous attempts to improve the performance of GANs to model images, using CNNs were unsuccessful.
2. This paper tells us about the various layers and activations used by the authors in their network, for successfuly modelling image distributions.
3. The various settings and hyperparameters used by the authors, and their effects on the result, are also mentioned in the paper.

Methodology
1. A uniform noise distribution z is fed into the first layer of the generator, which can be a fully connected layer.
2. This layer is used for matrix multiplication, and the result is reshaped into a 4-dimensional vector.
3. For the discriminator, the last layer is flattened and then fed into a single sigmoid output.
4. Pooling layers are replaced with strided convolutions for discriminator, and with fractional-strided convolutionals for the generator.
5. To prevent mode collapse, Batch Normalization has been used.
6. Batch Normalization is not applied to the output layer of the generator and the input layer of the discriminator, as it may lead to sample oscillations and also model instability.
7. The generator uses ReLU activations for all layers except the output, which uses Tanh.
8. The discriminator uses LeakyReLU activations for all layers.
9. Dropout was used to decrease the likelihood of memorization.

---------------------------

Introduction

GANs provide an attractive alternative to maximum, likelihood techniques. One can additionally argue that their learning process and the lack of a heuristic cost function (such as pixel-wise independent mean-square-error) are attractive to representation learning.

GANs have been known to be unstable to train, often resulting in generators that produce nonsensical outputs. There has been very limited published research in trying to understand and visualize what GANs learn, and the intermediate representations of multi-layer GANs.

Architecture guidelines for stable Deep Convolutional GANs
- Replace any pooling layers with strided convolutions (discriminator) and fractional-strided convolutions (generator)
- Use batchnorm in both the generator and the discriminator.
- Remove fully connected hidden layers for deeper architectures.
- Use ReLU activation in generator for all layers except for the output, which use Tanh.
- Use LeakyReLU activation in the discriminator for all alyers.

This paper introduces various techniques for successful learning:
1. Convert max-pooling layers to convolution layers.
2. Convert fully connected layers to global average pooling layers in the discriminator.
3. Use batch normalization alyers in the generator and the discriminator
4. Use LeakyReLU activation functions in the discriminator.

--------------------------------

DCGAN: Convolutional and Deconvolution
- To use DCGAN, we should know
	1. Convolution
	2. Deconvolution
- Convolution in discriminator
	- To check whether the generated data is real or not.
	- More specifically, to check whether the generated data captures the key (abstract) features of the input data.
- Deconvolution in generator
	- Unsampling
- Pooling and unpooling are not needed in DCGAN

A GAN takes the idea of using a generator model to generate fake examples and a discriminator model that tries to decide if the image it receives is a fake (i.e. from the generator) or a real sample. This was originally shown with relatively simple fully connected networks.

A DCGAN does something very similar, but specifically focus on using deep convolutional networks in place of those fully connected networks. Conv nets in general find areas of correlation within an image, that is, they look for spatial correlations. This means a DCGAN would likely be more fitting for image/video data, whereas the general idea of GAN can be applied to wider domain, as the model specifics are left open to be address by indiivdual model architectures.

Regarding dimensions - I don't think the dimensions of your data would dictate which of the two variants to go for, other than of course influencing things that we always have to consider, such as training time, model complexity, capacity to learn and so on.
