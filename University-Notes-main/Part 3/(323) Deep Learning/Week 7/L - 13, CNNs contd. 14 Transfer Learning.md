
## Transfer Learning

> topic outline, 
> ResNet as a Type of CNNs
> What is Transfer Learning
> Different Transfer Learning Models
> 	Feature extraction
> 	Fine-tuning 
> 	Knowledge Distillation


Resnet, hypothesis, the problem is optimisation, deeper models are harder to optimise
the deeper model should perform at least as well as the shallower model
skipnet, pass input from one layer with output to next layer,give option that if a set of layers is enough, then just pass that output to the next layers
find parameters in convolution layers, in a way where when you pass X it produces X


transfer learning,

in practice, many tasks only have limited labelled data
training from scratch on small datasets leads to, severe over-fitting,
poor genrealisation

transfer learning is the process of reusing knowledge from a source task / domain to improve learning in a target task/domain

instead of training from scratch:
start from a pre-trained model
adapt it to the new task with limited data

benefits:
- requires less labelled data
- faster training
- often achieves higher accuracy than training from scratch

## Different Transfer Learning Methods

Inductive Transfer Learning 
- train on labelled image net (general objects) fine-tune on animal dataset
	- feature extraction, fine tuning, knowledge distillation
Transductive transfer learning
- Domain adaptation for unlabelled target data
Unsupervised Transfer Learning
- from self-supervised learning-pretrained model (no labels), transfer informatiom

### Transfer Learning, Inductive Transfer Learning
#### Feature extraction
• Use a pre-trained model as a fixed feature extractor.
• Freeze backbone layers (e.g., Conv layers in ResNet).
• Replace the final classification layer with a new one for the
target task.
• Train only classification layer on your small dataset.

Limitations, 
works best when source and target domains are similar
if target task is very different, frozen features especially high-level ones, may be sub-optimal
classifier capacity is limited -> may underfit complex tasks requiring deeper feature adaption
leads to motivation for fine tuning
#### Fine Tuning

Full, 
unfreeze all layers, retrain the entire network, low learning rate

Partial,
freeze early layers, unfreeze later layers

Discriminating,
use different learning rates

#### Knowledge Distillation

Goal: tranfer knowledge from a large accurate teacher model, to a smaller efficient student model

why: large models are powerful, but too costly for real-time or mobile deployment

Idea: instead of only training on hard labels, the student learns from the teachers soft predictions (logits, softmax)
- soft targets contain "dark knowledge"
- example, teacher predicts, student learns

Training procedure,
1. train a large teacher network
2. compute soft outputs
3. train small student network using combined soft + hard loss