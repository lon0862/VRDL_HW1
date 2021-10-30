# VRDL_HW1
200 bird images classification code for the assignment of Selected Topics in Visual Recognition using Deep Learning, NYCU, in fall 2021.

## Abstract
In this work,I use efficientnet-b6 to train model, and all the work is done on Google Colab with gpu.<br>
You can follow the notebook to check the detail if you want.<br>

## Reproducing submission
To reproduct my submission, do the following steps:
1. [Installation](#installation)
2. [Data preparation](#data-preparation)
## Installation

## Data preparation
Origin TA give us train_images,test_images as the data directory.<br>
train_images has 3000 bird images.<br>
test_images has 3033 bird images.<br>
They are structured as:
```
+- train_images
    +- 0003.jpg
    +- 0008.jpg
    ...
  +- test_images
    +- 0001.jpg
    +- 0002.jpg
    ...
```
After downloading train_images,train_images_new,valid_images, the data directory is structured as:
## Pretrain model
