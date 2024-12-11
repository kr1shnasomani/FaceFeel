# Facial Emotion Recognition
This project involves building a Convolutional Neural Network (CNN) for facial emotion recognition using the FER-2013 dataset. It preprocesses images, trains the model, evaluates accuracy, visualizes performance and includes a prediction function to classify emotions from images with confidence scores.

## Execution Guide:
1. Run the following command line in the terminal:
   ```
   pip install numpy pandas matplotlib seaborn opencv-python tensorflow scikit-learn kaggle
   ```

2.

## Overview:
The code is used for building, training and evaluating a Convolutional Neural Network (CNN) model for facial emotion recognition using the FER-2013 dataset. Here's an overview of the various steps and components involved:

1. **Importing Libraries**:
   - Essential libraries for data manipulation (NumPy, pandas), image processing (OpenCV, matplotlib, seaborn), and model development (TensorFlow, Keras) are imported.
   - Warnings are suppressed to avoid unnecessary messages during execution.

2. **Downloading and Unzipping the Dataset**:
   - The dataset (`fer2013`) is downloaded from Kaggle using the `!kaggle datasets download` command.
   - The dataset is unzipped using Python’s `zipfile` module.

3. **Data Preprocessing**:
   - Image data augmentation is applied using `ImageDataGenerator` for training images, which includes random transformations (like shifts and horizontal flips) to improve model generalization.
   - The images are scaled to a range between 0 and 1 (`rescale=1.0 / 255`).
   - A validation split is set aside from the training set to evaluate model performance.
   - Separate generators are created for the training and validation sets (`train_generator` and `validation_generator`).

4. **Model Architecture**:
   - A Sequential CNN model is defined with the following layers:
     - **Convolutional layers** (`Conv2D`) to learn spatial hierarchies of features.
     - **Max-pooling layers** (`MaxPool2D`) to downsample the feature maps.
     - **Batch Normalization** layers for faster convergence and reduced internal covariate shift.
     - **Dropout** layers for regularization to prevent overfitting.
     - **Dense layers** for classification with softmax activation to output the probability of each emotion class.
   - The model ends with a final output layer of 7 neurons (one for each emotion class) and softmax activation.

5. **Model Compilation**:
   - The Adam optimizer is used with a low learning rate (`0.0001`) for gradient descent optimization.
   - The loss function used is `categorical_crossentropy` (suitable for multi-class classification).

6. **Training the Model**:
   - The model is trained using the `fit` method with the training data (`train_generator`) and evaluated on the validation data (`validation_generator`).
   - The number of epochs is set to 100, and the model's training and validation accuracy/loss are tracked.
   
7. **Model Evaluation**:
   - After training, the model is evaluated on both the training and validation datasets using the `evaluate` method, and the accuracy is printed for both.
   
8. **Confusion Matrix**:
   - A confusion matrix is generated to visualize the performance of the model on the validation data. This matrix is plotted using `ConfusionMatrixDisplay` to show true vs predicted labels.

9. **Visualization of Accuracy and Loss**:
   - Accuracy and loss over epochs are plotted for both training and validation sets. This helps visualize the learning curve and assess model convergence.

10. **Prediction Function**:
   - A `predict_emotion` function is defined to predict the emotion of a given image. It:
     - Loads and preprocesses the input image.
     - Passes the image through the trained model to get predictions.
     - Maps the predicted class to the corresponding emotion label.
     - Displays the image with the predicted emotion and confidence score.
   - The function is then used to predict the emotion of an example image (`img_path`).

### Key Points:
- **Dataset**: FER-2013 dataset with 7 emotion classes (angry, disgust, fear, happy, neutral, sad, and surprise).
- **Data Augmentation**: Applied to the training set to improve generalization.
- **CNN Architecture**: Multiple convolutional layers with pooling, dropout for regularization, and dense layers for classification.
- **Evaluation Metrics**: Accuracy, confusion matrix, and loss/accuracy visualization are used for model evaluation.
- **Emotion Prediction**: Function to predict emotion from a given image and display the result with confidence.

### Final Output:
The code predicts the emotion of a given image, displays it and shows the confidence of the prediction. The model's performance is tracked through accuracy metrics and visualizations during training.
