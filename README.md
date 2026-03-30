# CIFAR-10 CNN Classifier

CNN trained from scratch on the CIFAR-10 dataset using TensorFlow/Keras.
Achieved **76.7% test accuracy** with overfitting control through data augmentation, BatchNormalization, and Dropout.

## Results

| Version | Epochs | Test Accuracy | Train/Test Gap |
|---------|--------|---------------|----------------|
| v1 — no augmentation | 10 | 73.17% | ~3.3 pp |
| v2 — with augmentation | 20 | 76.69% | ~1.8 pp |

Data augmentation reduced overfitting by ~45% while improving test accuracy by 3.5 percentage points.

## Model Architecture

3 convolutional blocks followed by fully connected layers:
```
Input (32x32x3)
→ Conv2D(32) + BatchNorm + MaxPool + Dropout
→ Conv2D(64) + BatchNorm + MaxPool + Dropout
→ Conv2D(128) + BatchNorm + MaxPool + Dropout
→ Flatten → Dense(256) + Dropout
→ Dense(10, softmax)
```

Total parameters: 667,434 (~2.5 MB)

## Training

- Optimizer: Adam
- Loss: Sparse Categorical Crossentropy
- Batch size: 128
- Data augmentation: horizontal flip, rotation ±15°, width/height shift ±10%

## Training History

![Training History](https://raw.githubusercontent.com/Isay-cz/cifar10-cnn-classifier/main/notebooks/training_history.png)

## Tech Stack

- Python 3.12
- TensorFlow 2.21 / Keras 3.13
- NumPy, Matplotlib
- Google Colab (GPU)

## Limitations & Next Steps

The practical ceiling for custom CNNs on CIFAR-10 (32×32px) is ~80-83%.
Surpassing that threshold requires transfer learning.

## Usage

Open directly in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1ayUzYI7ibabe-HWblpgpKQ5jWJBZOdz6?usp=sharing)
