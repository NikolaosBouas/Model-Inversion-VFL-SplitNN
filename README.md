# Model-Inversion-VFL-SplitNN
This project was created as part of my Independent Study Option for the MSc Computing (AI &amp; ML) programme at Imperial College London.

In this notebook, I am testing the privacy guarantees provided by the OpenMined PyVertical framework against model inversion attacks that use the activations signals shared between parties. 

The setting that I am examining consists of two parties, e.g. Alice and Bob, where Alice holds the inputs and Bob holds the labels. The two parties want to jointly train a model on vertically split data and they are using Split Neural Networks. 

Let's assume there is a malicious adversary that has access to the communication channel between Alice and Bob, thus learning the "smashed" data that Alice sends to Bob. If it also has access to the original data, the adversary can train a model to reconstruct the original input, given the smashed data tha Alice sends to Bob.

In this notebook, I am going to show that the more processing Alice performs upon the data the harder it is for the adversary to reconstruct it. In essence, we are going to vary the position of the split layer and see that the more layers that Alice holds the worse the reconstruction.

I am using the MNIST dataset and a simple convolutional network with 5 fully connected layers. We are going to split the network on 5 positions (on each of the fully connected layers) and observe the reconstruction quality.
