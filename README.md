# Distracted driver detection

The purpose of this project was to get myself more familiar with the following packages: 

- fast ai
- neptune
- captum
- shap

[image1]: https://github.com/cpow-89/distracted_driver_detection_with_neptune/blob/master/doc_images/overview.png "Overview image"
![Overview image][image1]

I used the [fast ai](https://www.fast.ai/) package to train a model on the [state-farm-distracted-driver-detection](https://www.kaggle.com/c/state-farm-distracted-driver-detection) dataset.
I achieved an accuracy of 0.933047 on the full dataset and an accuracy of 0.970033 on the dataset without category "C9 - talking to passenger".
I tracked all my experiments with the [neptune package](https://neptune.ml/) package and analysed my models with the help of fast ai interpreter module, the [shap package](https://github.com/slundberg/shap) and [captum package](https://github.com/pytorch/captum).

If you are interested in how I did that feel free to follow along.


## Requirements:

- download the [state-farm-distracted-driver-detection](https://www.kaggle.com/c/state-farm-distracted-driver-detection) dataset
- create an account for neptune.ml -> https://docs.neptune.ml/python-api/tutorials/get-started.html
- install all packages conda env create -f driver_env.yml


## Pretrained models:

[Full Neptune Experiment History](https://ui.neptune.ml/cpow-89/distracted-driver-detection/experiments?viewId=standard-view&sortBy=%5B%22accuracy%22%5D&sortDirection=%5B%22descending%22%5D&sortFieldType=%5B%22numericChannel%22%5D&trashed=false&lbViewUnpacked=true) 


## How to

If you want to follow my journey, then this part will give you all the information you need.

##### Step 1: Init Project
Start by cloning this repo folder. Then extract the [state-farm-distracted-driver-detection](https://www.kaggle.com/c/state-farm-distracted-driver-detection) dataset inside this folder.

##### Step 2: Prepare dataset
Open the [Prepare dataset](https://github.com/cpow-89/distracted_driver_detection_with_neptune/blob/master/Prepare%20dataset.ipynb) notebook and follow along the instructions.

Note: This will create a new folder inside your project folder called "dataset". The new folder will include a rearranged copy of the [state-farm-distracted-driver-detection](https://www.kaggle.com/c/state-farm-distracted-driver-detection) dataset, well suited for training.

##### Step 3 Train your own model
If you want to train your own models on the rearranged [state-farm-distracted-driver-detection](https://www.kaggle.com/c/state-farm-distracted-driver-detection) dataset, you can do so by following the [Train Resnet Model For Distracted Driver Detection](https://github.com/cpow-89/distracted_driver_detection_with_neptune/blob/master/Train%20Resnet%20Model%20For%20Distracted%20Driver%20Detection.ipynb) notebook. The notebook allows you to run one training loop. It uses neptune.ml to log all information from the current run. 

If you don't want to train your own model you can also download my pre-trained weights by following this link:

https://ui.neptune.ml/cpow-89/distracted-driver-detection/experiments?viewId=standard-view&sortBy=%5B%22accuracy%22%5D&sortDirection=%5B%22descending%22%5D&sortFieldType=%5B%22numericChannel%22%5D&trashed=false&lbViewUnpacked=true 

Click on DDD-28 for the model trained on the full dataset or DDD-36 for the dataset trained on the dataset without c9.
The weights can be downloaded under Artifacts.

##### Step 4 Model evaluation using fast ai tools
If you want to get some useful statistics about your model, you can use the [Evaluate Resnet Model For Distracted Driver Detection](https://github.com/cpow-89/distracted_driver_detection_with_neptune/blob/master/Evaluate%20Resnet%20Model%20For%20Distracted%20Driver%20Detection.ipynb) notebook. This notebook generates the confusion matrix for your model and gives you some hints on how to improve your model. For example, I found that my model from experiment DDD-28 had the most problems with the C9 category. I investigated this further, and these images are tough to distinguish from the other images. So I decided to exclude this category which led to an improvement of about 4 %.

##### Step 5 Delete c9 (optional) 
If you want also want to remove c9 from your dataset, you can do so by running the [Delete C9 from Dataset](https://github.com/cpow-89/distracted_driver_detection_with_neptune/blob/master/Delete%20C9%20from%20Dataset.ipynb) notebook. This will create a new copy of the dataset in a folder called clean_dataset which does no longer include files from the c9 class.

##### Step 6 Train on dataset without c9 (optional) 
If you want to train a new model on the clean_dataset use the [Train Resnet Model For Distracted Driver Detection](https://github.com/cpow-89/distracted_driver_detection_with_neptune/blob/master/Train%20Resnet%20Model%20For%20Distracted%20Driver%20Detection.ipynb) notebook again.

##### Step 7 Investigate your model
If you want to investigate your model further with the help of the [shap package](https://github.com/slundberg/shap) and [captum package](https://github.com/pytorch/captum) you can do so by using the [Inspect Best Model](https://github.com/cpow-89/distracted_driver_detection_with_neptune/blob/master/Inspect%20Best%20Model.ipynb) notebook.
