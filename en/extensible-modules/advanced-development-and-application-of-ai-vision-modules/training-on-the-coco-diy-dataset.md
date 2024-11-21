---
description: >-
  This section describes how to extract some of the labels and data from the
  COCO dataset for training using the scripting tool provided by Petoi.
---

# Training on the COCO DIY dataset

Below is a brief description of the COCO dataset:

```
COCO (Common Objects in Context) dataset is a widely used computer vision dataset for tasks such as object detection, segmentation, and keypoint detection. Developed by Microsoft Research, the goal of the COCO dataset is to provide a rich dataset with high-quality annotations to advance computer vision technology.

Key features of COCO dataset:
Data content:

Number of images: contains over 330,000 images.
Classes: Covering 80 object classes, e.g., people, cars, animals, furniture, etc.
Annotation: each image is annotated with objects, supporting tasks such as object detection, segmentation (instance segmentation) and key point detection (e.g., human pose estimation).
Data type:

Object detection: the bounding box (bounding box) of the object is labelled.
Instance segmentation: pixel-level segmentation mask (mask) for each object instance.
Key point detection: the position of the key points of the body is labelled.
Scene description: each image also contains textual information describing the content of the image.
Data Distribution:

Training set: contains about 118,000 images.
Validation set: contains about 5,000 images.
Test set: contains about 20,000 images (for competition and evaluation).
Data set structure:

Image data: Stored in the image folder.
Annotation data: stored in JSON format files, including information such as object bounding boxes, segmentation masks, keypoints, and so on.
Usage Scenario:
Object detection: identify objects in the image and determine their locations.
Example segmentation: segment each object in the image at pixel level.
Human body pose estimation: detects the position of key points of the human body in the image.
Scene understanding: analyses the image content and generates a description.
The COCO dataset is widely used in the field of computer vision because it provides a large and diverse set of annotated data that helps in training and evaluating different vision models.
```

The COCO dataset is approximately 20GB in size, with a large amount of data and many labels, enabling detection of up to 80 different labels. However, this comes with a trade-off in detection accuracy. To meet users' needs for balancing the number of recognized categories and recognition accuracy in different scenarios, Petoi has implemented a way to recreate the dataset with any number of labels from the COCO dataset.

## COCO Dataset Download

Copy the following code into a file named `coco_download.py`. Place the script in the parent directory of the target location for the COCO dataset.

```
import os
import requests
from zipfile import ZipFile
from tqdm import tqdm
import argparse

def download_url(url, dir):
    if not os.path.exists(dir):
        os.makedirs(dir)
    response = requests.get(url, stream=True)
    file_size = int(response.headers.get('content-length', 0))
    filename = os.path.join(dir, url.split('/')[-1])
    
    with open(filename, 'wb') as f, tqdm(
        desc=filename,
        total=file_size,
        unit='B',
        unit_scale=True,
        unit_divisor=1024,
    ) as bar:
        for chunk in response.iter_content(chunk_size=1024):
            if chunk:
                f.write(chunk)
                bar.update(len(chunk))

def extract_zip(file_path, extract_to):
    with ZipFile(file_path, 'r') as zip_ref:
        zip_ref.extractall(extract_to)

def main(dataset_path):
    images_path = os.path.join(dataset_path, 'images')
    labels_url = 'https://github.com/ultralytics/yolov5/releases/download/v1.0/coco2017labels.zip'
    data_urls = [
        'http://images.cocodataset.org/zips/train2017.zip',
        'http://images.cocodataset.org/zips/val2017.zip',
        'http://images.cocodataset.org/zips/test2017.zip'
    ]

    # Download and extract labels
    download_url(labels_url, dataset_path)
    extract_zip(os.path.join(dataset_path, 'coco2017labels.zip'), dataset_path)
    
    # Download and extract images
    if not os.path.exists(images_path):
        os.makedirs(images_path)

    for url in data_urls:
        zip_name = url.split('/')[-1]
        zip_path = os.path.join(images_path, zip_name)
        download_url(url, images_path)
        extract_zip(zip_path, images_path)
        os.remove(zip_path)  # Clean up zip file after extraction

if __name__ == '__main__':
    parser = argparse.ArgumentParser(description='Download and extract COCO dataset.')

    main(".")
```

Execute:&#x20;

_**`python .\coco_download.py`**_

If you find that there is no way to download the full COCO dataset due to unstable network or other reasons during the download process, then please download the COCO dataset manually and unzip the zip archive to the appropriate location.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption><p>Enter the url directly into the browser to download the zip file</p></figcaption></figure>

The final dataset format is guaranteed to be:

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

The COCO DIY dataset is extracted using the following script, which can be named coco\_remake.py&#x20;

Before running the script, please change `src_coco_path` to the path of COCO2017 and `dst_coco_path` to the path of DIY\_COCO dataset. Change `src_yaml_file` to the path of the official COCO2017 YAML file and `dst_yaml_file` to the path of the YAML file for DIY\_COCO.&#x20;

```
import os
import shutil
import yaml

src_coco_path = "E:\Project\yolov5\datasets\coco"
dst_coco_path = "E:\Project\yolov8_coco_simple\coco_04"
src_yaml_file ="E:\Project\yolov5\data\coco.yaml"
dst_yaml_file ="E:\Project\yolov8_coco_simple\coco_03_02_03.yaml"


def get_key_from_value(dictionary, value):
    for key, val in dictionary.items():
        if(val-int(value))==0:
            return key
           

def get_value_from_key(dictionary, key_item):
    for key, val in dictionary.items():
        if key == key_item:
            return val
    return None  # 如果没有找到匹配的值

def load_coco_labels(yaml_file):
    """
    Load COCO labels from a YAML file.
    :param yaml_file: Path to the YAML file
    :return: Dictionary mapping class names to their indices
    """
    with open(yaml_file, 'r', encoding='utf-8') as file:
        data = yaml.safe_load(file)
    return {v: k for k, v in data['names'].items()}

def get_class_indices(classes, labels_mapping):
    """
    Get indices for specific class names based on the labels mapping.
    :param classes: Set of class names to find indices for
    :param labels_mapping: Dictionary mapping class names to their indices
    :return: List of indices corresponding to the class names
    """
    return [labels_mapping[cls] for cls in classes if cls in labels_mapping]

def load_value_mapping(yaml_file):
    """
    从 YAML 文件中加载标签映射
    :param yaml_file: YAML 文件路径
    :return: 标签 ID 集合
    """
    with open(yaml_file, 'r') as file:
        data = yaml.safe_load(file)
    # 提取标签 ID
    labels = set(data['names'].values())
    return labels

def modify_list(lst):
    #print(lst)
    if not lst:
        return lst  # 如果列表为空，直接返回空列表
    
    first_element = lst[0]  # 提取第一个元素
    #print(first_element)
    dst_first_element_label = get_key_from_value(src_labels_values,first_element)
    #print(dst_first_element_label)
    dst_first_element       = get_value_from_key(dst_labels_values,dst_first_element_label)
    #print(dst_first_element)
    remaining_elements = lst[1:]  # 剩下的元素
    modified_list = []
    #print(">>>>>>>>>>")
    #print(len(remaining_elements))

    for i in range(0, (len(remaining_elements)//4)*4, 4):

        #print(remaining_elements[i])
        modified_list.append(dst_first_element)  # 添加第一个元素
        modified_list.append(' ')
        modified_list.append(remaining_elements[i])
        modified_list.append(' ') 
        modified_list.append(remaining_elements[i+1])  
        modified_list.append(' ')
        modified_list.append(remaining_elements[i+2])  
        modified_list.append(' ')
        modified_list.append(remaining_elements[i+3]) 
        modified_list.append('\n')  # 添加换行符
    
    return modified_list


if __name__ == '__main__':
    values = load_value_mapping(dst_yaml_file)
    #print(values)
    src_labels_values = load_coco_labels(src_yaml_file)
    #print(src_labels_values)
    dst_labels_values = load_coco_labels(dst_yaml_file)
    #print(dst_labels_values)

    gt_labels = get_class_indices(values,src_labels_values)

    #print(gt_labels)
    src_images_dir = os.path.join(src_coco_path, "images")
    src_labels_dir = os.path.join(src_coco_path, "labels")
    src_images_train_dir = os.path.join(src_images_dir, "train2017")
    src_images_val_dir = os.path.join(src_images_dir, "val2017")
    src_labels_train_dir = os.path.join(src_labels_dir, "train2017")
    src_labels_val_dir = os.path.join(src_labels_dir, "val2017")

    dst_images_dir = os.path.join(dst_coco_path, "images")
    dst_labels_dir = os.path.join(dst_coco_path, "labels")
    dst_images_train_dir = os.path.join(dst_images_dir, "train")
    dst_images_val_dir = os.path.join(dst_images_dir, "val")
    dst_labels_train_dir = os.path.join(dst_labels_dir, "train")
    dst_labels_val_dir = os.path.join(dst_labels_dir, "val")
    
    os.makedirs(dst_images_train_dir, exist_ok=True)
    os.makedirs(dst_images_val_dir, exist_ok=True)
    os.makedirs(dst_labels_train_dir, exist_ok=True)
    os.makedirs(dst_labels_val_dir, exist_ok=True)


    #print(src_labels_train_dir)
    for txt_file in os.listdir(src_labels_train_dir):
        if txt_file.endswith(".txt"):
            src_labels_train_file_path = os.path.join(src_labels_train_dir, txt_file)
            src_images_train_file_path = os.path.join(src_images_train_dir, txt_file.replace(".txt", ".jpg"))
            with open(src_labels_train_file_path, 'r') as f:
                    print(src_labels_train_file_path)
                    lines = f.readlines()
                    temp_lines=[]
                    temp_line=[]
                    for line in lines:
                        label_id = int(line.strip().split()[0])
                        if label_id in gt_labels:
                            temp_line=modify_list(line.strip().split())
                            temp_lines+=temp_line
                    #print(temp_lines)

                    if temp_lines:
                        print(temp_lines)
                        dst_labels_train_file_path = os.path.join(dst_labels_train_dir, txt_file)
                        dst_images_train_file_path = os.path.join(dst_images_train_dir, txt_file.replace(".txt", ".jpg"))
                        with open(dst_labels_train_file_path, 'w') as f_2:
                            for item in temp_lines:
                                f_2.write(f"{item}")
                        shutil.copy(src_images_train_file_path, dst_images_train_file_path)
        
    #print(src_labels_val_dir)
    for txt_file in os.listdir(src_labels_val_dir):
        if txt_file.endswith(".txt"):
            src_labels_val_file_path = os.path.join(src_labels_val_dir, txt_file)
            src_images_val_file_path = os.path.join(src_images_val_dir, txt_file.replace(".txt", ".jpg"))
            with open(src_labels_val_file_path, 'r') as f:
                    print(src_labels_val_file_path)
                    lines = f.readlines()
                    temp_lines=[]
                    temp_line=[]
                    for line in lines:
                        label_id = int(line.strip().split()[0])
                        if label_id in gt_labels:
                            temp_line=modify_list(line.strip().split())
                            temp_lines+=temp_line
                    #print(temp_lines)

                    if temp_lines:
                        print(temp_lines)
                        dst_labels_val_file_path = os.path.join(dst_labels_val_dir, txt_file)
                        dst_images_val_file_path = os.path.join(dst_images_val_dir, txt_file.replace(".txt", ".jpg"))
                        with open(dst_labels_val_file_path, 'w') as f_2:
                            for item in temp_lines:
                                f_2.write(f"{item}")
                        shutil.copy(src_images_val_file_path, dst_images_val_file_path)

```

You can write the YAML file for DIY\_COCO in the following style, where the labels need to be selected from the labels that already exist in the COCO dataset. But the order of the labels does not have to be the same as in the COCO dataset, they just need to be counted from 0.

```
train: E:\Project\yolov8_coco_simple\coco_04\images\train
val: E:\Project\yolov8_coco_simple\coco_04\images\val

# Classes
names:
  0: bicycle
```

This YAML file includes the paths to the train and val directories as well as the label order and corresponding labels. For local training, use absolute paths. For cloud training, this YAML file needs to be modified to the following format:

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

And, when training in the cloud, be sure to follow this organisation of the dataset below:

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

Combined with the steps in the Model Training section, you can train your own model based on the COCO DIY dataset!

If your dataset was downloaded manually, you will also need to download _**`COCO.yaml`**_ manually.The download link is below:

{% @github-files/github-code-block url="https://github.com/ultralytics/ultralytics/blob/main/ultralytics/cfg/datasets/coco.yaml" %}

