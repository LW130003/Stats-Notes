What is the meaning of the word logits in TensorFlow?

Summary

In the context of deep learning the logits layer means the layer that feeds in to softmax (or other such normalization). The output of the softmax are the probabilities for the classification task and its input is logits layer. The logit layer typically produces value from -inf to inf and the softmax layer transforms it to values from 0 to 1.

Historical Context

Where does this term comes from? In 1930s and 40s, several people were trying to adapt linear regression to the problem of predicting probabilities. However, linear regression produces output from -inf to inf while for probabilites our desired output is 0 to 1. One way to do this is somehow mapping the probabilities 0 to 1 to -inf to inf and then use linear regression as usual. One such mapping is cumulative normal distribution that was used by Chester Ittner Bliss in 1934 and he called this "probit" model, short for "probability unit". However, this function is computationally expensive while lacking some of the desirable properties for multi-class classification. In the 1944 Joseph Berkson used the function log(p/(1-p)) to do this mapping and called it logit, short for "logistic unit". The term logistic regression derived from this as well.

The Confusion

Unfortunately the term logits is abused in deep learning. From pure mathematical perspective logit is a function that performs above mapping. In deep learning people started calling the layer "logits layer" that fefeds in to logit function. Then people started calling the output of this layer "logit" creating the confusion with logit the function.

TensorFlow Code

Unfortunately TensorFlow code further adds in to confusion by names like tf.nn.softmax_cross_entropy_with_logits. What does logits mean here? It just means the input of the function is supposed to be the output of last neuron layer as described above. The _with_logits suffix is redundant, confusing and pointless. Functions should be named without regards to such very specific context because they are simply mathematical operations that can be performed on values derived from many other domains. In fact TensorFlow has another similar function sparse_softmax_cross_entropy where they unfortunately forgot to add _with_logits suffix creating inconsistency and adding in to confusion. PyTorch on the other hand simply anmes its function without these kind of suffixes.

Reference

The Logit/Probit lecture slides is one of the best resource to understand logit. I have also updated Wikipedia article with some of above information.

http://www.columbia.edu/~so33/SusDev/Lecture_9.pdf
https://en.wikipedia.org/wiki/Logit
