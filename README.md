# 🩺 Breast Cancer Prediction using Deep Learning

A deep learning-based image classification project that classifies breast tumor images as **Benign (Non-Cancerous)** or **Malignant (Cancerous)** using **MobileNetV2** and transfer learning.

This project was developed as a **group project**, with my primary contribution focused on **data augmentation and image preprocessing** to improve model generalization and reduce overfitting.

---

## 📌 Project Overview

Breast cancer detection is an important medical image classification problem. This project uses a pre-trained **MobileNetV2** model to extract image features and classify breast tumor images into two categories:

- **Benign** – Non-cancerous tumor
- **Malignant** – Cancerous tumor

The model uses transfer learning, data augmentation, fine-tuning, and regularization techniques to improve classification performance.

---

## 🚀 Features

- Breast tumor image classification
- Binary classification: Benign vs Malignant
- Transfer learning using MobileNetV2
- Image preprocessing and normalization
- Real-time data augmentation
- Fine-tuning of pre-trained layers
- Early stopping to prevent overfitting
- Adaptive learning rate reduction
- Prediction with confidence score
- Model evaluation using classification metrics and confusion matrix

---

## 🛠️ Technologies Used

- Python
- TensorFlow
- Keras
- MobileNetV2
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab

---

## 📂 Dataset Structure

The dataset is organized into training, validation, and testing folders:

    dataset/
    │
    ├── train/
    │   ├── benign/
    │   └── malignant/
    │
    ├── val/
    │   ├── benign/
    │   └── malignant/
    │
    └── test/
        ├── benign/
        └── malignant/

---

## 🔄 Project Workflow

1. Upload and extract the image dataset.
2. Resize all images to `128 × 128` pixels.
3. Normalize pixel values from `0–255` to `0–1`.
4. Apply data augmentation to the training images.
5. Load the pre-trained MobileNetV2 model.
6. Fine-tune the last layers of MobileNetV2.
7. Add custom classification layers.
8. Train the model using training and validation data.
9. Evaluate the model on unseen test data.
10. Upload a new image and predict whether the tumor is benign or malignant.

---

## 🖼️ Data Preprocessing and Augmentation

The training images are normalized and augmented using Keras `ImageDataGenerator`.

The following augmentation techniques are applied:

- Rotation
- Zooming
- Horizontal flipping
- Width shifting
- Height shifting
- Shearing

Example:

    train_datagen = ImageDataGenerator(
        rescale=1./255,
        rotation_range=25,
        zoom_range=0.25,
        horizontal_flip=True,
        width_shift_range=0.25,
        height_shift_range=0.25,
        shear_range=0.2,
        fill_mode='nearest'
    )

Data augmentation increases image diversity and helps reduce overfitting.

Validation and test images are only normalized and are not augmented.

---

## 🧠 Model Architecture

The project uses **MobileNetV2**, pre-trained on the ImageNet dataset, as the base model.

The final architecture consists of:

    MobileNetV2
          ↓
    GlobalAveragePooling2D
          ↓
    Dense Layer (512 neurons, ReLU)
          ↓
    Batch Normalization
          ↓
    Dropout (0.5)
          ↓
    Dense Layer (1 neuron, Sigmoid)
          ↓
    Benign / Malignant

### Why MobileNetV2?

MobileNetV2 is:

- Lightweight
- Computationally efficient
- Suitable for transfer learning
- Faster than many larger CNN architectures
- Effective for image classification tasks

---

## ⚙️ Model Configuration

- **Image Size:** 128 × 128
- **Batch Size:** 16
- **Optimizer:** Adam
- **Learning Rate:** 0.0001
- **Loss Function:** Binary Cross-Entropy
- **Output Activation:** Sigmoid
- **Maximum Epochs:** 12

---

## 🔧 Fine-Tuning

The model uses transfer learning with ImageNet pre-trained weights.

Most of the MobileNetV2 layers are frozen, while the last 30 layers are available for fine-tuning. This allows the model to retain general image features learned from ImageNet while adapting deeper features to the breast tumor classification task.

---

## 📉 Callbacks Used

### EarlyStopping

Stops training when the validation performance stops improving and restores the best model weights.

### ReduceLROnPlateau

Reduces the learning rate when the validation loss stops improving, allowing the model to make smaller updates during training.

---

## 📊 Model Evaluation

The model is evaluated using:

- Test Accuracy
- Precision
- Recall
- F1-Score
- Classification Report
- Confusion Matrix

The confusion matrix helps analyze:

- True Positives
- True Negatives
- False Positives
- False Negatives

---

## 🔍 Prediction

The trained model can accept a new breast tumor image and classify it as:

- **Benign (Non-Cancerous)**
- **Malignant (Cancerous)**

The output also displays the model's confidence score.

Example output:

    Prediction: Malignant (Cancerous)
    Confidence: 0.96

---

## 👩‍💻 My Contribution

This was a group project. My primary contribution was focused on:

- Image preprocessing
- Implementing data augmentation using `ImageDataGenerator`
- Applying rotation, zoom, shift, shear, and horizontal flip transformations
- Improving dataset diversity
- Helping reduce model overfitting and improve generalization

---

## 💡 Future Improvements

- Deploy the trained model using Streamlit
- Use a larger and more diverse medical image dataset
- Compare MobileNetV2 with other models such as ResNet and EfficientNet
- Apply advanced augmentation techniques
- Improve model explainability using Grad-CAM
- Perform further hyperparameter tuning

---

## ⚠️ Disclaimer

This project is developed for **educational and research purposes only**. The predictions generated by this model should not be considered a medical diagnosis. Medical decisions should always be made by qualified healthcare professionals.

