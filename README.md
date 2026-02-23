# Real-Time Image Classification using Camera and SVM

A Python-based real-time image classification system that uses webcam input to train a Support Vector Machine (SVM) classifier for distinguishing between two user-defined object categories.

## Overview

This project demonstrates how to build an interactive machine learning application that captures images from your webcam, trains a classification model, and performs real-time predictions. The system uses a simple GUI built with Tkinter and leverages scikit-learn's LinearSVC for classification.

## Features

- **Interactive GUI**: Easy-to-use Tkinter interface for capturing images and managing the classifier
- **Custom Categories**: Define your own two-class classification problem (e.g., "Paper" vs "Book")
- **Real-time Training**: Capture training images directly from your webcam
- **Live Predictions**: Classify objects in real-time with auto-prediction mode
- **Model Reset**: Clear all data and retrain from scratch anytime

## Requirements

### Python Packages

```
tkinter (usually included with Python)
opencv-python (cv2)
Pillow (PIL)
scikit-learn
numpy
```

### Installation

Install the required packages using pip:

```bash
pip install opencv-python pillow scikit-learn numpy
```

## Usage

### 1. Start the Application

Run the main Python file:

```bash
python main.py
```

A Tkinter window will open displaying your webcam feed.

### 2. Define Your Classes

When prompted, enter names for your two classification categories:
- First class (e.g., "paper")
- Second class (e.g., "book")

These names will be used for organizing captured images and displaying predictions.

### 3. Capture Training Images

- Position an object from the first class in front of the camera
- Click the button labeled with your first class name to capture images
- Repeat for the second class
- **Recommended**: Capture 10-20 images per class for better accuracy
- Try different angles, distances, and lighting conditions

### 4. Train the Model

Once you have sufficient training images:
- Click the **"Train Model"** button
- The system will process all captured images and train the SVM classifier
- Wait for the console message confirming successful training

### 5. Make Predictions

Two prediction modes are available:

**Manual Mode:**
- Click the **"Predict"** button to classify the current webcam frame

**Auto Prediction Mode:**
- Toggle **"Auto Prediction"** to enable continuous real-time classification
- The predicted class will update automatically for each frame

### 6. Reset (Optional)

To start over with new classes or retrain the model:
- Click the **"Reset"** button
- This deletes all captured images and clears the trained model

## How It Works

### Image Capture and Storage
- Images are captured in grayscale from the webcam
- Class 1 images are saved to the `1/` directory
- Class 2 images are saved to the `2/` directory

### Model Training
1. All captured images are loaded and resized to a standard dimension (160x120 pixels)
2. Images are flattened into 1D arrays for the SVM classifier
3. A LinearSVC model is trained on the labeled dataset
4. The trained model is stored in memory for predictions

### Prediction
- Current webcam frames are preprocessed (grayscale conversion, resizing)
- The flattened image is passed to the trained SVM model
- The predicted class label is displayed in the GUI

## Applications

- **Educational Tool**: Demonstrates fundamental machine learning concepts and computer vision workflows
- **Prototype Development**: Foundation for building more sophisticated vision systems
- **Object Recognition**: Quick and simple binary classification for physical objects
- **Automation**: Can be adapted for industrial sorting or quality control applications
- **Gesture Recognition**: Potential starting point for gesture-based interfaces

## Technical Details

### Machine Learning
- **Algorithm**: Linear Support Vector Classifier (LinearSVC)
- **Image Preprocessing**: Grayscale conversion, resizing to 160x120 pixels
- **Feature Representation**: Flattened pixel arrays (19,200 features)

### Computer Vision
- **Library**: OpenCV for webcam access and image processing
- **Format**: Grayscale images reduce computational complexity while maintaining classification accuracy

### User Interface
- **Framework**: Tkinter for cross-platform GUI
- **Components**: Live video feed, class buttons, control buttons, prediction display

## Limitations and Considerations

- **Binary Classification**: Currently supports only two classes
- **Lighting Sensitivity**: Performance may vary with lighting conditions
- **Simple Features**: Uses raw pixel values rather than advanced feature extraction
- **Training Data**: Requires manual data collection for each new classification task

## Future Enhancements

Potential improvements to consider:
- Support for more than two classes
- Advanced feature extraction (HOG, SIFT, CNN-based features)
- Model persistence (save/load trained models)
- Confidence scores for predictions
- Data augmentation for improved robustness
- Performance metrics and validation

## Troubleshooting

**Webcam not detected:**
- Ensure your webcam is connected and not in use by another application
- Check camera permissions in your operating system

**Poor classification accuracy:**
- Capture more training images (20-30 per class recommended)
- Ensure training images have varied angles and positions
- Improve lighting conditions
- Make sure the two classes are visually distinct

**GUI not responding:**
- Check if the application is waiting for user input in a dialog box
- Restart the application if it becomes unresponsive

## Acknowledgments

Built using:
- [OpenCV](https://opencv.org/) for computer vision capabilities
- [scikit-learn](https://scikit-learn.org/) for machine learning algorithms
- [Tkinter](https://docs.python.org/3/library/tkinter.html) for GUI development
