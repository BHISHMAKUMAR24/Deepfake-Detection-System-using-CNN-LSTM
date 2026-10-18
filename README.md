# Deepfake Video Detection System using CNN + LSTM

## Overview

The **Deepfake Video Detection System** is a deep-learning-based application designed to identify manipulated videos by analyzing facial features and temporal inconsistencies across video frames.

Deepfake technology uses artificial intelligence to create or manipulate videos, making people appear to say or do things they never actually did. These videos can be used to spread misinformation, impersonate individuals, and create misleading digital content.

This project combines **Convolutional Neural Networks (CNNs)** and **Long Short-Term Memory (LSTM) networks** to analyze both spatial information within individual frames and temporal patterns across a sequence of frames. The system predicts whether an uploaded video is REAL or FAKE.

The project was presented at **SVCE Innovates 2026**, where it secured first place at Student Research Day.

## Objectives

- Detect deepfake videos using deep learning.
- Extract facial information from video frames.
- Identify visual artifacts and inconsistencies in facial features.
- Analyze temporal relationships between consecutive frames.
- Classify videos as REAL or FAKE.
- Provide prediction results through a web-based interface.

## System Architecture

The system follows a hybrid deep-learning architecture combining CNN-based feature extraction with LSTM-based temporal analysis.

**Video Input → Frame Extraction → Face Detection → CNN Feature Extraction → LSTM Sequence Analysis → Binary Classification**

### 1. Video Preprocessing

The input video is processed using OpenCV. Frames are extracted from the video, and face detection is performed to focus the analysis on relevant facial regions. Frames without detectable faces can be excluded from the analysis.

### 2. CNN-Based Feature Extraction

A ResNeXt-50 convolutional neural network serves as the spatial feature extractor in the documented architecture. It extracts high-dimensional feature representations from individual face frames.

These features can capture visual patterns and irregularities associated with manipulated facial regions.

### 3. LSTM-Based Temporal Analysis

The extracted features are passed to an LSTM network, which learns relationships across a sequence of frames.

This temporal analysis helps identify inconsistencies that may not be apparent when examining individual frames independently, such as changes in facial appearance or unnatural transitions over time.

### 4. Classification

The learned temporal representation is passed through fully connected classification layers and a Softmax output to produce a binary prediction:

- **REAL:** The video is classified as authentic.
- **FAKE:** The video is classified as potentially manipulated.

The application can present the prediction and its associated confidence score, depending on the inference implementation.

## Dataset

The documented training-data sources include:

- **FaceForensics++** — videos containing authentic and manipulated facial content.
- **Deepfake Detection Challenge (DFDC)** — a dataset created for deepfake video detection.
- **Celeb-DF** — a dataset containing realistic celebrity deepfake videos.

The project notes describe a combined dataset of approximately 6,000 videos. Exact counts, preprocessing decisions, and train/test splits should be verified against the final dataset used in the repository.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| PyTorch | Deep-learning model development and inference |
| ResNeXt-50 | Spatial feature extraction |
| LSTM | Temporal sequence analysis |
| OpenCV | Video processing and frame extraction |
| Django | Web application and backend integration |
| Jupyter Notebook / Google Colab | Model experimentation and development |
| Git and GitHub | Version control and project management |

## Workflow

1. Upload a video through the application interface.
2. Extract representative frames from the video.
3. Detect and crop facial regions.
4. Extract spatial features using the CNN backbone.
5. Analyze sequential features using the LSTM network.
6. Perform binary classification.
7. Display the REAL or FAKE prediction and available confidence information.

## Key Features

- Automated video frame extraction and preprocessing.
- Face-focused video analysis.
- CNN-based spatial feature learning.
- LSTM-based temporal consistency analysis.
- Binary real-versus-deepfake classification.
- Web-based video submission and result presentation.

## Why CNN + LSTM?

A CNN and an LSTM address complementary aspects of video analysis.

A CNN learns spatial patterns within individual frames, while an LSTM models sequential dependencies across frames. Combining them allows the system to consider both facial appearance and how that appearance changes over time.

This is particularly useful because some manipulated videos may look convincing in isolated frames but exhibit inconsistencies when analyzed as a sequence.

## Research and Evaluation

Model performance should be evaluated using appropriate classification metrics, including:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix

Testing with different numbers of sampled frames can also help assess the trade-off between computational cost and detection performance.

For a reliable evaluation, the test set should be kept separate from training data, with care taken to prevent data leakage between related videos.

## Limitations

- Detection performance depends on the quality and diversity of the training data.
- Low-resolution videos, compression artifacts, and poor lighting may affect predictions.
- Previously unseen deepfake generation techniques may reduce generalization.
- A predicted label is not definitive proof that a video is authentic or manipulated.
- Confidence scores should not be interpreted as guaranteed probabilities of correctness unless properly calibrated.

## Future Enhancements

- Expand training and evaluation using more diverse datasets.
- Improve generalization to unseen manipulation techniques.
- Optimize inference speed for longer videos.
- Explore explainability methods to highlight suspicious facial regions.
- Add support for additional video formats and improved quality assessment.
- Evaluate robustness against compression, resizing, and other common video transformations.

## Conclusion

The Deepfake Video Detection System demonstrates how spatial feature extraction and temporal sequence learning can be combined to detect potentially manipulated videos. By integrating a CNN backbone, an LSTM network, video preprocessing, and a web application, the project provides a foundation for AI-assisted media authenticity analysis.

**Project Domain:** Artificial Intelligence, Deep Learning, Computer Vision, Video Forensics, and Media Authenticity.
