https://ai.stackexchange.com/questions/5546/what-is-the-difference-between-a-convolutional-neural-network-and-a-regular-neur

The Convolutional Neural Networks is a subclass of neural networks which have at least one convolution layer. They are great for capturing local information (e.g. Neighbour pixels in an image or surrounding words in a text) as well as reducing the complexity of the model (faster training, needs fewer samples, reduces the chance of overfitting).

Neural Networks (NN), or more precisely Artificial Neural Networks (ANN), is a class of Machine Learning algorithms that recently received a lot of attention due to the availability of Big Data and fast computing facilities (most of Deep Learning algorithms are essentially different variations of ANN).

The class of ANN covers several architectures including Convolutional Neural Network (CNN), Recurrent Neural Networks (RNN) e.g. LSTM and GRU, Autoencoders, and Deep Belief Networks. Therefore, CNN is just one kind of ANN.

Generally speaking, an ANN is a collection of connected and tunable units (a.k.a as nodes, neurons, and artificial neurons) which can pass a signal (usually a real-valued number) from a unit to another. The number of (layers of) units, their types, and the way they are connected to each other is called the network architecture.

A CNN, in specific, has one or more layers of convolution units. A convolution unit receives its input from multiple units from the previous layer which together create a proximity. Therefore, the input units (that form a small neighbourhood) share their weights.

The convolution units (as well as pooling units) are especially beneficial as:
- They reduce the number of units in the network (since they are many-to-one mappings). This means, there are fewer parameters to learn which reduces the chance of overfitting as the model would be less complex than a fully connected network.
- They consider the context/shared information in the small neighbourhoods. This future is very important in many applications such as image, video, text and speech processing/mining as the neighboring inputs (e.g. pixels, frames, words, etc.) usually carry related information.

