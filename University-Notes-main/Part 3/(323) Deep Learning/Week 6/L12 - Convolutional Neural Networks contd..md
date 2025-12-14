
### Batch Normalisation (during training)

- normalisation is performed using the statistics (mean variance) of the current mini-batch

- simultaneously, the layer updates an exponential moving average of the mean and variance (run in background)

- these running averages are saved as part of the trained model to estimate the total dataset's statistics


### During testing

Interface:
	mini-batch statistics are not used 
	normalisation is performed using the final accumulated running averages that were saved during training

### Applying an Activation Function

- **input** feature map
- **activation function** non-linear function, applied element-wise to the feature map
- **output** new feature map with transformed values, enhancing non-linearity for better learning

Max & Average Pooling: max, the maximum activation is chosen from selected block. average, the mean is taken from selected block

hyperparams
pooling size, stride

output size = [input size - filter size / stride] + 1


