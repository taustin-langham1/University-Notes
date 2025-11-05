

 - explore a health dataset
 - train BERT model for health text analysis
 - evaluate model performance using appropriate metrics and visualisations

- rows are usually the amount of data available
- columns are typically the features and classifications

``` python
import pandas as pd

df = pd.read_csv('.../Diabetes.csv')

# Display the first 5 rows

df.head()

df.shape[0] # is ROWS (20,000 rows of data)
df.shape[1]# is COLUMNS (12 columns of data)

df.columns # -> returns the list of all column labels

df['confirmed_diagnosis'] # returns a series with all values in column
df['confirmed_diagnosis'].nunique() # unique number of values (so classifications)

df['confirmed_diagnosis'].value_counts() # returns a series showing each unqiue value in the column and how many times it appears, sorted in descending order

# very useful in showig how representitive the dataset is, how weighted it is in different classifications

```

**what is a series?**

a one dimensional labelled array in python that can hold data of any type - supports both integer-based and label-based indexing, allowing for easy data manipulation and access.


**Find the list of different symptoms reported by patients**

```python

df['symptom'].value_counts() # maybe more useful

# or

df['symptom'].unique()

```

**Find the number of words in each clinicians note**

```python

df['note_word_count'] = df['clinicians_notes'].apply(lamda x:len(str(x).split()))

print(df['note_word_count'].describe()) # gives a sumary of stats: count, mean, min, max, quartiles

- apply(...) # applies a function to each value in the column one by one
  # whatever the function returns becomes the new value in the resulting series (note_word_count)
  
- lambda x: # defines an inline function for each x (one clinicians note) the expression after the colon is excecuted
  
- str(x) # ensures the value is treated as a string
  
- .split() # splits the string by spaces into a list of words "low glucose level", becomes "low", "glucose", "level".
  
- len(...) # counts the number of words in that list

```

**Extract clinician notes** from the data frame, and store them in a variable X

```python

X = df['clinician_notes'].values()

# check

print("sample clinician notes: \n", X[3])
print("total number of clinician notes: " len(X))


```

**Extract the confirmed diagnosis (labels)** (text) from the data frame and store it in a variable Y. We need this because BERT must learn to classify each clinician's note into one of the diagnosis categories

to do this: train the model on part of the dataset where both:
 - the clinician's note (input), and 
 - the confirmed diagnosis (classification) are known

then, we'll test the model on the remaining data to check how accurately it can predict the diagnosis categories when only the notes are provided


``` python

Y = df['confirmed diagnosis'].values

# Y holds the target diagnosis labels the model must learn to predict during training


print("sample confirmed diagnoses:\n", Y[:5])
print("Total number of labels:", len(Y))

```

**processing for numerical input**


``` python

# convert diagnosis categories into numbers because classifcation models require numeric labels during training


import sklearn.processing # provides functions and transformer classes to convert raw data into formats suitable for machine learning

import LabelEncoder # converts categorical text labels into numeric values so the model can learn from them



le = LabelEncoder() # le creates a label encoder instance that will map each confirmed_diagnosis category into a number
Y_encoded = le.fit_transform(Y) 
# scans all unique diagnosis categories
# assigns a unique ID to each category (e.g., dehydration = 0, hyperglycermia = 1...)
# transforms the text labels into a numeric array
# Y_encoded stores these integer IDs for each record in the dataset; this becomes the target variable the model will learn to predict

```

**Print each diagnosis category and its assigned numeric label**

```python

label_mapping = {label: int(idx) for label, idx in zip(le.classes_,le.transform(le.classes_))}

print("Label mapping:\n", label_mapping)

# le.classes_ -> ['dehydration', 'hyperglycemia',..] (unqiue labels)
# le.transform(...) -> [0, 1, 2, 3, ..] corresponding numeric IDs
# zip(...) -> pairs each label with its numeric ID 
# int(idx) -> ensures the numbers are printed as clean Python integers
# label_mapping -> final readable dictionary showing label -> ID mapping


```


**Now the data is required to be split into 3 sets for training, validation, and test sets**

```python
from sklearn.model_selection import train_test_split



# first split into training and testing
X_train, X_test, Y_train, Y_test = train_test_split(

	X,
	Y_encoded,
	test_size=0.2,
	random_state=42,
	stratify= Y_encoded # preserves class proportions in each split
)

# second split, some validation, from training

# Training is used to fit the model
# validation is used to tune and monitor the model during trainig
# test set remains completely unseen until final evaluation

# the validation set is used during training, after each epoch, to monitor how well the model is generalizing, without touching the test data

X_train, X_valid, Y_train, Y_valid = train_test_split(
	
	X_train,
	Y_train,
	test_size=0.15,
	random_state=42,
	stratify=Y_train
)

print("Final Training set size:", X_train.shape[0])
print("Final Test set size:", X_test.shape[0])
print("Final Validation set size:", X_valid.shape[0])


```


When training models with PyTorch or Hugging Face Transformers, the data must be provided in a structured, iterable format

We create a custom dataset class to convert our text and labels into a format that the trainer can understand

this class handles tokenisation and makes sure each sample is returned as tensors


```python

from torch.utils.data import Dataset
import torch
from transformers import BertTokenizer
tokenizer = BertTokenizer.from_pretrained("bert-base-uncased")


# dataset is part of PyTorch's data utilities
# your textdataset class inherits from it, so python must know what dataset is before the class definition


```

**Input Representation**

Tokenize clinicians' notes in the dataset, separately for the training, validation, and testing set

```python

encodings_train = tokenizer(

list(X_train),
truncation = True,
padding="max_length",
max_length=32,
return_tensors="pt"
)

encodings_test = tokenizer(

list(X_test),
truncation = True,
padding="max_length",
max_length=32,
return_tensors="pt"
)

encodings_valid = tokenizer(

list(X_valid),
truncation = True,
padding="max_length",
max_length=32,
return_tensors="pt"
)




#visualisation

idx = 400
print("original text:",X[idx])
print("token IDs:", encodings['input_ids'][idx])
print("Attention mask:", encodings['attention_mask'][idx])

```

truncation = cuts long text to keep each sequence within the length limit
padding = pads short text to ensure all sequences have equal length

so :
Notes with longer than 32 tokens will be truncated.
Shorter notes will be padded with zeros up to length 32.


- summary: converted raw clinician notes into tokenized tensors so they can be processed by BERT

Each note is now represented as:
- input_ids , numerical token IDs
- attention_mask, indicators for real tokens vs padding


**Train and Evaluate a BERT Classification Model**

use the pre-trained embeddings from BERT and the tokenized clinicians notes from our dataset to train a text classification model.
This model will learn to associate language patterns in clinicians notes with the correct diagnosis category
Once trained, it can predict diagnoses for new, unseen notes

Stage involves:

- Loading a pre trained model (BERT for sequence classifications)
- Defining training arguments (ephocs, batch size, logging, etc.)
- Setting evaluation metrics (accuracy, F1 score)
- Saving the model and tokenizer for future use


transformers -> popular open-source library by Hugging Face
BertForSequenceClassification -> a pretrained bert model with a classificaiton layer on top

```python

## compute the number of unique labels

num_labels = len(le.classes_)

output_labels = num_labels

model = BertForSequenceClassification.from_pretrained("bert-base-uncased", num_labels=output_labels)

# confirmation message

print("BERT pretrained model loaded successfully with", num_labels, "labels")


```


**Define training arguments**

Before training, we need to configure how the fine-tuning will run, how many epochs, how big each training batch is, when to evaluate, how to log, and where to save results. 
We use TrainingArguments, a configuration class provided by Hugging Face.

```python

training_args = TrainingArguments(
output_dir="./results",
num_train-epochs=2,
per_device_train_batc_size=32,
per_device_eval_batch_size=32,
eval_strategy="epoch",
logging-strategy="epoch",
save_strategy="epoch"
)

```


• output_dir → directory where model checkpoints and logs will be stored after each epoch.
• num_train_epochs → how many times the model will pass through the entire training set.
(2 is usually a good start for fine-tuning BERT.)
• per_device_train_batch_size → how many samples the model processes before updating its weights. Larger values train faster but need more memory.
• per_device_eval_batch_size → batch size during evaluation.
• eval_strategy → tells the trainer when to run evaluation (here, after each epoch).
• logging_strategy → controls when to log metrics (also after each epoch).
• save_strategy → saves the model after each epoch so you can restore it later if needed.


**Define Evaluation Metrics (accuracy, F1 score)**

```
import numpy as np
from sklearn.metrics import accuracy_score, f1_score

```

umpy library -> for numerical operations and efficient array handling

sklearn.metrics -> for metrics that quantify prediction quality

accuracy_score -> measures the overall proportion of correct predictions i.e., how often the model correctly classifies clinician's notes into the right diagnosis


F1 score -> precision & recall

precision = of all the cases predicted as a given diagnosis, how many were actually correct

recall = of all the cases that truly belong to a diagnosis, how many were correctly identified

range between 0 & 1



**computer metrics**

```python

def compute_metrics(eval_pred):
	logits, labels = eval_pred
	predictions = np.argmax(logits, axis=1)
	acc=accuracy_score(labels, predictions)
	f1 = f1_score(labels, predictions, average="weighted")
	return {"accuracy": acc, "f1":f1}


```

**initialise the trainer**

Once we have:
	the BERT model
	the training arguments
	the training, validation (tokenized)
	and the metrics function (compute_metrics)

Trainer -> a high level API from hugging face that simplifies training and evaluation

Transformers -> an open-source library developed by hugging face, which provides pretrianed models


```python

trainer = Trainer(

model=model,
args=trianing_args,
train_dataset=train_dataset,
eval_dataset=valid_dataset,
compute_metrics=compute_metrics
)

trainer.train()


````

model -> our fine-tuned BERT model (loaded with correct number of output labels)
args -> training configuration already defined 
train_dataset -> our dataset used to train the model
eval_dataset -> our validation set, used after each epoch to evaluate progress
compute_metrics -> the function in step 4 to calculate accuracy and F1 after each epoch


```python

test_results=trainer.evaluate(test_dataset)
print(test_results)



save_path = ".../results/model"
trainer.save_model(save_path)
tokenizer.save_pretrained(save_path)
print(f"Model and tokenzier saved to {save_path}")



```