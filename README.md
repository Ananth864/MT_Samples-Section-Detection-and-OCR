# MT_Samples-Section-Detection

### Objective 

Perform object detection on the MT samples to identify different sections and extract text from specific sections using OCR.

### Dataset

This dataset contains sample medical transcriptions for various medical specialties.
https://www.kaggle.com/datasets/tboyle10/medicaltranscriptions

### MT Sample with added noise to simulate scanned document
![Part_4_first](https://user-images.githubusercontent.com/85446106/197342932-0c10485d-0b80-4af0-9eea-6eaa239ea453.PNG)

## Aproach

First we need to manually annotate the dataset in order to train our model. Hence PDF miner and PDF plumber was used to extract coordinates of all the test. Using patterns in the document, you can automate the process of getting bounding boxes around each section of the document and then convert to yolo format which the model can understand. Lines which were part of the same section were merged to form the bounding box of the section as shown below.

![Part_2_first](https://user-images.githubusercontent.com/85446106/197360641-b16e6998-02d0-4a56-8424-6e3a278ea7f7.PNG)

![Part_2_second](https://user-images.githubusercontent.com/85446106/197360647-8bc3a2a8-d79b-493d-96fa-7ea190ea1372.PNG)



