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

10. What is a Perceptron or a Single Layer Neural Network?
If the output crosses a certain threshold, the perceptron outputs one class or otherwise, it outputs the other class.

11.  What is Multilayer Perceptron and How it is different from a Single-Layer Perceptron?
ontains one or more hidden layers between the input and output layers. It is a type of feedforward neural network and is widely used in deep learning.

12. How are the number of hidden layers and neurons per hidden layer selected?
    There is no fixed rule for selecting hidden layers and neurons and they are chosen based on the complexity of the problem and are often tuned experimentally.

Number of Hidden Layers

For shallow problems or simple patterns we can use 1–2 hidden layers.
For complex problems like images, speech or NLP we can use deeper networks with many layers.
Universal Approximation Theorem says even a single hidden layer with enough neurons can approximate any function, but deeper networks often train more efficiently.
Number of Neurons per Layer

Too few neurons can lead to underfitting (model can’t capture the patterns).
Too many neurons can lead to overfitting (model memorizes training data).
A common practice is to start with a number between the size of the input layer and output layer, then adjust based on validation performance.
Some heuristics methods like powers of 2 (e.g., 64, 128, 256) are commonly tried in practice.

13. What is the difference between Shallow Networks and Deep Networks?

14. Why are Neural Networks Called Black Boxes?
because their internal workings are not easily interpretable. While they can learn complex patterns and make highly accurate predictions, it is usually difficult to understand how inputs are transformed into outputs.

15. What are Feedforward Neural Networks?
Feedforward Neural Network is the simplest type of artificial neural network where the data flows only in one direction i.e from the input layer to hidden layers and then to the output layer.

There are no cycles or loops in the connections.
Each layer passes information forward and neurons are fully connected to the next layer.
Training is usually done using backpropagation with gradient descent to adjust weights and biases.
Easy to design and train for smaller tasks.
Works well for problems like image recognition, speech recognition and regression tasks.
Unlike recurrent networks, FNNs do not have memory of past inputs.

