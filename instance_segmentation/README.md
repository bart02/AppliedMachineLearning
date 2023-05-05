# Assignment 2 - Instance Segmentation

https://colab.research.google.com/github/bart02/AppliedMachineLearning/blob/main/instance_segmentation/mask_rcnn.ipynb  
https://colab.research.google.com/github/bart02/AppliedMachineLearning/blob/main/instance_segmentation/yolov8.ipynb

## Task description
1. Take photos of your environment of two or more objects. (at least 100 instances between all objects, photos from Assignment 1 can be used)
2. Annotate them on Roboflow for segmentation
3. Train a Mask RCNN model using detectron2
4. Train Yolov8 the smallest size for segmentation
5. Evaluate both models based on mAP and speed and size

## Process
### 1. Data collection
I used [collected dataset from Assignment 1](../object_detection#1-data-collection) of 2 objects: a pepperjack, an Apple charger.

### 2. Data annotation
I used detection annotations from [Assignment 1](../object_detection#2-data-annotation).

For segmentation annotations I used [Segment Anything Model (SAM)](https://github.com/facebookresearch/segment-anything) by Meta.

![](readme_assets/seg.png)

### 3. Training
I trained Mask R-CNN model using `detectron2` and YOLOv8 using Ultralytics' toolbox.

More information about models you can find in notebooks.

I used Google Colab for training, because it is free and has GPU.

### 4. Evaluation
I evaluated both models based on mAP, speed and size.

The mAP for object detection is the average of the AP calculated for all the classes. mAP@0.5 (or mAP50) means that it is the mAP calculated at IOU threshold 0.5.

| Model | mAP50 seg | Training Speed | Inference Speed | Model Size |
| --- | --- | --- | --- | --- |
| YOLOv8n | 0.715 | 7.2 minutes for 52 epochs | 8.3 ms | 30 MB |
| Mask RCNN (R_50_FPN_3x) | 0.633 | 11.5 mins for 1800 iters | 87.4 ms | 335 MB |

## Conclusion
I think, that YOLOv8 is better for segmentation, because it has better mAP and inference speed. That is because YOLOv8 is SOTA model for now, and Mask RCNN is too old.
