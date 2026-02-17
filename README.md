# EEG Signal Processing and Machine Learning for Emotion Classification

**Project Duration:** Jan ’24 – Mar ’24  
**Guide:** Dr. Sidharth Pancholi (Postdoctoral Fellow, Harvard Medical School)

## Project Overview
This project focuses on the development of a Brain-Computer Interface (BCI) system designed to classify emotional states (specifically stress vs. non-stress) using EEG signals. The pipeline integrates sophisticated signal preprocessing, artifact removal, and machine learning to achieve high accuracy and subject-independent generalization.

## Key Features
* **Advanced Denoising:** Multi-stage pipeline using band-pass filtering, Savitzky-Golay filtering, and Wavelet thresholding to ensure high signal quality.
* **Artifact Removal:** Utilized Independent Component Analysis (ICA) via the MNE-Python library to identify and remove physiological artifacts like eye blinks.
* **Feature Extraction:** Developed a novel method for extracting time-frequency domain features, including mean, standard deviation, and band-specific Power Spectral Density (PSD).
* **Robust Classification:** Achieved 90.6% accuracy in subject-dependent testing and 64.7% accuracy in subject-independent Leave-One-Participant-Out (LOPO) validation.

## Technical Pipeline

### 1. Signal Preprocessing
Raw EEG data (32 channels at 128Hz) underwent rigorous cleaning:
* **Savitzky-Golay Filter:** Used for smoothing and trend removal.
* **Wavelet Denoising:** Implemented Discrete Wavelet Transform (DWT) with 'db2' wavelets and soft thresholding to remove noise while preserving signal transients.
* **ICA Implementation:** Decomposed signals into independent components to isolate and exclude non-brain signal artifacts.

### 2. Feature Extraction
Features were calculated to capture the neural markers of stress:
* **Time-Domain:** Statistical features like Mean and Standard Deviation.
* **Frequency-Domain:** Power Spectral Density (PSD) calculated using Welch’s method across specific EEG bands.

### 3. Machine Learning & Validation
A **Logistic Regression** classifier was trained to differentiate between stress and non-stress states:
* **Non-LOPO Strategy:** Standard training and testing on known subjects to evaluate peak performance.
* **LOPO Strategy:** Leave-One-Participant-Out cross-validation used to test the system's ability to generalize to completely new users.

## Performance Results

| Metric | Non-LOPO (Subject Dependent) | LOPO (Subject Independent) |
| :--- | :--- | :--- |
| **Accuracy** | 90.6% | 64.7% |
| **F1-Score** | 0.91 | 0.59 |



## Tools & Libraries Used
* **MNE-Python:** For EEG data handling and ICA.
* **Scipy & PyWavelets:** For Savitzky-Golay filtering, PSD calculation, and DWT.
* **Scikit-learn:** For Logistic Regression modeling and LOPO validation.
* **Pandas & NumPy:** For data manipulation.
* **Matplotlib:** For signal visualization.

## Repository Structure
* `EEG_pre_processing.ipynb`: Focuses on Savitzky-Golay and Wavelet denoising techniques.
* `ICA_without_leave_one_out.ipynb`: Details the ICA process and subject-dependent classification.
* `leave_one_out.ipynb`: Demonstrates the subject-independent performance via LOPO validation.
