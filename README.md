# CAN-Detection-ECG-ML
This project implements a machine learning-based system for detecting **Cardiovascular Autonomic Neuropathy (CAN)** in **Type 2 Diabetes** patients using **ECG data**. The system focuses on feature extraction from RR intervals and classification using ML algorithms such as XGBoost and Random Forest.

## Data Collection:
The process begins with obtaining an ECG dataset from Open-source repository. The extracted files consisted of multiple CSV files, each containing ECG waveform data recorded from 50 individual subjects (25 normal subjects and 25 subjects diagnosed with CAN). The recordings were acquired at a sampling frequency of 250 Hz, which is suitable for heart rate variability (HRV) analysis, as it provides sufficient temporal resolution for detecting R-peaks accurately.

## Data Preprocessing :
The raw ECG data is cleaned to remove noise, artifacts, and irrelevant fluctuations to enhance signal quality for feature extraction. Bandpass filtering is applied to isolate relevant frequency components, and baseline correction is performed to eliminate signal drifts, enhancing overall signal quality for feature extraction. Heart rate variability (HRV) parameters such as RMSSD (Root Mean Square of Successive Differences), SDNN (Standard Deviation of NN Intervals) and Mean RR (Mean of RR Intervals) features that are autonomic function indicators are extracted from the processed ECG signals.

## Labelling :
Labeling is based on a threshold-based classification approach using specific HRV parameters. Participants are classified as "Normal" or "CAN-affected" based on predefined threshold values: 
**SDNN < 17.13 ms and RMSSD < 24.94 ms** 
indicate the presence of CAN, while values above these thresholds are classified as normal. Since the XGBoost model requires numerical labels: **"Normal" → 0 "CAN" → 1**

## Machine Learning Model :
Random Forest (RF) : Helps in selecting the most important features and classifying CAN cases effectively.
XGBoost : Enhances classification accuracy by using an advanced boosting technique to refine predictions.

## Model Training and Validation :
The XGBoost and Random Forest models are trained on labeled data to classify individuals as normal or CAN-affected based on HRV features. Model performance is assessed using accuracy, confusion matrix, label distribution, and AOC curve analysis to ensure reliable classification. 

## Conclusion :
Among the models tested, Random Forest exhibit strong classification performance with high recall, ensuring that most CAN cases are correctly identified. XGBoost, while also effective, shows slightly lower sensitivity, which could impact its ability to detect CAN in borderline cases. However, the models significantly outperform traditional diagnostic methods, which are invasive, time-consuming, and require specialized clinical expertise. This approach automates the classification process using ECG-derived features, making it a practical tool for early detection and routine screenings.
