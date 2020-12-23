# Basic YOLO code for Google Colab

## Requirments

1. Download or clone Yolov4 framework from [this site](https://github.com/AlexeyAB/darknet.git).
   All the requirments can be found in that repo.

   Visit the website for more information about the [darknet](http://pjreddie.com/darknet/)

2. Download yolov3 weights from [here](https://pjreddie.com/media/files/yolov3.weights) OR download the yolov4 weights from [here](https://drive.google.com/open?id=1cewMfusmPjYWbrnuJRuKhPMwRe_b9PaT)

3. Download pretrained weight darknet53.conv.74 from [here](https://pjreddie.com/media/files/darknet53.conv.74)

## About the code

This code use pre-trained model to detect the below classes.

   >'person', 'bicycle', 'car', 'motorbike', 'aeroplane', 'bus', 'train', 'truck', 'boat', 'traffic light', 'fire hydrant', 'stop sign', 'parking meter', 'bench', 'bird', 'cat', 'dog', 'horse', 'sheep', 'cow', 'elephant', 'bear', 'zebra', 'giraffe', 'backpack', 'umbrella', 'handbag', 'tie', 'suitcase', 'frisbee', 'skis', 'snowboard', 'sports ball', 'kite', 'baseball bat', 'baseball glove', 'skateboard', 'surfboard', 'tennis racket', 'bottle', 'wine glass', 'cup', 'fork', 'knife', 'spoon', 'bowl', 'banana', 'apple', 'sandwich', 'orange', 'broccoli', 'carrot', 'hot dog', 'pizza', 'donut', 'cake', 'chair', 'sofa', 'pottedplant', 'bed', 'diningtable', 'toilet', 'tvmonitor', 'laptop', 'mouse', 'remote', 'keyboard', 'cell phone', 'microwave', 'oven', 'toaster', 'sink', 'refrigerator', 'book', 'clock', 'vase', 'scissors', 'teddy bear', 'hair drier', 'toothbrush'

This code is available in their official [website](https://pjreddie.com/darknet/yolo/) . This code is modified to run in google colab.