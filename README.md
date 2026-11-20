# Semantic Segmentation of Road Scenes with a U-Net

An object detector draws a box around a car. **Semantic segmentation** goes further: it labels *every pixel* of the image (road, car, building, sky, …). That pixel-level understanding is what a self-driving car needs to know where it can drive. This project trains a **U-Net** to do it on small road images.

## The data

265 road-scene photos at 160 × 120 pixels, each with a mask image in which every pixel stores the **class ID** of the object it belongs to. The images are small on purpose, so the whole model trains in minutes on a single GPU.

## Why a U-Net?

A U-Net is an encoder-decoder with shortcuts:

- The **encoder** repeatedly downsamples the image, learning *what* is in it (large-scale context).
- The **decoder** upsamples back to full resolution, recovering *where* it is.
- **Skip connections** copy high-resolution features from the encoder to the decoder, so thin structures and object boundaries are not lost on the way down.

The network is built from repeated blocks of two 3 × 3 convolutions with batch normalisation (an encoder block, a bottleneck and a decoder block with transposed convolutions), ending in a per-pixel softmax over the classes. It is trained with categorical cross-entropy and the Adam optimiser, batch size 16, for 60 epochs.

## What the results show

- **Training accuracy** climbs quickly towards 1.0 and stays there: the model fits the training images well.
- **Validation accuracy** is erratic in the first epochs (the network is still settling) and then improves steadily and stabilises at a high level.
- **Mean IoU is about 0.53.** Pixel accuracy flatters a segmentation model because large background classes dominate the pixel count. Mean Intersection-over-Union averages the overlap per class, so rare classes count as much as common ones, and it is the more honest score. A value around 0.5 on only 265 training images is a solid result and leaves clear room for improvement.

## What you can take from this

1. For dense prediction, *accuracy is not enough*. Use IoU, which is not inflated by easy background pixels.
2. Skip connections are what make U-Nets work on small datasets: they preserve detail that downsampling destroys.
3. The next steps with the biggest payoff would be data augmentation (flips, crops, brightness changes) and a pre-trained encoder.

## Files

- `Multiclass_SS_for_road_data.ipynb`: model, training, curves and evaluation
- `CameraRGB160x120.zip`, `CameraMask160x120.zip`: the images and their masks
