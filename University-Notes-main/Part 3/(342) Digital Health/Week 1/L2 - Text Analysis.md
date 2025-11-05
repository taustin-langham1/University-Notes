**[Week 2 Lecture Slides](file:///home/thomas/Downloads/Health%20Text%20Analysis.pdf)**

Deep learning for health text analysis

BERT:  Bidirectional Encoder Representations from Transformers
- inner working
- model components
- training BERT

Learning Objectives
- BERT - abilities, composition, how to train.


## Deep learning for health text analysis

#### Why Health Text Matters


- text - data modality with the strongest semantic value for ML
	- Temporal cues
	- causality
	- uncertainty
	- negation
	- social context

- clinical notes contain rich information - hidden cues in texts can identify risks, treatments, and patterns

- NLP uses ML to read and make sense of text
- Traditional ML - needs human judgement and effort to extract key informaiton
- Deep learning - learns what matters automatically from raw text, capturing context and meaning

#### NLP Tasks: What We Want to Do With Text

Representation - converts text into numeric form so that computers can process
	example: transforms the clinical note:
		"patient reports frequent urination and fatigue"
		into a vector of numbers that encodes each word for later analysis
classification / prediction - assign labels or scores
- example: predict whether a patient is "high-risk", or "low-risk"


## BERT: Bidirectional Encoder Representations from Transformers

### Inner Working

used by google since 2019 - brought context-aware understanding to search queries

Analogous to extracting patterns and risk factors in clinical notes

![[Pasted image 20251009151322.png]]

### Model Components

#### BERT Components

Input Representation:

>- vocabulary
>- word Piece tokenization
>- embedding layer
>- positional information

Processing:

> - transformer & layers

transformer layers:
- 1-3: basic word meaning
- 4-6: relations across several words
- 7-9: meaning across distant parts of text
- 10-12: high-level concepts into a holistic sequence representation

Output:

>- CLS token
>- Output heads




### Training BERT

Step 1: Data reading and preparation

Step 2: tokenisation

Step 3: running model

Step 4: evaluation metrics


## Key terms:



word piece: A sub-word tokenisation method that breaks rare words into common fragments

CLS token: special token added to the beginning of a sequence; summarises overall meaning

SEP token: special token marking the end of a sentence or sequence; provides structural context

embedding:
- vector: numerical vector representing token; captures syntactic and semantic properties
- matrix: a large matrix pre-trained embedding for all vocabulary tokens; provides default meanings

transformer
	layer:
	-  a single analysis unit in BERT that applies self-attention to token vectors
	transformer:
	- the full stack of layers in BERT; coordinates layer outputs to produce final contextual embedding