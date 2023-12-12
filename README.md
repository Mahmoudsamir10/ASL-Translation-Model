# ASL-Translation-Model

This repository contains code to build an American Sign Language (ASL) Translation Model using MediaPipe landmarks detection as a starting point.

## Sections

- **Importing Libraries**: Install necessary libraries and import dependencies.
- **Data Preparation**: Load and organize the dataset information, extracting essential details like gloss, video paths, frame numbers, and split types.
- **MediaPipe Implementation**: Implementation details to extract landmarks for hands, pose, and face.
- **Visualizing Landmarks**: Code to visualize landmarks on images and videos.
- **Data Encoding**: Encode the data using landmarks for further processing.
- **Data Loading**: Load the encoded data for training and testing.
- **Data Augmentation**: Techniques used for data augmentation, including rotation, zoom, shift, mask, horizontal flip, and speedup.
- **Data Preprocessing**: Preprocess data for model input using two methods: sequencing and padding.
- **Models**: Implementation of different models for the ASL Translation task, including Hady's, Kamel's, and Nour's models.

The repository includes:

- Kaggle Notebook for the full code.
- Models implemented using TensorFlow/Keras for ASL Translation.
- Model visualization and saving checkpoints.
- Evaluation metrics, training logs, and model performance plots.

Refer to the respective sections in the notebook for detailed instructions on how to execute each part of the code.

### Note

- Ensure dataset paths are correctly set for loading and saving data.
- Adjust parameters and hyperparameters for data processing and model training based on specific requirements.
- Checkpoints and trained models are saved for future use or model evaluation.
