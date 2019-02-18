Advanced Topic in Deep Learning - Disentangled Representation

https://www.tik.ee.ethz.ch/file/8ca5c4b6375e366a1497653cbba27d13/LearningDisentRepresentations.pdf

Deep neural networks have been very successful at automatic extraction of meaningful features from data. Manual feature engineering is often not necessary anymore, and we can instead focus on designing the architecture of the neural networks. However, due to the complexity of neural networks, the extracted features are themselves highly complex and can often not be interpreted by humans. Instead, the neural network is treated as a black box and we have to trust external evaluation metrics such as train and test error.

Often it would be beneficial to understand what kinds of hidden representations, or features, the model has actually learned.

Several method exist that are particularly suited for learning meaningful hidden representations.

The model we will be mainly looking at in this thesis is the Variational Autoencoder (VAE), a deep generative model. VAEs have been shown to be able to disentangle simple data generating factors from a highly complex input space.

For example, when being fed with images of faces, a VAE might automatically learn to encode the direction of the lighting in a single hidden variable. After training, we can very each hidden variable and observe the effect on the output, which let's us analyze, albeit manually, what kinds of features the model has learned. Several VAE extensions such as β-VAE focus mainly on the disentanglement aspect and also introduce disentanglement metrics, making evaluation easier.

So far, VAEs (and other generative models) have been most succesful in the image domain, where most architectures are based on Convolutional Neural Networks (CNNs), which by themselves are known to be powerful extractors. In sequential and/or discrete domains, such as music and language processing, there has been limited success.

In this thesis we want to investigaate the causes for this limited success. In particular, we want to compare different neural network architectures and their disentanglement capabilities when using them as building blocks for VAEs. Depending on the results we will go more towards improving existing methods for learning disentangled features and having a close look at current disentanglement metrics, or try to learn disentangled representations for sequence tasks.

