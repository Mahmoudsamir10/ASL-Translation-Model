# ASL-Translation-Model

This repository contains code to build an American Sign Language (ASL) Translation Model using MediaPipe landmarks detection as a starting point.

# Sections

## Installation 
- Install miniConda from [here](https://docs.anaconda.com/free/miniconda/)
- Create a new conda environment 
```bash
    $ conda create -n asl-demo python=3.9
```
- Activate conda env
```bash
    $ conda activate asl-demo
```
- Install the requirement.txt file using this command
```bash
    $ pip install -r requirement.txt
```
## Datasets
In our project, we experimented with two datasets: WLASL and ASL Citizen. ASL Citizen offers a notable advantage due to its larger number of examples per word. Additionally, the quality of the videos in ASL Citizen was more consistent compared to WLASL.
| Dataset | Link     |
| :-------- | :------- |
| `WLASL` | [WLASL Link](https://www.kaggle.com/datasets/risangbaskoro/wlasl-processed) |
| `ASL Citizen` | [ASL Citizen Link](https://www.kaggle.com/datasets/abd0kamel/asl-citizen) |

## Data Preparation
Both WLASL and ASL Citizen datasets are structured as CSV files. We read these CSV files to extract the video data along with associated gloss and split information. This split categorizes the dataset into train, test, and validation subsets.
## MediaPipe Implementation
We utilized MediaPipe to extract landmarks from each frame of every video. These landmarks comprised a total of 180 points, which were categorized into 132 face landmarks, 6 pose landmarks, and 42 hand landmarks.
## Data Augmentation
We tried different types of augmentation to increase the number of examples per gloss. these methods are:
- **Rotate**: Rotates the landmarks data using a specified rotation matrix. This method helps introduce variations in the orientation of the hand or body gestures.

- **Rotate Z**: Rotates the landmarks data around the z-axis by a random angle. This augmentation simulates changes in the hand or body orientation along the depth axis.

- **Rotate Y**: Rotates the landmarks data around the y-axis by a random angle. This augmentation introduces variations in the hand or body orientation along the vertical axis.

- **Rotate X**: Rotates the landmarks data around the x-axis by a random angle. This augmentation simulates changes in the hand or body orientation along the horizontal axis.

- **Zoom**: Zooms the landmarks data by scaling the coordinates around a specified center point. This augmentation helps simulate changes in the distance between the camera and the signer.

- **Shift**: Shifts the landmarks data by a random amount along the x and y axes. This augmentation introduces spatial translations in the hand or body gestures.

- **Mask**: Masks a portion of the landmarks data by setting selected landmarks to zero. This augmentation helps simulate occlusions or missing data in the input.

- **Speedup**: Speeds up the sequence of frames by selecting every alternate frame. This augmentation helps vary the speed of the gestures captured in the video sequence.
## Data Preprocessing
Preprocessing involves preparing the data to serve as input for the model by ensuring uniformity in the number of frames per video across the entire dataset. Additionally, we explored various preprocessing methods to enhance the data for improved model performance.
- **Padding**: This method pads the input sequences to make them of equal length. It takes the maximum length among all input sequences and pads each sequence accordingly. If a sequence is longer than the specified length, it truncates the sequence; otherwise, it pads the sequence with a specified padding value.

- **Sequencing**: This method generates sequences of fixed length from input sequences. It slides a window of fixed length over each input sequence, creating multiple smaller sequences (subsequences) with a specified step size. It generates corresponding labels for each generated sequence.

- **Interpolation**: This method interpolates the input sequences to a fixed length. It applies linear interpolation to each feature dimension of the input sequences to resample them to the desired length. This is useful for standardizing the length of variable-length sequences.

- **Padding from center**: This method pads input sequences from their center to make them of equal length. If a sequence is shorter than the desired length, it calculates the required padding before and after the sequence to make its length equal to the desired length. It pads the sequence with zeros or a specified padding value accordingly.

- **Padding with none**: Similar to the padding method, this method pads input sequences with a specified length. However, if a sequence is shorter than the desired length, instead of using a constant padding value, it randomly selects frames from a predefined "none" sample and pads the sequence with these frames. This technique introduces variability in the padding process.
## Model
In our exploration of various models, we experimented with a wide range of architectures, spanning from simple 1D convolutional networks and Long Short-Term Memory (LSTM) networks to more complex models incorporating custom transformer layers. Our efforts yielded promising results, with our models achieving a peak accuracy of 22% when trained on the WLASL dataset and a remarkable 80% accuracy when trained on the ASL Citizen dataset.

The selection of these diverse architectures allowed us to analyze and compare their performance across different datasets. We conducted extensive hyperparameter tuning and architecture adjustments to optimize the models for each dataset.
## Demo
Inside the demo folder, you'll discover a notebook showcasing the implementation of the ASL Translation Model. This notebook demonstrates the model's functionality with both live video feeds and pre-recorded videos. Additionally, it prints the translation output directly onto the frame for easy reference.



The repository includes:

- Kaggle Notebook for the full code.
- Models implemented using TensorFlow/Keras for ASL Translation.
- Model visualization and saving checkpoints.
- Evaluation metrics, training logs, and model performance plots.

Refer to the respective sections in the notebook for detailed instructions on how to execute each part of the code.

