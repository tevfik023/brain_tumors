
You can use the YOLOv11 model (colab) in your work !


YOLOv11 segmentation re-implementation using PyTorch

### Installation

```
conda create -n YOLO python=3.10.10
conda activate YOLO
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
pip install opencv-python
pip install PyYAML
pip install tqdm
```



### Train

* Configure your dataset path in `main.py` for training
* Run `bash main.sh $ --train` for training, `$` is number of GPUs

### Test

* Configure your dataset path in `main.py` for testing
* Run `python main.py --test` for testing



#### Reference

* https://github.com/ultralytics/ultralytics


## CITATION

Dear Author

If you want to use the brain dataset and YOLOv11 model of the study on this github page in your own study, you need to provide some information to the following e-mail addresses.

1. Purpose of your study
2. Text stating that you have met the citation requirements in your study

mail:
mtagdas@munzur.edu.tr
ademkorkmaz@bandirma.edu.tr
