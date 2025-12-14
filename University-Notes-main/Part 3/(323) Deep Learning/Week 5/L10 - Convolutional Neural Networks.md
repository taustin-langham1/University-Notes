**[Lecture Slides](https://modules.lancaster.ac.uk/mod/resource/view.php?id=2805922)**
## Topic Outline:

Strengths and Limitations of Multi Layer Perceptrons (MLPs)
What are Convolutional neural networks (CNN)
- convolution layer
- batch normalisations
- activation layer
- pooling layer
- fully connected layer(s)

CNN Architectures (LeNet-5, AlexNet, ZFNet, VGGNet, GoogLeNet, ResNet)

## Strengths and Limitations of MLPs


**universal approximators** MLPs even with just one hidden layer, can in theory approximate any function

effective on tabular data: especially when input features are meaningful and compact

but what if our input isn't nicely structured features . . . but raw pixels, word sequences, or time series signals?

## Using MLPs with Engineered Features

using MLPs with handcrafted input features can be effective, especially when those features are informative and compact

however this approach: 
	- depends on manual engineering
	- may miss subtle patterns in the raw data
	- requires domain expertise and trial and error

## Automated Feature Learning, in place of Engineered Features

Aim of specialised networks like convolutional:

**Automated Feature Learning**

improve flexibility and model performance, we want:

- the network to learn features automatically
- to work directly with raw inputs (e.g., images, audio, time series, text)

![[Pasted image 20251107151346.png]]

1000x1000 image and 100 neurons in the hidden layer 1

**around $10^9$ weight parameters in the first layer!**

MLPs treat all input pixels equally, ignoring the spatial locality of pixels in the image

even a one-pixel shift in the image can significantly alter the input pattern which may result in an incorrect or different classification

- imagine you have a sequence of length **7** and each element is a vector of size **d**
- input to MLP: the entire sequence is flattened into a single vector of size
- T * d

suppose:
	a sentence with five words (t = 5)
	each word is a 100-dim embedding (d = 100)
then:
	the original input shape (5,000)
	flattened input shape (500, )
that 500-dimensional vector is what we pass into the MLP

**Problems:**
• Poor scalability with sequence length
	• The number of parameters grows rapidly with longer sequences.
	• This makes training inefficient and prone to over-fitting.
• Inflexible input size
	• All sequences must be padded or truncated to a fixed length.
	• This is unnatural for variable-length data like sentences.
• No temporal awareness
	• MLPs treat all inputs as independent and fixed-size vectors.
	• They don’t model the order of elements in the sequence.

## What Are CNNs?

- watch the lecture again

Convolutional Neural Networks also know as CovNets, are a class of deep neural networks specialised for processing data with a grid-like topology, such as:

- 1D grids -> time series data
- 2D grids -> images
- 3D grids -> videos


- why CNNs are powerful for visual tasks

- preserve spatial structure using convolutional filters
	- only connect local regions of the input -> leads to sparsity
- parameter sharing makes them efficient and less prone to overfitting
	- the same filter is applied across the entire image
	- drastically reduces the number of parameters compared to MLPs

## Convolution Layer


### Filter Size in Convolution

common sizes: 3x3, 5z5, 7x7, 1x1 (channel mixing, dimensionality reduction)

key points:
	- **larger filters** -> capture more spatial context, but more parameters
	- **smaller filters** -> fewer parameters and stacking them can capture information from a wider region (e.g, two 3x3 filters can cover a similar area as one 5x5 filter)
	- filter size affects feature map resolution
	- **filter depth** always matches **input channels** (e.g., RGB input = 3 channels -> filter size 3x3x3)

### Variants of Convolution Function

- **zero padding**
	- to avoid layer-to-layer shrinking
- **stride**
	- the amount of down-sampling
- **unshared convolution**
	- like convolution, but without sharing
- **tiled convolution**
	- cycle between shared parameter groups

### Convolution with Zero Padding

**definition**: adding rows/columns of zeros around the image before applying convolution
why is it used?
- preserve spatial size -> prevents shrinking of feature maps
- utilise broader information -> ensures edge pixels contribute equally
- enable deeper networks -> keeps feature maps large enough


- **Padding size:** Number of pixels added around the boarder

