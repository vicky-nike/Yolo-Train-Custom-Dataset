# Training on custom dataset in Google colab

## Requirments

1. Download or clone Yolov4 framework from [this site](https://github.com/AlexeyAB/darknet.git).

   All the requirments can be found in that repo.

   Visit the website for more information about the [darknet](http://pjreddie.com/darknet/)

2. Download yolov3 weights from [here](https://pjreddie.com/media/files/yolov3.weights) OR download the yolov4 weights from [here](https://drive.google.com/open?id=1cewMfusmPjYWbrnuJRuKhPMwRe_b9PaT)

3. Download pretrained weight darknet53.conv.74 from [here](https://pjreddie.com/media/files/darknet53.conv.74)

## How to edit yolov3_custom_train.cfg file

1. Make a copy of *yolov3.cfg*/*yolov4.cfg* in same directory and rename to *yolov3_custom_train.cfg* and open in wordpad. Comment 3rd and 4th line

   ```python
   [net]
   #Testing
   #batch=1
   #subdivisions=1
   #Training
   batch=64
   subdivisions=32
   width=416
   height=416
   channels=3
   momentum=0.9
   decay=0.0005
   angle=0
   saturation = 1.5
   exposure = 1.5
   hue=.1
   ```
2. Now in 20th line we have to change max_batches and steps according to number of classes.

    _max_batches = 2000*(number of class)_

    steps = (0.8 x max_batches), (0.9 x max_batches)
    >It is 80% and 90% of max batch

    Here I'm working on only one class so,

   ```python
   learning_rate=0.001
   burn_in=1000
   max_batches = 2000
   policy=steps
   steps= 1600, 1800
   scales=.1,.1
   ```

3. Now search for keyword "yolo" by pressing crtl+f. Change the classes as per the our requirement. And above this *[yolo]* part will be *[convolutional]*, change the filters as:-

   _filters = (5 + number_of_classes) * 3_

   In my case

   ```python
   [convolutional]
   size=1
   stride=1
   pad=1
   filters=18
   activation=linear


   [yolo]
   mask = 6,7,8
   anchors = 10,13,  16,30,  33,23,  30,61,  62,45,  59,119,  116,90,  156,198,  373,326
   classes=1
   num=9
   jitter=.3
   ignore_thresh = .7
   truth_thresh = 1
   random=1
   ```

   Search and change other *[yolo]* & *[convolutional]* parts too using crtl+f

   *Note: You may change "random=0" in [yolo] part to speed up training but accuracy will decrease.*

## How to edit yolov3_custom_test.cfg file

   Make a copy of the *yolov3_custom_train.cfg* file in same directory and rename it to *yolov3_custom_test.cfg*.

   The only change we have to make is uncomment training section and comment training section as below:

   ```python
   [net]
   #Testing
   batch=1
   subdivisions=1
   #Training
   #batch=64
   #subdivisions=16
   width=416
   height=416
   channels=3
   #momentum=0.9
   #decay=0.0005
   #angle=0
   #saturation = 1.5
   #exposure = 1.5
   #hue=.1
   ```

## Creating yolo.names file

In darknet/data/ directory you will find *obj.names* or *voc.names* file. Make a copy of that file and rename to *yolo.names* in same directory.

Open this file in Notepad and keep only the class you are working on.

## Creating yolo.data file

In darknet/data/ directory, copy and rename the file *obj.data* into *yolo.data* and edit it in notepad.

```python
Classes=1
train = data/train.txt
test = data/test.txt
names = data/yolo.names
backup = backup
```
