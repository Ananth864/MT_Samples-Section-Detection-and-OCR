# MT_Samples-Section-Detection

### Objective 

Perform object detection on the MT samples to identify different sections and extract text from specific sections using OCR.

### Dataset

This dataset contains sample medical transcriptions for various medical specialties.
https://www.kaggle.com/datasets/tboyle10/medicaltranscriptions

### MT Sample with added noise to simulate scanned document
<img src="https://user-images.githubusercontent.com/85446106/197342932-0c10485d-0b80-4af0-9eea-6eaa239ea453.PNG" width="450" height="600">

## Aproach

### Dataset Annotations

First we need to manually annotate the dataset in order to train our model. Hence PDF miner and PDF plumber was used to extract coordinates of all the test. Using patterns in the document, you can automate the process of getting bounding boxes around each section of the document and save it in the COCO format. Then we convert it to the YOLO format which the model can understand. Lines which were part of the same section were merged to form the bounding box of the section as shown below.

<img src="https://user-images.githubusercontent.com/85446106/197360641-b16e6998-02d0-4a56-8424-6e3a278ea7f7.PNG" width="400" height="525"> <img src="https://user-images.githubusercontent.com/85446106/197360953-20f618dc-477f-4b30-aa09-3cd46addcd11.PNG" width="400" height="525">

### Object detection model

Yolov5m model by ultralytics was used to predict bouding boxes of sections
https://github.com/ultralytics/yolov5

Yolov5m is the best combination of inference time and mAP. Hence, this model was used for the prediction over models like faster RCNN and other variants of Yolov5.The Yolov5m trained model was then run on an ONNX runtime to improve the inference time.

Now OCR needed to be performed on the predicted sections 

hyperparameters: lr0=0.01, lrf=0.01, momentum=0.937, weight_decay=0.0005, warmup_epochs=3.0, warmup_momentum=0.8, warmup_bias_lr=0.1, box=0.05, cls=0.5, cls_pw=1.0, obj=1.0, obj_pw=1.0, iou_t=0.2, anchor_t=4.0, fl_gamma=0.0, hsv_h=0.015, hsv_s=0.7, hsv_v=0.4, degrees=0.0, translate=0.1, scale=0.5, shear=0.0, perspective=0.0, flipud=0.0, fliplr=0.5, mosaic=1.0, mixup=0.0, copy_paste=0.0

## Results
![Part_5_seventh](https://user-images.githubusercontent.com/85446106/197361365-62de2a7e-3bf0-46d8-8c84-bfef72837710.PNG)




