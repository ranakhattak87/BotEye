
InHAR Dataset Preprocessing Tutorial in Colab
This tutorial guides you through preprocessing the INHARD dataset in Google Colab. The process involves downloading the dataset from a public repository, storing it on your Google Drive, extracting dataframes (if available), and saving action frames per target class as separate folders.

Prerequisites:

A Google account and access to Google Colab (https://colab.research.google.com)
Basic understanding of Python
Steps:

1. Mount Google Drive:

In the first code cell of your Colab notebook, run the following code to mount your Google Drive:
Python
from google.colab import drive
drive.mount('/content/drive')
Use code with caution.

Follow the on-screen instructions to authenticate your Google account. This allows you to access and manage files on your Google Drive from Colab.
2. Create Dataset Directory (Optional):

Uncomment the following lines to create a directory named datasets within your Google Drive to store the downloaded dataset:
Python
# Create a directory to store the dataset
dataset_dir = '/content/drive/My Drive/datasets'
os.makedirs(dataset_dir, exist_ok=True)
Use code with caution.

This step is optional, and you can adjust the dataset_dir path to an existing directory if preferred.
3. Change Directory:

Use the following code to change the working directory to the dataset directory you created (or your preferred location):
Python
# Change the current directory to the dataset directory
os.chdir(dataset_dir)
Use code with caution.

4. Install Required Libraries:

Run the following code cell to install the libraries needed for data manipulation, video processing, and file system interactions:
Python
import pandas as pd
import os
import cv2
import numpy as np
Use code with caution.

5. Download the INHARD Dataset (Choose a Method):

!wget https://zenodo.org/records/4003541/files/01-InHARD.7z.001?download=1

6. Extract the Dataset :

!7za x 01-InHARD.7z.001

7. Define Paths:

Set the following variables to specify the locations of the INHARD dataset and the output directory for storing extracted frames:
Python
# Define paths
dataset_path = '/content/drive/My Drive/datasets/Segmented/RGBSegmented'  # Update with your actual dataset path
output_path = '/content/drive/My Drive/FramesperLabel/'                 # Update with your desired output path


Replace dataset_path with the actual path to your unzipped INHARD dataset directory (containing video folders).
Replace output_path with the desired location on your Google Drive where you want to save the extracted action frames per class.
8. Frame Extraction Function:

The provided code defines a function named extract_frames that extracts frames from videos and saves them with the label name. This function assumes the label information is embedded in the video filenames (before the extension).
9. Preprocess Dataset:

The code iterates through the class folders within the dataset path (dataset_path) and calls the extract_frames function for each video file. This extracts frames and saves them in separate folders within the specified output_path, using the class label as the folder name.
10. Run the Preprocessing Script:

Once you've replaced the placeholders (<URL>, dataset_path, and output_path) with your specific details, run all the code cells in your Colab notebook.
