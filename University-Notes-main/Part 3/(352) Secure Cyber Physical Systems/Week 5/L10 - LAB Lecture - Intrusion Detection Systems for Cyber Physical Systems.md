TODO: 
Course work should have been mentioned in the lecture - so watch the recording and note here

1. Identify the main approaches to intrusion detection for CPSs and the major challenges associated with implementation
2. Recall approaches to anomaly detection that can be used to identify cyber-attacks
3. Understand approaches to measuring the performance of detection methods


## Detection Methods for CPSs

1. **Signature-based detection**
	1. Detect known malicious patterns
	2. requires signatures of known malicious behaviour 
2. **Anomaly-based detection**
	1. detects deviations from a known baseline (normal) behaviour
	2. flags events deviating from the baseline
3. **Specification-based detection**
	1. uses formal models or rules describing correct system behaviour; deviations indicate attacks
	2. requires accurate specifications of behaviour - good for safety systems


## Data sources

- **Cyber data**
	- Network traffic 
	- System logs, authentication events
	- PLC state such as cycle times, mode, program checksums
- **Physical Data**
	- timeseries data from a process under control
- **Domain-specific information**
	- unsafe system states or control actions
	- physical laws


## Challenges for CPS IDS

availability of data
explainability of results
Limited computational resources
proprietary protocols and systems


# Specification-Based Detection

### At the edge:

- devices at the industrial edge are becoming increasingly sophisticated to support advanced devices
- this introduces cyber security risks but also opportunities
- can we use functionality at the industrial edge to support cyber security with a small physical footprint?

# Anomaly detection
### Approaches

• Statistical analysis
• Change point detection using algorithms, such as Cumulative Sum (CUSUM),
Auto Associative Kernel Regression (AAKR) and Kullback-Leibler divergence
• Model-based detection
• Detect residuals between measured state and predicted state using a model,
such as a Kalman filter
• Machine learning
• Use various machine learning-based approaches to detect an anomaly, e.g., as
an outlier or a significant deviation from a prediction
• Examples include Autoencoders or K-means clustering




# TODO: Watch Lecture here, until:


# Measuring Detection Performance


Errors in intrusion detection

an IDS may wrongly classify an event 
we can recognise two types of errors
![[Pasted image 20251106121908.png]]

detection metrics:

- precision
- recall
- accuracy 
- f1 score


Setting a Threshold:

![[Pasted image 20251106121938.png]]


# TODO: Course work should have been mentioned in the lecture - so watch the recording and note here:
