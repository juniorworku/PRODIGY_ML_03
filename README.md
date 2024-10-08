# Dog vs Cat Image Classification using Support Vector Machine (SVM)

## Project Overview

This project implements a Support Vector Machine (SVM) to classify images of cats and dogs from the [Kaggle Dogs vs Cats dataset](https://www.kaggle.com/c/dogs-vs-cats/data). The dataset contains labeled images of dogs and cats for training and unlabeled images for testing. 

The SVM classifier is trained using features extracted from images by applying the Histogram of Oriented Gradients (HOG), a powerful feature descriptor for image classification tasks.

## Table of Contents

1. [Dataset](#dataset)
2. [Project Structure](#project-structure)
3. [Requirements](#requirements)
4. [Preprocessing](#preprocessing)
5. [Feature Extraction](#feature-extraction)
6. [Model Training](#model-training)
7. [Model Evaluation](#model-evaluation)
8. [Results](#results)
9. [References](#references)

## Dataset

The dataset used is the Kaggle "Dogs vs Cats" dataset, which contains two directories:

- `train/`: Labeled images of dogs and cats (used for training).
- `test/`: Unlabeled images of dogs and cats (used for testing).

### Download the dataset
You can download the dataset from the official Kaggle competition page [here](https://www.kaggle.com/c/dogs-vs-cats/data).

## Project Structure

    ├── train/ # Training data folder 
    ├── test/ # Test data folder 
    ├── svm_dog_vs_cat.py # Main Python file for the SVM model 
    ├── README.md # This README file 
    |── requirements.txt # Required Python packages


## Requirements

To run this project, ensure that you have the following libraries installed:

- Python 3.x
- OpenCV
- NumPy
- Scikit-learn
- TQDM (for progress bars)
- Matplotlib (for visualization)
- Scikit-image (for HOG feature extraction)

You can install the required dependencies using the following command:

```sh
pip install opencv-python numpy scikit-learn tqdm matplotlib scikit-image
```

## Preprocessing

The images are first converted to grayscale to reduce computational complexity, and resized to 64x64 pixels to ensure uniformity in the input data. Preprocessing includes the following steps:

- Grayscale Conversion: Convert each image to grayscale.
- Resizing: Resize all images to 64x64 pixels.

## Feature Extraction

We use Histogram of Oriented Gradients (HOG) to extract meaningful features from the images. HOG is a feature descriptor that captures object structure and shape, making it suitable for distinguishing between dogs and cats.

For each image, HOG features are extracted using the following parameters:

- Orientations: 8
- Pixels per cell: 8x8
- Cells per block: 2x2

## Model Training

Once the HOG features are extracted from the training images, we use an SVM with a linear kernel to classify the images into two classes:

- 0: Cat
- 1: Dog
The SVM classifier is trained using the labeled training dataset. You can experiment with different kernels such as 'rbf' for improved results.

## Training Process

```sh
from sklearn.svm import SVC
svm = SVC(kernel='linear')
svm.fit(train_hog_features, train_labels)
```

## Model Evaluation

After training the model, use the test dataset to make predictions. If the test dataset contains true labels, the model's accuracy can be evaluated.

To make predictions on the test dataset:

```sh
test_predictions = svm.predict(test_hog_features)
```

## Results

- The accuracy of the model depends on several factors such as the feature extraction process and the kernel used in the SVM.
- You can also visualize some of the sample predictions to get an idea of how well the model performs on the test data.

## References

- [Kaggle Dogs vs Cats Dataset](https://www.kaggle.com/c/dogs-vs-cats/data)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
-[OpenCV Documentation](https://docs.opencv.org/4.x/index.html)
