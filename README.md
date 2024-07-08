# **EEG-Classification for different Cognitive States** 

This project is to use deep learning to classify EEG Signals related to subject's state.

The goal is to use various data processing techniques, feature extraction techniqus and making deep neural network architectures to perserve both spacial and time information in the classification of EEG data.

## **Introduction**

An **electroencephalogram (EEG)** is a test that detects electrical activity in your brain using small, flat metal discs (electrodes) attached to your scalp. Your brain cells communicate via electrical impulses and are active all the time, even when you're asleep. This activity shows up as wavy lines on an EEG recording.

The goal is to classify these EEG signals related to their state whether the subject is stressed by Airthmectic Operation or not.Each Subject is to carry out subtraction of two numbers in their minds and their EEG siganls are recorded.

Secondary goals include providing insight into which brain regions and frequency bands associate with each of the respective classes.There are mainly five classes **Delta(1-4Hz), Theta (4-8 Hz), Alpha (8-12 Hz), Beta (12-30 Hz), and Gamma (30-100
Hz)** We have to compute the Power spectrcal denisty(psd) in each frequency band.

## **Dataset Description**

The dataset Contain edf(European data format) files of 36 subjects.Each subject had gone through two different cognitive states and each subject has 2 edf files related to rest and stress state.

The dataset Has been taken from [PhysioNet]( https://physionet.org/physiobank/database/eegmat/)

The signals are of 0.5-45 Hz, with a sampling rate 500Hz.

## **Approaches**

1. This approach is based on deep learning Architecture of [EEGnet](https://github.com/FReakYdiVi/EEG-Classification/blob/main/EEGModels.py). We have used psd as feature extraction method like we have divided the EEG epoched signal into patches of frequency bands and calculating the psd over those bands. We have also tried statistical method for feature extraction but it produced not better results than psd

  ## *Result of first Approach* 
   This is with psd dataset 
  **Testing Accuracy**-0.8221963974433469
  ### Classification Report

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.82      | 0.97   | 0.89     | 1262    |
| 1     | 0.83      | 0.42   | 0.56     | 459     |

| Metric       | micro avg | macro avg | weighted avg | samples avg |
|--------------|-----------|-----------|--------------|-------------|
| Precision    | 0.82      | 0.82      | 0.82         | 0.82        |
| Recall       | 0.82      | 0.69      | 0.82         | 0.82        |
| F1-Score     | 0.82      | 0.72      | 0.80         | 0.82        |
| Support      | 1721      | 1721      | 1721         | 1721        |
   
   With referenced the result obtained from epoched array

   **Testing Accuracy**-0.7780360255665311

   ### **Classification Report**

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.78      | 0.98   | 0.87     | 1262    |
| 1     | 0.81      | 0.22   | 0.35     | 459     |

| Metric       | micro avg | macro avg | weighted avg | samples avg |
|--------------|-----------|-----------|--------------|-------------|
| Precision    | 0.78      | 0.79      | 0.78         | 0.78        |
| Recall       | 0.78      | 0.60      | 0.78         | 0.78        |
| F1-Score     | 0.78      | 0.61      | 0.73         | 0.78        |
| Support      | 1721      | 1721      | 1721         | 1721        |

You can clearly see that how using psd as feature extraction method is much better.

2. The second approach was based on The EEG signals acquired from the dataset were augmented using a **variational autoencoder** (VAE).The augmented EEG signals were later used for Classifier model.There are two CLassifier models, EEGnet and other one is from [research paper](https://arxiv.org/pdf/2302.00789#:~:text=Specifically%2C%20a%20novel%20variational%20autoencoder,1%2D%20D%20convolutional%20neural%20network).
The data used in paper is different so we have to upate the kernel size and layers. 

Overall archiecture of Proposed model
![Alt text](Screenshot%202024-07-06%20at%2011.06.26%E2%80%AFAM.png)

## *Result of Second Approach* 









