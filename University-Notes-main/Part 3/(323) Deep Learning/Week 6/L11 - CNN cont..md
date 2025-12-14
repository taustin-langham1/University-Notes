**[Lecture Slides](https://modules.lancaster.ac.uk/mod/resource/view.php?id=2805922)**


**• Convolutional Layer**
	• Applies filters (kernels) to extract features
	• Produces feature maps
**• Batch Normalization**
(optional)
	• Normalizes activations, stabilizes training
**• Activation Layer**
	• Adds non-linearity (ReLU, sigmoid, tanh)
**• Pooling Layer**
(optional)
	• Reduces spatial size of feature maps
**• Fully Connected Layer**
(optional)
	• Flattens feature maps into a vector
	• Connects to all neurons, followed by activations
**• Output Layer**
	• Produces final prediction


## Variants of Convolution Function

- zero padding
	- to avoid layer-to-layer shrinking
- Stride
	- the amount of down-sampling
- un-shared convolution
	- like convolution but without sharing
- tiled convolution
	- cycle between shared parameter groups

**after convolution, batch normalisation:**


## Pooling layer:
reduce the size of the feature map

replaces the output of the network at a certain location with a summary statistic of the nearby outputs
reduces computation for upper layers
provides some translation invariance
(robustness to small shifts in input)

variants:
	max pooling - reports the maximum output, within a rectangular neighbourhood
	average pooling - reports the average output
	
![[Pasted image 20251111165012.png]]