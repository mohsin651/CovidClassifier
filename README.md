# COVID-19-Classifier

## Introduction

COVID-19 is one of the most destructive pandemic humankind has ever faced. It has not only shaken the economy across the world but also made it an extremely difficult task for effective medical help to reach across remote regions. 
An extremely accurate and lightweight AI model could be a solution for this as it could aid the doctors and medical team especially in remote areas to detect COVID-19. 

Hence keeping this in mind, this project aims to create a **deep learning based COVID-19 CT-Scan images classifier**.

<p align = "center">
<img src = "https://user-images.githubusercontent.com/51092051/132006234-1d286018-f6d1-44e4-a5cd-a317f6385a41.png">
</p>

## Approach

All deep learning tasks have pipelines which look quite similar to the below one:

<p align = "center">
<img src = "https://user-images.githubusercontent.com/51092051/131998752-1f28bd1d-da6f-41a7-831e-e092992b73ed.png">
</p>

Therefore, I would be going step-by-step as per the pipeline on the approaches which I took to tackle this task.

## Dataset Creation and Pre-processing

The dataset curated for training was collected from [this github repo](https://github.com/ieee8023/covid-chestxray-dataset) 

The images took fall in 2 categories :
- Covid (25 images)
- Non_Covid(25 images)

As the size of the dataset was small, image augmentation techniques were used:
- Rotation upto 20 degrees on either side
- Horizontal Flip

The dataset finally gathered after augmentation was of 200 images - 100 images in each class.

The code for entire data pre-processing can be found in [this](https://github.com/AmanGoyal99/COVID-19-Classifier/blob/main/IISC_Covid_Task_Data.ipynb) notebook. 

## Model creation and training

The following 2 approaches were taken by me :

- Without transfer learning
  - Created a model with 6 layers of CNN and Max Pooling 2D
  - Keras-Tensorflow frameworks were used
  - Notebook link to this approach can be found [here](https://github.com/AmanGoyal99/COVID-19-Classifier/blob/main/IISC_covid_task_keras_tf.ipynb).

- With transfer learning
  - Used MobileNet model trained multiple times with freezed and un-freezed layers 
  - Pytorch-Fastai framework was utilized
  - Notebook link to this approach can be found [here](https://github.com/AmanGoyal99/COVID-19-Classifier/blob/main/IISC_covid_task_Transfer_Learning.ipynb).

## Inferencing model and evaluation

This is the final step of almost all the pipelines and quite imperative as the model we trained is evaluated and tested here.

Following were the results of the two approaches which I had taken:

- Without transfer learning 
  - Even though after getting an accuracy close to 100%, the model did not perform well on test images. Following are it's test predictions.

![image3](https://user-images.githubusercontent.com/51092051/132005007-fff0b950-95a7-471f-91da-7644da141483.png) ![image1](https://user-images.githubusercontent.com/51092051/132005016-e2a84ac8-23fd-4776-8db7-f4bb3141f59f.png)

  - The left image has been detected correctly as covid infected. However, the right image is not covid infected and yet has been predicted as covid infecte.
  - This is probably due to the shallow model used as features differ by very minor variations which would be captured by the network only if it is deep enough.

- With transfer learning
 - As expected, the results here not only just showed 100% accuracy but also labelled all the images correctly in the testing set. Following is it's confusion matrix:

<p align = "center">
<img src = "https://user-images.githubusercontent.com/51092051/132005486-d3ed44a6-7bd9-47ef-864e-7a24769e6fce.png">
</p>

  - This can clearly be illustrated as well when the model is inferred over test images. It is able to correctly classify both categories of images as shown below:

<p align = "center">
<img src = "https://user-images.githubusercontent.com/51092051/132005779-c39db37f-c71f-4694-84aa-482d6d0f916e.png">
</p>

## Conclusion

Therefore as per the results stated above, a successful approach is heavily dependent on the dataset and given the dataset which was used here, transfer learning approach is definitely well suited-one.
The best part about the approach used is that it provides close to perfect accuracy as well as is lightweight and easy to deploy.
