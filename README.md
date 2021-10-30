# VRDL_HW1
200 bird images classification code for the assignment of Selected Topics in Visual Recognition using Deep Learning, NYCU, in fall 2021.
Accuracy is 0.67194, over the baseline
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
And training_labels.txt as truth class for train_images, class.txt for class name<br>
train_images has 3000 bird images.<br>
test_images has 3033 bird images.<br>
They are structured as:
```
train_images
    +- 0003.jpg
    +- 0008.jpg
    ...
test_images
    +- 0001.jpg
    +- 0002.jpg
    ...
```

I follow training_labels.txt and class.txt to do some preprocess to divide train_images into 200 class.<br>
And get one images in every class to validation_images, which is empty origin.<br>
```
drive.mount('/content/gdrive')  # link google drive
```
```
label_header = ["photo", "type"]
labels = pd.read_csv("/content/gdrive/My Drive/VRDL_HW1/training_labels.txt",
                     names=label_header, sep=' ')
train_fold = "/content/gdrive/MyDrive/VRDL_HW1/train_images_new"
valid_fold = "/content/gdrive/MyDrive/VRDL_HW1/validation_images"

class_header = ["type"]
class_data = pd.read_csv("/content/gdrive/My Drive/VRDL_HW1/classes.txt",
                         names=class_header, sep=' ')
test_fold = "/content/gdrive/MyDrive/VRDL_HW1/test_images"
```
```
# make training data to different folder
foldername = "/content/gdrive/MyDrive/VRDL_HW1/train_images"
for index in range(len(labels['photo'])):
    print(data)
    print(labels['photo'][index], labels['type'][index])
    fdname = train_fold + '/' + labels['type'][index]
    os.makedirs(fdname, exist_ok=True)
    shutil.move(foldername + '/' + labels['photo'][index], fdname)
```
```
# divide train data to validation data
for index in range(1):
    fdname_old = train_fold + '/' + class_data['type'][index]
    fdname_new = valid_fold + '/' + class_data['type'][index]
    os.makedirs(fdname_new, exist_ok=True)
    j = 0
    print(fdname_old)
    for file in os.listdir(fdname_old):
        if(j < 1):
            shutil.move(fdname_old + '/' + file, fdname_new + '/' + file)
            j += 1
```
You also can just download train_images_new,validation_images to use.They are structured as:
```
train_images_new
    +- 001.Black_footed_Albatross
        +- 3154.jpg
        +- 3731.jpg
        ...
    +- 002.Laysan_Albatross
        +- 0847.jpg
        +- 1268.jpg
        ...
    ...
validation_images
    +- 001.Black_footed_Albatross
        +- 3212.jpg
    +- 002.Laysan_Albatross
        +- 3666.jpg
    ...
```
## Pretrain model
