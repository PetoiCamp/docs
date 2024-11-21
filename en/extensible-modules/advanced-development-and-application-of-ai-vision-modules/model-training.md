---
description: >-
  With deep learning networks can learn data features from large amounts of
  data, which can be applied to a variety of detection, segmentation tasks.
---

# Model Training

To use deep learning to solve specific problems, it is important to understand how to train a network model with known data. Therefore, we first explained how to train a deep-learning neural network. The content of this section is as follows:

* Model training locally&#x20;
* Model training in the cloud&#x20;
* Make your training datasets&#x20;



## Model training locally&#x20;

This subsection describes how to perform model training on a personal PC. You will need to have the following hardware:

A laptop or desktop computer with an NVIDIA graphics card and Windows installed (if your computer does not contain an NVIDIA graphics card, we recommend using the cloud for your model training).

Please install Anaconda software to manage your Python environment. There are three versions of Anaconda available for Windows, Max, and Linux; please choose the one that corresponds to your system.

{% embed url="https://www.anaconda.com/" %}

Install VScode as your code editing software.

{% embed url="https://code.visualstudio.com/Download" %}

Use anaconda to create the environment we will use to train our model:

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Open the Anaconda Prompt below

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Enter the following commands to enter the work command, activate the environment, and open vscode (note that you replace the working directory and environment names with your corresponding names).

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Enter the following command in Terminal:

```
pip install ultralytics
git clone https://github.com/ultralytics/ultralytics
cd ultralytics
pip install -e .
```

When you're done, type&#x20;

```
pip uninstall torch torchvision 
```

Uninstalling and installing the GPU-friendly version of Torch.

{% embed url="https://pytorch.org/" %}

Before installing, please check the Cuda driver installed on your card and install pytorch and torchvision corresponding to the Cuda version. e.g., my cuda version is higher than 12.1, so I install

```
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
```

At this point, you have completed all the environment configurations required for model training, and you can happily train the model below 😊. To train the model, you need to execute the following commands:

```
yolo train detect model=yolov8n.pt data=coco128.yaml imgsz=192 epochs=100
```

Where _<mark style="color:purple;">**model**</mark>_ is the path to the model you need to train, the current Grove Vision V2 only supports the deployment of yolov8n.pt, so please choose yolov8n.pt. data is the path to the training set needed for model training, here we use a very small dataset as a test, later in this section we will explain how to create the training set for training. In addition, we have implemented custom partial label training for the coco dataset, which allows you to select specific labels for training according to your preferences and uses, enabling more flexible inference. imgsz is the image size accepted as input to the model, which must be 192. epochs is the number of times the model has been trained. In general, the more times it has been trained, the better the model fits the data.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

At the end of the training, you can find your trained model at the location where the model is saved as shown on the command line (e.g. my model is saved at runs\detect\train3)

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

## Model training in the cloud&#x20;

Unfortunately, if you don't have a computer with an NVIDIA graphics card, you can't train the model locally. However, you can train it in the cloud, and both training methods will give you the same model results. We use ultralytics for cloud model training. Below is the link to the Ultralytics HUB. Open the link, and you will see an introduction and tutorial on how to use it.

{% embed url="https://docs.ultralytics.com/hub/" %}

You need a GitHub, Google, or Apple account to use the Ultralytics HUB.

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption><p>Ultralytics HUB home page</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Create a project</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption><p>Enter the project name and click ‘Create ’</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption><p>Click on ‘Train Model’</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption><p>Select the dataset you are interested in.</p></figcaption></figure>

The ultralytics hub supports the training of users' own datasets. See the subsequent section for how to make and upload a dataset.

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption><p>Select the model to be trained, if it is to be deployed in Grove Vision V2, we recommend yolov8n</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Set the Advanced Model Configuration. If you are using Google Colab for model training in the future, it is recommended to change the Epochs to 30 because although Google Colab is free, there is a time limit for using it, and 30 training is about 2 hours, which is just within the time limit. If we want to deploy the model on the Grove Vision V2 module, we also need to change the image size to 192, which is more in line with our actual application scenario. In addition, a Google mailbox is required to use Google Colab.

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption><p>Copy the code and open this link.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption><p>You will then be redirected to the following page, where you need to replace the ‘Start’ section with the code you just copied</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption><p>Click Setup, wait for the setup to complete, and then click start.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption><p>If the printout is similar to the screenshot I showed, the model is trained properly.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption><p>Model training can also be visualised in the Ultralytics HUB.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption><p>If google colab interrupts training, there is no need to worry as the data has been saved. Simply wait until google colab has remaining training resources and then resume training.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption><p>Once the model training is complete, you can select the model format you want to download.</p></figcaption></figure>

## Make your own training datasets

If you want to detect labels outside the open-source dataset, you need to make your own dataset. The dataset should include the images and the corresponding labels.&#x20;

The following is the dataset format specified by yolov8

{% embed url="https://docs.ultralytics.com/datasets/#how-can-i-optimize-and-zip-a-dataset-using-ultralytics-tools" %}

We use the Make Sense online data labeling tool to complete the training set production process:

{% embed url="https://www.makesense.ai/" %}

For information on how to use Make Sense, see:

{% embed url="https://xailient.com/blog/how-to-annotate-your-images-using-the-makesense-tool/" %}

After labeling the dataset labels, you need to merge the image and label data to form a complete dataset. The dataset needs to meet the following format:

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

You need to copy the label data generated by Make Sense to the appropriate location. For example, if you tagged the labeled data for training, the images required for training should be located in images/train and the labeled data should be located in labels/train. Additionally, you need to write a dataset.yaml file. This file needs to be placed in the dataset directory with the contents of the file: (! <mark style="color:red;">(Note: the dataset.yaml naming should match the folder naming. Otherwise, you will encounter problems when uploading the dataset to ultralytics)</mark>

```
train: images/train
val: images/val
test: images/test

names:
  0: class_one
  1: class_two
  2: class_three
  
```

Names need to correspond to the labels used for Make Sense annotation. If you are training locally, it is recommended that you change the paths of train, val, and test to absolute paths, which is not required for training in the cloud. At this point, you are ready to train your model with the made dataset; just change the path from ‘data=coco128.yaml’ to dataset.yaml in your made dataset.

```
yolo train detect model=yolov8n.pt data=coco128.yaml imgsz=192 epochs=100
```

If you are training in the cloud, you must upload your dataset to the ultralytics hub. The upload process is very simple:

<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

With your dataset in the Ultralytics HUB, you can now use your own dataset for model training.
