# Medical-Image-Classification-Using-GCP-Auto-ML



# Google Cloud AutoML Vision for Medical Image Classification

## Pneumonia Detection using Chest X-Ray Images

| | |
|-|-|
|__Title__| Google Cloud AutoML Vision for Medical Image Classification 
|__Author__ | __Ekaba Bisong__ <br>Google Developer Expert in Machine Learning<br> Google Certified Professional Data Engineer
|__Website__ | <a href="https://ekababisong.org/automl-medical-classification/">https://ekababisong.org/automl-medical-classification/</a>

Google Cloud AutoML Vision simplifies the creation of custom vision models for image recognition use-cases. The concepts of neural architecture search and transfer learning are used under the hood to find the best network architecture and the optimal hyperparameter configuration that minimizes the loss function of the model. This project uses Google Cloud AutoML Vision to develop an end-to-end medical image classification model for Pneumonia Detection using Chest X-Ray Images.

## About the Dataset
The dataset contains:
- 5,232 chest X-ray images from children.
- 3,883 of those images are samples of bacterial (2,538) and viral (1,345) pneumonia.
- 1,349 samples are healthy lung X-ray images.

The dataset is hosted on Kaggle and can be accessed at <a href="https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia">Chest X-Ray Images (Pneumonia).</a>

## Sample Images
<img src="chest-x-ray-samples.jpg" alt="examples-of-chest-X-Rays-in-patients-with-pneumonia">
The normal chest X-ray (left panel) shows clear lungs without any areas of abnormal opacification in the image. Bacterial pneumonia (middle) typically exhibits a focal lobar consolidation, in this case in the right upper lobe (white arrows), whereas viral pneumonia (right) manifests with a more diffuse "interstitial" pattern in both lungs. (Source: Kermany, D. S., Goldbaum M., et al. 2018. Identifying Medical Diagnoses and Treatable Diseases by Image-Based Deep Learning. Cell. https://www.cell.com/cell/fulltext/S0092-8674(18)30154-5)



# Reference Links
For Step by Step solution.
--https://towardsdatascience.com/google-cloud-automl-vision-for-medical-image-classification-76dfbf12a77e

DataSet Repository
--https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia

How to move from KaggleToGoogleCloudStorage
--https://github.com/gitrekm/KaggleToGoogcleCloudStorage


# Part 1: Enable AutoML Cloud Vision on GCP
(1). Go to the cloud console: https://cloud.google.com/

--Open Cloud AutoML Vision by clicking the triple-dash at the top-left corner of the GCP dashboard. Select Vision under the product section for Artificial Intelligence.
--Select Image Classification under AutoML Vision.
--Image Classification under AutoML Vision
--Setup Project APIs, permissions and Cloud Storage bucket to store the image files for modeling and other assets.
--Setup Project APIs and Permissions
--Select your GCP billing project from the drop-down when asked. Now we are ready to create a Dataset for building the custom classification model on AutoML. We will return here after downloading the raw dataset from Kaggle to Cloud Storage and preparing the data for modeling with AutoML.

# Part 2: Download the Dataset to Google Cloud Storage

-- Download Kaggle API token key that will enable the Kaggle CLI to authenticate/ authorize against Kaggle to download the desired datasets.
Login to your Kaggle account.
--Go to: https://www.kaggle.com/[KAGGLE_USER_NAME]/account
--Click on: Create New API Token.
--Download the token to your local machine and upload it to the cloud shell.
--Move the uploaded .json key to the directory .kaggle . Use the code below:
  ## mv kaggle.json .kaggle/kaggle.json
--Download dataset from Kaggle to Google Cloud Storage.
--kaggle datasets download ### paultimothymooney/chest-xray-pneumonia
--Move the dataset from the ephemeral cloud shell instance to the created cloud storage bucket. Insert your bucket name here.
 ## gsutil -m cp -r chest_xray gs://optimum-vine-297907/chest_xray/
 
# Part 3: Preparing the Dataset for Modeling
-- Check the Preprocessing in above file.
-- Clone the preprocessing script from Github. Click on the icon, circled in red and labeled (1) and enter the Github URL https://github.com/dvdbisong/automl-medical-image-classification to clone the repo with the preprocessing code.
-- Run all the cells in the notebook preprocessing.ipynb to create the CSV file containing the path and labels of the images and upload this file to Cloud Storage. Be sure to change the parameter for the bucket_name.

# Part 4: Modeling with Cloud AutoML Vision

-- Click on “New Dataset” from the AutoML Vision Dashboard.
--Fill-in the dataset name and select the CSV file from the Cloud Storage bucket created by AutoML.
--For now, you may dismiss if you see the error message that duplicated files are located. To the best of my knowledge, this is not the case as per the file names.
--Click on Train as shown in red in the image above to initiate model building with Cloud AutoML.
--Select how the model will be hosted, and the training budget.
--After model training is complete, click on Evaluate to view the performance metric of the model.
--Assess the performance metric (precision, recall and confusion matrix).

