# Image Classification with CNNs using Keras

<div align="center">
  <img src="https://miro.medium.com/v2/resize:fit:700/1*1wDoZyhXhGvkfqpO0k0y6g.png" alt="CNN Image Classification Banner" width="85%" style="border-radius: 8px;">
</div>

<br>

<div align="center">

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mohd-faizy/02P_Project_Image_Classification_with_CNNs_using_Keras/blob/master/Image_Classification_with_CNN_using_Keras.ipynb)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![TensorFlow 2.x](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://www.tensorflow.org/)
[![Keras](https://img.shields.io/badge/Keras-3.x-red.svg)](https://keras.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

</div>

Deep learning project implementing a modular **Convolutional Neural Network (CNN)** in **Keras** with a **TensorFlow** backend to perform multi-class image classification on the **CIFAR-10** dataset (specifically distinguishing between **Aeroplanes**, **Cars**, and **Birds**).

---

## 📌 Project Overview

This repository demonstrates how to design, train, evaluate, and interpret a deep Convolutional Neural Network from scratch. The notebook is structured with modern best practices, including:
- Modular **hierarchical convolutional blocks** with `Conv2D`, `BatchNormalization`, and `MaxPooling2D`.
- Regularization via spatial **Dropout** to mitigate overfitting.
- Efficient training callbacks: **EarlyStopping** and **ModelCheckpoint**.
- Extensive diagnostic analytics: class distributions, RGB channel histograms, dual learning dynamics curves, normalized confusion matrices, and **intermediate feature map activations**.

---

## 📂 Repository Structure

```
02P_Project_Image_Classification_with_CNNs_using_Keras/
├── assets/
│   └── cifar10_examples.jpg                         # CIFAR-10 10x10 dataset visualization
├── Image_Classification_with_CNN_using_Keras.ipynb  # Primary Jupyter notebook with modern CNN pipeline
├── model_0.912.h5                                   # Pre-trained Keras model weights (~91.2% accuracy)
└── README.md                                        # Project documentation & overview
```

---

## 📊 Dataset: CIFAR-10 Subset

The **CIFAR-10** (Canadian Institute For Advanced Research) dataset is a benchmark collection of $60,000$ $32 \times 32$ color images across $10$ distinct classes ($6,000$ images per class).


<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/mohd-faizy/02P_Project_Image_Classification_with_CNNs_using_Keras@master/assets/cifar10_examples.jpg" alt="CIFAR-10 Dataset Examples" width="85%" style="border-radius: 8px;">
</div>


In this project, we extract and focus on a targeted **3-class classification problem**:
- **Class 0:** Aeroplane ✈️
- **Class 1:** Automobile (Car) 🚗
- **Class 2:** Bird 🐦

### Dataset Specifications
| Parameter | Value |
| :--- | :--- |
| **Total Classes in Benchmark** | 10 classes |
| **Classes Evaluated** | 3 (`aeroplane`, `car`, `bird`) |
| **Image Resolution** | $32 \times 32 \times 3$ (RGB) |
| **Normalization** | Scaled to $[0.0, 1.0]$ via $X / 255.0$ |
| **Target Encoding** | One-Hot Encoding (3 classes) |

---

## 🏗️ Model Architecture

The CNN architecture utilizes 3 stacked convolutional blocks followed by a dense classification head:

```
Input (32x32x3)
  │
  ├── Block 1: Conv2D (32, 3x3, same) ──► BatchNorm ──► Conv2D (32, 3x3) ──► MaxPool (2x2) ──► Dropout (0.5)
  │
  ├── Block 2: Conv2D (64, 3x3, same) ──► BatchNorm ──► Conv2D (64, 3x3) ──► MaxPool (2x2) ──► Dropout (0.5)
  │
  ├── Block 3: Conv2D (128, 3x3, same) ─► BatchNorm ──► Conv2D (128, 3x3) ─► MaxPool (2x2) ──► Dropout (0.5)
  │
  └── Classification Head: Flatten ──► Dense (3, Softmax)
```

- **Loss Function:** `categorical_crossentropy`
- **Optimizer:** `Adam(learning_rate=0.001)`
- **Evaluation Metric:** `accuracy`

---

## 🚀 Project Tasks & Workflow

The notebook is divided into 6 structured tasks:

### 1. Import Libraries & Hardware Setup
- Importing modern TensorFlow, Keras, NumPy, Matplotlib, Seaborn, and Scikit-learn.
- Hardware device verification (`tf.config.list_physical_devices('GPU')`).

### 2. Preprocess Data & Exploratory Analysis
- Vectorized filtering for the 3 target classes (`get_three_classes`).
- Random shuffling and standardizing pixel intensities to $[0.0, 1.0]$.
- **Class Distribution Plot:** Visual comparison of train vs. test splits.
- **RGB Intensity Histograms:** Exploratory channel distribution inspection across sample images.

### 3. Visualize Dataset Examples
- Visual grid displaying random training and test images with their ground-truth labels.

### 4. Create CNN Architecture
- Defining the modular `add_conv_block` function.
- Sequential model construction with explicit input dimensions and compilation.

### 5. Train the Model & Learning Diagnostics
- Training with test set validation.
- Callbacks: `EarlyStopping` (patience=4, restore best weights) and `ModelCheckpoint`.
- **Dual Learning Curves:** Synchronized accuracy and loss dynamics plots tracking optimization progression.

### 6. Evaluation, Performance Metrics & Interpretability
- Loading best saved model checkpoint (`model_0.912.h5`).
- **Confusion Matrix Heatmaps:** Dual visualization with raw counts and normalized recall percentages.
- **Per-Class Metrics Bar Chart:** Precision, Recall, and F1-Score breakdown per class.
- **Softmax Probability Distributions:** Sample test images paired with horizontal confidence bar charts.
- **Feature Map Activations:** Visual inspection of filters from the first `Conv2D` layer.

---

## 📈 Visual Diagnostics & Results

| Diagnostic Visualization | Purpose |
| :--- | :--- |
| **Class Distribution Bar Chart** | Verifies balanced class representation across training and test subsets |
| **RGB Channel Histograms** | Analyzes pixel value distributions across color spaces |
| **Dual Learning Curves** | Diagnoses model convergence, overfitting, and learning rates |
| **Normalized Confusion Matrix** | Pinpoints specific inter-class confusion patterns |
| **Softmax Confidence Bars** | Demonstrates model prediction certainty per test instance |
| **Feature Map Activations** | Visualizes learned low-level edge and texture detectors |

---

## 💻 Getting Started

### Prerequisites
Make sure you have Python 3.9+ and install the required dependencies:
```bash
pip install tensorflow keras numpy matplotlib seaborn scikit-learn
```

### Running Locally
Launch JupyterLab or VS Code and open the notebook:
```bash
jupyter notebook Image_Classification_with_CNN_using_Keras.ipynb
```

---

## 🔗 Connect with me

<div align="center">

[![Twitter](https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/F4izy)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohd-faizy/)
[![Stack Exchange](https://img.shields.io/badge/Stack_Exchange-1E5397?style=for-the-badge&logo=stack-exchange&logoColor=white)](https://ai.stackexchange.com/users/36737/faizy)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mohd-faizy)

</div>
