# VRDL_HW1
200 bird images classification code for the assignment of Selected Topics in Visual Recognition using Deep Learning, NYCU, in fall 2021.<br>
Accuracy is 0.67194, over the baseline.<br>

## Abstract
In this work,I use efficientnet-b6 to train model, and all the work is done on Google Colab with gpu.<br>
You can follow the notebook to check the detail if you want.<br>

## Reproducing submission
To reproduct my submission, do the following steps:
1. [Installation](#installation)
2. [Data preparation](#data-preparation)
3. [Pretrain model](#pretrain-model)
4. [Inference](#inference)
5. [Make submission](#make-submission)

## Installation
Download all dataset and model from this link [VRDL_HW1](https://drive.google.com/drive/folders/1b717BfH1ZSHI1JrqZ8DDUDbMsScpT3qc?usp=sharing)
Its structured is:
```
VRDL_HW1
    +- train_images
    +- train_images_new
    +- test_images
    +- validation_images
    +- training_labels.txt
    +- classes.txt
    +- testing_img_order.txt
    +- answer.txt
    +- hw1_total.ipynb
    +- data_preparing.ipynb
    +- efficientnet_b6_pretrain.ipynb
    +- inference.ipynb
    +- weight_eff.pth
```
hw1_total.ipynb is the total code of data_preparing.ipynb, efficientnet_b6_pretrain.ipynb, inference.ipynb.<br>
You can just run it to data prepare, pretrain model and get the answer.txt to submit.<br>
All module and package you need to import is:
```
from google.colab import drive
import pandas as pd 
import torch
import torch.nn.functional as F
import torchvision
from torchvision.datasets import ImageFolder
from torch.utils.data import Dataset, DataLoader
import torchvision.transforms as T
import numpy as np
import os
import shutil
from PIL import Image
!pip install efficientnet_pytorch
from efficientnet_pytorch import EfficientNet
import torch.nn as nn
import torch.optim as optim
from torch.optim import lr_scheduler

%matplotlib inline
```
## Data preparation
Origin TA give us train_images,test_images as the data directory.<br>
And training_labels.txt as truth class for train_images, class.txt for class name<br>
train_images has 3000 bird images.<br>
test_images has 3033 bird images.<br>
They are structured as:
```
VRDL_HW1
    +- train_images
        +- 0003.jpg
        +- 0008.jpg
        ...
    +- test_images
        +- 0001.jpg
        +- 0002.jpg
        ...
```

I follow training_labels.txt and class.txt to do some preprocess to divide train_images into 200 class.<br>
And get one images in every class to validation_images, which is empty origin.<br>
You can download data_preparing.ipynb and use colab to do these process.<br>

Or you also can just download train_images_new, validation_images from the link to use.They are structured as:
```
VRDL_HW1
    +- train_images_new
        +- 001.Black_footed_Albatross
            +- 3154.jpg
            +- 3731.jpg
            ...
        +- 002.Laysan_Albatross
            +- 0847.jpg
            +- 1268.jpg
            ...
        ...
    +- validation_images
        +- 001.Black_footed_Albatross
            +- 3212.jpg
        +- 002.Laysan_Albatross
            +- 3666.jpg
        ...
```

## Pretrain model
I use model efficientnet-b6 and save wight to weight_eff.pth .<br>
You can download efficientnet_b6_pretrain.ipynb and use colab to run.<br>

## Inference
You need to download weight_eff.pth and inference.ipynb.<br>
Run inference.ipynb with colab, then you can get answer.txt, which output order is following testing_img_order.txt,and accuracy is 0.67194.<br>

## Make submission
Download answer.txt you produce,make it to zip file.<br>
Then upload it to [Codalab](https://competitions.codalab.org/competitions/35668?secret_key=09789b13-35ec-4928-ac0f-6c86631dda07)
