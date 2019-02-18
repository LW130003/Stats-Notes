Better Mixing via Deep Representations
https://arxiv.org/pdf/1207.4404.pdf

Abstract

Deeper representation of given data does a better job at disentangling the underlying factors of variation. The author of this paper studied a related conjecture, better representations, in the sense of better disentangling, can be exploited to produce faster-mixing Markov chains. And to understand better and why this happening, the authors proposed a second conjecture: the higher-level samples fill more uniformly the space they occupy and the high-density manifolds tend to unfold when represented at higher levels.

---------------------------------

Introduction and Background

Deep Learning algorithms discovers multiple levels of representation of a given data, and it is generally believed that higher representation can potentially capture higher-level abstractions relevant to the distribution of interest. (via experiment it have been shown that adding more depth to the representation can have great benefits).

Lower level features can be reused in forming higher level representations, and as the depth of the representation increases the potential gains become exponential.

Deep learning algorithms relies on the idea of reusing lower level features. (This is the reason why parameter sharing is such a powerful and effective method).

Another (less discussed) advantage of deep representation is the fact that it might help disentangle the underlying factors of variation. (If we have an algorithm that can separate data easily fi would make further processing much easier.) 

(When we say that we aim to build a machine that understand it's surroundings this can mean that the machine is able to disentangle the factors and causes it involves, so progress in that direction seems important.)

If the learned representation does a good job at disentangling the hidden factors, it can even counter the effects of the curse of dimensionality. Many observation have been made that deep learning algorithms aid this disentanglement however, we still don't know why or the degree of the extend.


Unsupervised learning algorithm tries to capture salient structure of given data distribution,whereas most deep learning algorithms are used to learn features and exploit them for classification or regression tasks. By their nature of unsupervised learning, some of the algorithms can be use to generate samples, however this can suffer from a fundamental problem of mixing: it is difficult for the Markov chain to jump from one mode of the distribution to another, when these are separated by large low-density regions, a common situation in real world data, and under the manifold hypothesis

Manifold Hypothesis - Natural classes presented in the data are associated with low-dimensional regions in input space near which the distirbution concentrates, and that different class manifolds are well-separated by regions of very low density.

Slow mixing means, that it takes many consecutive sampling steps to go from one mode to another and even more to cover all of them.

This happens since jumping around the low density void between modes are rare and unlikely.


When the learning algorithm does not have a good representation of the given data, the model tends to correspond to a smoother and uniform distribution, putting mass in larger volumes of input space, and in particular, between the modes. (This can be seen when we generate few sample of images, they will look more blurry and noisy).

As the model improves and its corresponding distribution sharpens near where the data concentrate, mixing become considerably slower. 

Since sampling is critical to many machine learning algorithms, this indicates that the learning is going to be slow or poor and even in some cases just stop due to the limitation of the learning algorithm.


To improve mixing, tempering have been introduce. The idea is use smoother densities to make quick but approximate jumps between modes, but use the sharp "correct" model to actually generate the samples of interest inside these models, and allow samples to be exchanged between the different levels of temperature.


Main Hypothesis: Mixing is easier when sampling at the higher levels of representation.

The main objective is to investigate this hypothesis and why this happens as well as to test on more specific hypothesis.

The idea that deep generative models produces better features and better quality samples is not novel and have been investigated by promising researchers.

--------------------------------

Hypotheses

H1: Deep vs Better Mixing. A successfully trained deeper architecture has the potential to yield representation spaces in which Markov chains mix faster.

H2: Depth vs Disentangling. Part of the explanation of H1 is that deeper representations can better disentangle the underlying factors of variation.

H3: Disentangling Unfolds and Expands. Part of the explanation of H2 is that more disentangled representations tend to (a) unfold the manifold near which raw data concentrates, as well as (b) expand the relative volume occupied by high probability points.

------------------------------

Conclusion

1. Deeper representations can yield better samples and better mixing
2. This is due to better disentangling
3. This is associated with unfolding of the manifold where data concentrate along with expansion of the volume good samples take in representation space.

And the performed experiments confirmed the author hypothesis, on higher levels better samples and better mixing are obtained. (even when interpolating between examples or adding isotropic noise).

