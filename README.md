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


## How to

If you want to follow my journey, then this part will give you all the information you need.

##### Step 1: Init Project
- clone the repo folder
- extract the [state-farm-distracted-driver-detection](https://www.kaggle.com/c/state-farm-distracted-driver-detection) dataset inside this folder

##### Step 2: Prepare dataset
- open the [Prepare dataset](https://github.com/cpow-89/distracted_driver_detection_with_neptune/blob/master/Prepare%20dataset.ipynb) notebook and follow along the instructions

Note: This will create a new folder inside your project folder called "dataset". The new folder will include a rearranged copy of the [state-farm-distracted-driver-detection](https://www.kaggle.com/c/state-farm-distracted-driver-detection) dataset, well suited for training.
