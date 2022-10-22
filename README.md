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

First we need to manually annotate the dataset in order to train our model. Hence PDF miner and PDF plumber was used to extract coordinates of all the test. Using patterns in the document, you can automate the process of getting bounding boxes around each section of the document and then convert to yolo format which the model can understand. Lines which were part of the same section were merged to form the bounding box of the section as shown below.

<img src="https://user-images.githubusercontent.com/85446106/197360641-b16e6998-02d0-4a56-8424-6e3a278ea7f7.PNG" width="450" height="600"> <img src="https://user-images.githubusercontent.com/85446106/197360953-20f618dc-477f-4b30-aa09-3cd46addcd11.PNG" width="450" height="600">

### Object detection model

Yolov5 model by ultralytics was used to predict bouding boxes of sections
https://github.com/ultralytics/yolov5

## Results
![Part_5_seventh](https://user-images.githubusercontent.com/85446106/197361365-62de2a7e-3bf0-46d8-8c84-bfef72837710.PNG)




