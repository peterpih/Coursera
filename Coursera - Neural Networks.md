#TOC
[Types of Learning](#types-of-learning-section)
[Neural Network Architecture](#nn-architecture-section)


Examples of tasks best solved by machine learning:  
1. Reconginzing Patterns  
2. Recognizing Anomolies  
3. Prediction: stock prices, movies likes

MNIST database of handwritten digits  

###What are neural networks?
Understand how the brain works  
Understand a stype of parrallel computing  
Different parts of the brain do different things (modularization)  

div id="types-of-learning-section">
###Three Types Of Learning
1. **Supervised Learning** learning to predict an output given an input  
   
   Another way to think about a model class is to ask yourself: are these models performing a fundamentally  
   different set of computations? In this case, the first neural network is performing nonlinear computations which    cannot be represented by a linear network.

  a. **Regression** target output is a number
  b. **Classification** the target output is a class label

2. **Reinforcement Learning** learning to maximize a payoff  
   Usually use a discount for payoffs in the future  
   Difficult to see where went wrong since there is a time delay  
   Can only handle 100's or 1,000's of features, not 1,000,000's

3. **Unsupervised Learning** discover a good internal representation of the input  
   Can use unsupervised learning to figure out structre of data, then use supervised learning  
   Provide compact representation of information  
   **Clustering** is an example
   **Principal Components Analysis**

<div id="nn-architecture-section">
###Neural Network Achitecture
1. **Feed Forward**  
   input units(bottom) -> hidden layer(s) -> output layer(top)
   if hidden layer is more than 1, it's called *deep neural network**  
   The activities of each layer needs to be a nonlinear function of the layer below  
   
2. **Recurrent**
   More powerful than Feed Forward networks  
   They have directed cycle in their network graph, possible to get back to where you started  
   Can have complicated dynamics and can be difficult to train  
   Weght matrix for hidden layer remain the same through time  

3. **Sysmetrically Connected**  
   Weights are the same in both directions  
   Symetric networks re much easier to analyze than recurrent networks (John Hopfield)  
   More restricted in what they do, restricted by an energy function  
