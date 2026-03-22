https://www.geeksforgeeks.org/deep-learning/deep-learning-interview-questions/
https://www.interviewbit.com/deep-learning-interview-questions/#what-is-deep-learning
https://devinterview.io/questions/machine-learning-and-data-science/computer-vision-interview-questions/

1. What is the difference between Deep Learning and Machine Learning?
deeplearning -> subset of machine leanrning
multple layers , amount of data,  learn features automatically from raw data,hard to interpret,
 image recongnition, nlp, self-driver cars,  expensive and slower
 
2. What are the different types of Neural Networks?
    Feedforward Neural Networks (FFNNs)
    Convolutional Neural Networks (CNNs)
    Recurrent Neural Networks (RNNs)
    Long Short-Term Memory Networks (LSTMs)
    Gated Recurrent Units (GRU)
    Autoencoder Neural Networks
    Generative Adversarial Networks (GANs)
    Transformers
    Deep Belief Networks (DBNs)

3. What is a Neural Network and Artificial Neural Network (ANN)?
neural network is a model for biolocal inspired by human brain
ANN is the implementaion of this concept in machines.

4. How Biological neurons are similar to the Artificial neural network.
in ANN , an artificail neural receives inputs,  multiplies with weigths and add bias, applies an activation funtion and passes the output to the next layer

5. What are Weights and Biases in Neural Networks?
z = w1 * x1 + w2 * x2 + b
weight  determine the importance of each input. If an input has a higher weight, it influences the output more strongly.
bias helps the model shift the activation curve so that the network can learn patterns more flexibly.

6. How weights are initialized in Neural Networks?
Zero Initialization: All weights are set to zero. This causes every neuron to learn the same features (symmetry problem) making training ineffective or extremely slow.
Random Initialization: Weights are assigned small random values from a uniform or normal distribution. This breaks symmetry, but poorly chosen ranges can lead to issues like vanishing or exploding gradients.
Xavier (Glorot) Initialization: Weights are drawn from a distribution with variance. Designed for sigmoid, softmax and tanh activations, it helps maintain balanced activations across layers.
He Initialization: A variant of Xavier where variance is scaled. It is well-suited for ReLU and its variants, preventing the dying ReLU problem.
Orthogonal Initialization: Weights are set as a random orthogonal matrix, ensuring columns are orthonormal. This method has shown strong performance in recurrent neural networks (RNNs).
Pretrained Initialization: Weights are initialized from a model trained on a related task (e.g., using ImageNet-pretrained CNN weights). This speeds up training and often improves performance on smaller datasets.

7. What is an Activation Function and how does it work in Neural Networks?
It introduces non-linearity, which allows the network to learn complex patterns instead of just simple linear relationships.
Sigmoid(0, 1)
softmax
ReLu(0->negative,  max)
Tanh(-1, 1)

8. What are the different types of Activation Functions used in Deep Learning?
sigmoid (0, 1)
softmax(0, 1)
ReLu
Tanh

9. What are the different layers in a Neural Network?
input layer
hidden layer -> multiply weights + bias  -> activate function
output layer


