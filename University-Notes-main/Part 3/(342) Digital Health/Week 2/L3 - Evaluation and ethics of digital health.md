
## Evaluation

Digital health technologies aim to improve measurable health outcomes

- clinical
- behavioural 
- long-term

Evaluation frameworks, like HTA, link these outcomes to structured assessment domains

HTA - science-based framework to evaluate health technologies

**clinical domains** - health problems, technical characteristics, relative safety,  relative clinical effectiveness

**Non-clinical domains** - cost & economic evaluation, ethical implications, organisational aspects, social aspects, legal aspects

evaluation frameworks structure how health technologies are assessed
health outcomes provide the evidence base for these assessments


## Data qualities 


### Health Data

Multiple sources: clinical systems, patient-generated data, integrated platforms
different modalities: text, images, biosignals - each reveals different aspects of health
these differences shape what we can measure, evaluate, and trust

**How good is our data?**

1 - **Validity** - is the foundation of meaningful evaluation

2 - Accuracy - ensures the measure itself is correct

3 - Completeness  - ensures the measure is representative 

4 - Timeliness - ensures the measure reflects reality

5 - Trustworthiness - ensures the measure can be relied upon


## Data Biases



Proxy bias 
Representation bias
Under-representation


**Data collection and measurement**
- measurement bias
	- tools may perform differently across groups or settings - leads to inaccurate values and mis-classifications
- missing data bias
	- missing-ness is often not random
	- can distort and reduce validity

**Population representation**
- selection bias
	- does not represent the target population
- attrition bias
	- focuses on those who remain in the dataset, ignoring those who drop out
- Survivor-ship bias
	- occurs when analyses include only those who survive or remain observable until the end of the study period 

**Computational**
- Algorithmic bias
	- how data is generated, who is represented, to how its interpreted 


## Mitigating Strategies for Health Data Biases

- Data collection
	-  broaden and diversify data sources
	- ensure representative recruitment and inclusion
	- check data quality early: validity, completeness, accuracy
	- document sources and known limitations
- Data analysis
	- Stratification and subgroup analysis
		- break dataset into meaningful subgroups
		- compare descriptive statistics across subgroups
		- identify uneven values of these descriptive statics
		- report results at subgroup level
	- handling missing data
		-  quantify missingness by variable and subgroup
		- explore patterns of missingness
		- adjust through imputation
		- interpret results with acknowledged uncertainty
	- weighting to correct imbalances
		- Assign different weights to subgroups to reflect the target population
		- corrects over- or under-representation
- Algorithmic bias
	- AI simulates or generates data
		- design simulation with transparent assumptions
		- validate synthetic data distributions against real-world populations
		- include domain experts in dataset generation
	- AI is used in data processing or analysis
		- diversity and balance training
		- validate proxy variables carefully
		- audit performance across demographic subgroups 
		- re-calibrate or fine-tune models as needed
	- AI mediates or adapts interventions
		- test personalsation logic across user subgroups
		- apply fairness constraints or minimum performance thresholds
		- monitor adaptive algorithms for feedback loops 
		- provide flexibility and clinician oversight





**summary in single words:**

• Measurement bias – systematic errors in how data are collected or recorded.

• Health data bias – any systematic distortion in the collection, representation, analysis, or interpretation of health data that leads to inaccurate, incomplete, or unfair conclusions about individuals or populations

• Selection bias – bias resulting from certain groups being more likely to be included in the dataset

• Attrition bias – bias resulting from loss of participants during follow-up, affecting group representation

• Survivorship bias – bias resulting from outcomes reflecting only those patients who remained alive or in the study

• Missing data bias – bias resulting from missing information that is not random, thus influencing results

• Algorithmic bias – bias resulting from AI systems reinforcing or amplifying inequities present in datasets, analytic layers, or adaptive interventions

• Autonomy – ethics principle of respect for patient choice and control

• Beneficence – ethics principle of promoting well-being

• Non-maleficence – ethics principle of not harming

• Justice – ethics principle of ensuring fairness and equity

• Accountability – ethics principle of assigning clear responsibility and oversight for
outcomes

• Responsiveness & sustainability – ethics principle of ensuring technologies align
with needs and remain adaptable over time