# Multiclass Semantic Segmentation for Road Data

This repository contains the implementation of a UNet model for multiclass semantic segmentation of road data. The project aims to accurately segment different classes in road scenes using deep learning techniques.

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Training and Validation](#training-and-validation)
- [Results](#results)
- [Requirements](#requirements)
- [Contributors](#contributors)
- [License](#license)

## Project Overview

This project utilizes a UNet model for multiclass semantic segmentation, focusing on road data. The goal is to accurately segment various elements within road scenes, such as vehicles, pedestrians, road markings, etc.

## Dataset

The dataset used for this project consists of images captured from road scenes with corresponding labeled masks for different classes. The dataset is preprocessed to standardize the input size and augment the data to improve model performance.

## Model Architecture

The model used in this project is a UNet, a convolutional neural network architecture designed for image segmentation tasks. The UNet model is composed of an encoder and a decoder:
- **Encoder**: Captures context through a series of downsampling operations.
- **Decoder**: Enables precise localization through a series of upsampling operations.

## Training and Validation

The model is trained using the training set, and its performance is validated on a separate validation set. Key metrics used for evaluating the model include training accuracy, validation accuracy, training loss, and validation loss.

## Results

The results of the UNet model experiment are encouraging:

- **Training Accuracy**: The training accuracy quickly reaches a high value close to 1.0 and remains stable, indicating effective learning of the training dataset.
- **Validation Accuracy**: Despite initial fluctuations, the validation accuracy improves steadily over time and stabilizes at a high level.
- **Training Loss**: The training loss remains low and stable, consistent with the high training accuracy.
- **Validation Loss**: The validation loss decreases significantly in the initial epochs and then stabilizes.

The Mean Intersection over Union (Mean IoU) score of 0.53 demonstrates the model's capability to learn and generalize the segmentation task effectively.

## Requirements

To run the code in this repository, you need the following dependencies:

- Python 3.x
- TensorFlow
- NumPy
- Matplotlib
- Other dependencies as listed in `requirements.txt`

## Contributors

- Muhammed Efe İncir

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
