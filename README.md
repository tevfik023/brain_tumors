
You can use the YOLOv11 model (colab) in your work !


We have prepared special yolov11 segmentation model file for Brain Tumor segmentation.

YOLOv11 segmentation re-implementation using PyTorch

### Installation
NOTE: To make it easier for us to manage datasets, images and models we create a HOME constant.
```
import os
HOME = os.getcwd()
print(HOME)
```
Install YOLO11 via Ultralytics
```
%pip install ultralytics supervision roboflow
```
Validate a model's accuracy on the COCO dataset's val or test splits. The latest YOLO11 models are downloaded automatically the first time they are used. See YOLO11 Val Docs for more information.

```
# Download COCO val
import torch
torch.hub.download_url_to_file('https://ultralytics.com/assets/coco2017val.zip', 'tmp.zip')  # download (780M - 5000 images)
!unzip -q tmp.zip -d datasets && rm tmp.zip  # unzip
```
# Validate YOLO11n on COCO8 val
```
!yolo val model=yolo11n.pt data=coco8.yaml
```
#Data
```
!mkdir {HOME}/datasets
%cd {HOME}/datasets

project = rf.workspace("***").project("brain-segment")
version = project.version(*)
dataset = version.download("yolov11")
```

### Train

* Configure your dataset path in `main.py` for training
* Run `bash main.sh $ --train` for training, `$` is number of GPUs

### Test

* Configure your dataset path in `main.py` for testing
* Run `python main.py --test` for testing

Custom Training
![image](https://github.com/user-attachments/assets/3bdd9425-7da7-4dca-a71b-8080d466ba62)

```
%cd {HOME}

!yolo task=detect mode=train model=yolo11s-seg.pt data={dataset.location}/data.yaml epochs=10 imgsz=640 plots=True
```
Confusion Matrix
```
from IPython.display import Image as IPyImage

IPyImage(filename=f'{HOME}/runs/segment/train/confusion_matrix.png', width=600)
```
Result Graph
```
IPyImage(filename=f'{HOME}/runs/segment/train/results.png', width=600)

```
![image](https://github.com/user-attachments/assets/faa74684-c955-4d38-89a8-569842c82353)

### Image Testing
```
IPyImage(filename=f'{HOME}/runs/segment/train/val_batch0_pred.jpg', width=600)

```

![image](https://github.com/user-attachments/assets/1c187fcb-0a57-407a-9b04-c8ed04dd132c)


#### Reference

* https://github.com/ultralytics/ultralytics

##Download YOLOv11 Segmentation Colab Files
##Download Brain Tumors Data Files

## CITATION

Dear Author

If you want to use the brain dataset and YOLOv11 model of the study on this github page in your own study, you need to provide some information to the following e-mail addresses.

1. Purpose of your study
2. Text stating that you have met the citation requirements in your study

mail:
mtagdas@munzur.edu.tr &
ademkorkmaz@bandirma.edu.tr
