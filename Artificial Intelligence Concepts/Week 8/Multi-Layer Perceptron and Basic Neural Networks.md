**[Module Page](https://modules.lancaster.ac.uk/course/view.php?id=44398)**

# Neural Networks

A neural network is a biologically motivated approach to machine learning

NN's similarities w.r.t biological neural network:

- NN's fundamental processing elements are also neurons
- NN also receives inputs from other sources, then combines them in someway, and finally outputs the final result 

- NN tries to mimic human brains 
- NNs are quite hot in 80s and ealy 90s
- resurgence currently, with state-of-the-art techniques
- NNs are not nearly as complex as the actual human brain


![[Pasted image 20250307092559.png]]

![[Pasted image 20250307092813.png]]


in machine learning, we call the neuron as perceptron

- perceptron can be seen as a simplified model of a biological neuron

- and are called network weights (or network parameters)
![[Pasted image 20250307093127.png]]

## Activation Function

- we can choose different types of activation functions, based on application requirements 


- Linear
![[Pasted image 20250307093302.png]]

- Rectified Linear Unit (ReLU)
![[Pasted image 20250307093337.png]]


- Hard Threshold (Step Function)
 ![[Pasted image 20250307093350.png]]


- we can choose different types of activation functions, based on application requirements

![[Pasted image 20250307093513.png]]

- please list some applications, where it is good to use the *Step function* (or *Sigmod function*) as the activation function


## Multi-Layered Perceptron (MLP)

Stacking multiple layers of perceptrons (neurons), we get the multi-layer perceptron (MLP) which has stronger expressive capability compared to a single perceptron 

![[Pasted image 20250307093729.png]]



- hard to say which architecture is bes.

a network with less parameters, so smaller computation cost, but its representation capability is relatively weak

a network with more layers are more params has a higher cost, but representation cost is relatively strong

- but a network with more layers can cause additional problems, namely the overfitting problem 