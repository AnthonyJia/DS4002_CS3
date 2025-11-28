# Who's the Imposter: AI Face Image Detection

This repository provides access to the data, scripts, reference materials, and step-by-step instructions for completing this case study.

## CS3 - Hook_Document

This document provides some context and establishes the motivation for this case study.  
***You should read this document before completing the case study.***

## Scripts

This folder contains the scripts needed to complete the case study.

## Supplemental_Materials

This folder contains some reference materials that you may find helpful for you to understand, as well as complete the case study.

## Data

The raw data for this case study is too large to be included in its entirety in this repository. Therefore, links to the Google Drive that contain each dataset will be included. There are two datasets for this case study: FFHQ dataset and StyleGAN dataset. The FFHQ dataset contains the real face images, while the StyleGAN dataset contains AI-generated face images. 

- [FFHQ dataset](https://drive.google.com/drive/folders/1tZUcXDBeOibC6jcMCtgRRz67pzrAHeHL)
- [StyleGAN dataset](https://drive.google.com/open?id=14lm8VRN1pr4g_KVe6_LvyDX1PObst6d4)

## Steps for Reproduction

### Step 0: Add Google Drive Shortcuts to datasets

For the [FFHQ dataset](https://drive.google.com/drive/folders/1tZUcXDBeOibC6jcMCtgRRz67pzrAHeHL), add shortcuts to folders (00000 - 09000) to your google drive. The `Download_data_and_eda.ipynb` script expects the shortcuts to be in  Mydrive/ai_classification_dataset/ffhq/ folder on your google drive.

To add a shortcut, simply click the three vertical dots on the right side of the folder/file --> Organize --> Add shortcut.

Your folder structure should look something like this:
```
MyDrive/
└── ai_classification_dataset/
    └── ffhq/
        ├── 00000 (shortcut)
        ├── 01000 (shortcut)
        ├── ...
        └── 09000 (shortcut)
```

For the [StyleGAN dataset](https://drive.google.com/open?id=14lm8VRN1pr4g_KVe6_LvyDX1PObst6d4), go into the `psi-0.7` folder, add shortcuts to the **zipped** folders (000000 - 009000) to your google drive. The `download_data_and_eda.ipynb` script expects the shortcuts to be in  Mydrive/ai_classification_dataset/stylegan/ folder on your google drive. 

Your folder structure should look something like this:
```
MyDrive/
└── ai_classification_dataset/
    └── stylegan/
        ├── 000000.zip (shortcut)
        ├── 001000.zip (shortcut)
        ├── ...
        └── 009000.zip (shortcut)
```

### Step 1: Download the data into the Google Colab environment and perform exploratory data analysis

Open the `Download_data_and_eda.ipynb` script in Google Colab environment and run it. 

This script does the following:
- Downloads the image data from NVIDIA's NVlabs research team's google drive via the shortcuts you made on your google drive
- Counts the number of real images (ffhq) and fake images (stylegan)
- Displays a sample of real images (ffhq) and fake images (stylegan)
- Performs EDA (color distribution, brightness, texture/level of detail)
- Zips the datasets on the virtual Google Colab environment and downloads them on your local computer (This is required for Step 2)

### Step 2: Model Training, Testing, and Evaluation

Open the `model-training-testing.ipynb` script in Kaggle Notebook environment. 

*Sidenote: You will need to create a Kaggle account to use the Kaggle Notebook environment (it's free)*

The reason why we use the Kaggle Notebook environment to run the second script is because Kaggle provides free GPUs, which speeds up the process of training deep neural networks such as convolutional neural networks. 

Before you can run the script, you have to upload the datasets you zipped in step 1 to the Kaggle Notebook environment. Simply open the right side menu of the notebook. Under the input section, click Upload --> New Dataset --> upload real_images.zip, fake_images.zip. For the dataset title, name it `human-faces`. This will take a while, since we are uploading 20k images to the environment. 

After the datasets are done uploading, you can run the script. 

This script does the following: 
- Counts the number of real images (ffhq) and fake images (stylegan)
- Preprocesses the image data for the chosen CNN model (Resnet18)
- Trains the model
- Tests the model
- Display evaluation metrics (Accuracy, Precision, Recall, F1-score) and confusion matrix
- Creates t-SNE embedding chart to visualize whether there are clear clusters forming between the real images and fake images
- Creates heatmaps on certain images to show which areas the model analyzed to classify whether an image is real or fake
