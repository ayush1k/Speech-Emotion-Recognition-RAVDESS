# Speech Emotion Recognition with RAVDESS

This repository contains a reference notebook for building a speech emotion recognition (SER) system using the RAVDESS dataset. The project demonstrates how to download audio data, extract acoustic features from speech signals, train multiple machine learning models, and use the best model to predict emotions from new audio files.

## Overview

Speech emotion recognition is the task of identifying a speaker’s emotional state from voice characteristics such as tone, pitch, energy, and timbre. In this project, the notebook uses a classic machine learning pipeline:

1. Download and organize the RAVDESS audio dataset.
2. Extract meaningful acoustic features from each waveform.
3. Map filename-based emotion labels to human-readable categories.
4. Train and compare several classifiers.
5. Use the best-performing model to predict the emotion of a new audio sample.

## What the notebook does

The notebook in [ML_for_speech.ipynb](ML_for_speech.ipynb) performs the following steps:

- Downloads the RAVDESS speech audio dataset from Zenodo.
- Extracts audio features using librosa, including:
  - MFCCs (Mel-Frequency Cepstral Coefficients)
  - Chroma features
  - Mel spectrogram features
- Builds a feature matrix for all audio files.
- Splits the data into training and testing sets.
- Trains and evaluates multiple classifiers:
  - Support Vector Machine (SVM)
  - Random Forest Classifier
  - Multi-Layer Perceptron (MLP)
- Visualizes model performance with a confusion matrix.
- Provides a helper function to test the trained model on a single audio file.

## Dataset

This project uses the RAVDESS (Ryerson Audio-Visual Database of Emotional Speech and Song) dataset.

The dataset contains recordings from professional actors expressing multiple emotions. The notebook focuses on the audio-only portion and maps the emotion identifiers in each filename to eight labels:

- Neutral
- Calm
- Happy
- Sad
- Angry
- Fearful
- Disgust
- Surprised

## Project structure

```text
Speech-Emotion-Recognition-RAVDESS/
├── ML_for_speech.ipynb
├── README.md
└── ravdess_data/          # created after running the notebook
```

## Requirements

The notebook requires Python 3 and the following packages:

- numpy
- librosa
- soundfile
- matplotlib
- scikit-learn

You can install them with:

```bash
pip install numpy librosa soundfile matplotlib scikit-learn
```

## Setup

1. Clone the repository.
2. Open [ML_for_speech.ipynb](ML_for_speech.ipynb) in Jupyter Notebook or JupyterLab.
3. Run the cells in order.
4. The notebook will download the dataset automatically and create the local data folder.

## How to run the notebook

Open the notebook and execute the cells sequentially:

- The first cells download the dataset and import required libraries.
- Feature extraction is performed in the next section.
- The data loading step prepares the training and testing sets.
- Model training and evaluation follow.
- The final section demonstrates how to test a single audio sample.

## Model workflow

The typical workflow in the notebook is:

1. Load an audio file.
2. Convert the waveform into a fixed-length feature vector.
3. Feed the feature vector into a classifier.
4. Predict the emotion label.

The extracted features are based on the audio signal’s spectral and temporal characteristics, which are often useful for distinguishing emotional tone.

## Notes about the implementation

- The notebook uses a simple but effective feature engineering approach based on acoustic descriptors.
- The current notebook sets the default best model to the Random Forest classifier, but you can change this after comparing the model accuracies.
- The dataset download relies on an internet connection.
- Some audio files may be skipped if there is an issue during feature extraction.

## Expected output

When you run the notebook, you should see:

- The number of training and testing samples loaded.
- Accuracy scores for the SVM, Random Forest, and MLP models.
- A confusion matrix for the selected best model.
- A predicted emotion label for the sample audio file.

## Limitations

This project is intended as a beginner-friendly reference implementation. It does not include advanced deep-learning architectures such as CNNs or transformers, and performance can vary depending on the feature set and dataset preprocessing choices.

## Future improvements

Possible extensions to this project include:

- Adding more advanced audio features such as zero-crossing rate, spectral contrast, or pitch-based features.
- Comparing deep learning models such as CNNs or LSTMs.
- Adding data augmentation to improve generalization.
- Building a small web app or command-line interface for real-time prediction.

## Summary

This repository provides a complete example of how to build a speech emotion recognition pipeline from scratch using classical machine learning. It is a strong starting point for learning how audio data can be transformed into features and used to classify emotions.
