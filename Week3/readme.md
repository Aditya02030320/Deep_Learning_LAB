# MNIST Digit Classification with Convolutional Neural Networks

## Overview & Aim

The goal of this project is to build and train a Convolutional Neural Network (CNN) using TensorFlow and Keras to accurately classify grayscale images of handwritten digits (from 0 to 9). 

This code demonstrates the foundational steps of image classification in deep learning, including data preprocessing, building a sequential CNN model, compiling it, and evaluating its performance.

## Dataset Used

This program uses the classic **MNIST** dataset directly loaded from `tensorflow.keras.datasets`.

* **Details:** The dataset consists of 60,000 training images and 10,000 testing images of handwritten digits. Each image is a 28x28 pixel grayscale image.
* **Preprocessing:** 
  * **Reshaping:** The images are reshaped to `(28, 28, 1)` to explicitly include the single color channel (grayscale) required by Keras convolutional layers.
  * **Standardisation:** The pixel values, which originally range from 0 to 255, are normalised to a scale of 0.0 to 1.0 by dividing by 255.0. This helps the neural network learn faster and more stably.

## Network Architecture
The model is built using a Keras `Sequential` architecture, featuring alternating convolutional and pooling layers for feature extraction, followed by dense layers for classification:

* **Conv2D Layer 1:** 32 filters of size 3x3, using **ReLU** activation. Accepts the 28x28x1 input.
* **MaxPooling2D Layer 1:** 2x2 pool size to downsample the spatial dimensions.
* **Conv2D Layer 2:** 64 filters of size 3x3, using **ReLU** activation.
* **MaxPooling2D Layer 2:** 2x2 pool size.
* **Conv2D Layer 3:** 64 filters of size 3x3, using **ReLU** activation.
* **Flatten Layer:** Converts the 2D matrix of extracted features into a 1D vector.
* **Dense (Hidden) Layer:** A fully connected layer with 64 neurons and **ReLU** activation to interpret the features.
* **Output Layer:** A fully connected layer with 10 neurons (one for each digit) using **Softmax** activation to output a probability distribution across the 10 classes.

## Results

The model is compiled using the **Adam** optimizer and the **Sparse Categorical Crossentropy** loss function (which is ideal for integer-labeled multi-class classification). 

After training for 5 epochs, a standard CNN of this architecture on the MNIST dataset typically achieves a very high test accuracy, often exceeding **98.5% to 99.0%**, demonstrating its strong capability in recognizing spatial patterns in handwritten digits.