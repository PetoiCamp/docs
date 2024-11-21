---
description: Let the robot be your Avatar!
---

# OpenCat Imitation Tutorial

{% embed url="https://youtu.be/4oNJMGLDIT4" %}
Demo
{% endembed %}

In this tutorial, we will introduce how to use the **Ailia** in python language to implement an OpenCat robot to imitate various human body movements.&#x20;

To clone or download the code from the GitHub repository, you can clone the code with the following command:

```
git clone https://github.com/PetoiCamp/OpenCat-Imitation
```

## 1. Run on a regular computer (Mac/Linux)

{% hint style="info" %}
Requirements

* Python 3.6 and later
{% endhint %}

1. It is recommended to install the [Anaconda3](https://www.anaconda.com/products/distribution) IDE. For the specific installation method, please refer to the following link:\
   [https://docs.anaconda.com/anaconda/install/](https://docs.anaconda.com/anaconda/install/)\

2. Open the **Anaconda Prompt** (Windows) or the **Terminal** (Linux / macOS) and enter the following commands to create and activate a virtual environment (the environment name is "venv", and can also be customized to other names):\
   `conda create --name venv`\
   `conda activate venv`\

3. Follow [the guide](https://github.com/axinc-ai/ailia-models/blob/master/TUTORIAL.md) to install the **Ailia SDK**, it will be used for pose detection. The guide mainly includes the following steps: download and install the ailia SDK and the related python library files.\
   \
   When downloading the **Ailia SDK**, you need to enter the correct email address to receive the download link address and license file. The free license is valid for only one month. The SDK is about 2GB, so it takes time to download. \
   \
   Move the downloaded license file (**AILIA.lic**) to the directory where `bootstrap.py` is located (`{ailia sdk directory}/python`), and then follow the steps to continue installing the **Ailia SDK**.\
   `cd {ailia sdk directory}/python`\
   `python3 bootstrap.py` \
   `pip3 install .`\
   \
   Download the [**requirements.txt**](https://raw.githubusercontent.com/axinc-ai/ailia-models/master/requirements.txt) from this page ([https://github.com/axinc-ai/ailia-models](https://github.com/axinc-ai/ailia-models)) to the directory where `bootstrap.py` is located before running the following command:\
   `pip install -r requirements.txt.`  It may take 30 minutes.
4. Use the USB uploader or Bluetooth module to connect the robot and power it on. The computer needs to be connected to a camera device.&#x20;
5. Run the following command to start the OpenCat Imitation program:

<pre><code><strong>cd {your file directory}/OpenCat-Imitation/
</strong># set python import path
export PYTHONPATH=$PWD:$PWD/serialMaster
python opencat_imitation/imitation.py -v0
</code></pre>

{% hint style="info" %}
You can execute **run.sh** within **OpenCat-Imitation/** with your shell command directly. It wraps up the above commands.&#x20;
{% endhint %}

## 2. Run on the Jetson Nano 2GB Developer kit

You may want to run the demo on a Jetson Nano to experiment with some GPU features. &#x20;

The developer kit uses a microSD card as a boot device and for main storage. It’s important to have a card that’s fast and large enough for your projects; the minimum requirement is a 32GB UHS-1 card. Many projects with Jetson Nano 2GB Developer Kit will utilize swap space on the MicroSD Card due to only 2GB physical memory. For this reason, we recommend 64GB or larger microSD cards. High-endurance microSD cards are also recommended.

1. &#x20;Please refer to [the user guide](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-2gb-devkit#write) to record the system image file ([JetPack 4.6](https://developer.nvidia.com/embedded/l4t/r32\_release\_v6.1/jeston\_nano\_2gb/jetson-nano-2gb-jp46-sd-card-image.zip)) into the microSD card and complete the system initialization.

{% hint style="info" %}
The system image file link in the user guide ([https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-2gb-devkit#write](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-2gb-devkit#write)) points to JetPack 4.6.1, download and burn it to a microSD card After that, system initialization may fail when the Jetson Nano is started. So we recommend using the earlier version: **JetPack 4.6**.
{% endhint %}

2\. Use a network cable to connect the Jetson Nano development board to a router or other computer hosts so that it can access the Internet.

3\. Clone or download the code from [GitHub](https://github.com/TomCC7/OpenCat-Imitation), and install the **Ailia SDK** according to [the guide](https://github.com/axinc-ai/ailia-models/blob/master/TUTORIAL.md), the specific method is the same as the above step 3 in **Run on the host computer**, but **NO need** to execute the statement:&#x20;

`pip install -r requirements.txt`

4\. Install the relevant python library files using the following command：

```
sudo apt install python3-pip
sudo apt install python3-matplotlib
sudo apt install python3-scipy
pip3 install cython
pip3 install numpy
sudo apt install nvidia-jetpack
pip3 install dataclasses
pip3 install pyserial
```

5\. Connect the camera and complete its configuration by referring to [the relevant guide](https://developer.nvidia.com/embedded/learn/tutorials/first-picture-csi-usb-camera).&#x20;

Please refer to the technical documentation to complete the setup if you use a USB camera[ the relevant technical documentation](https://forums.developer.nvidia.com/t/jetson-nano-faq/82953) to complete the setup.&#x20;

To connect the USB uploader, you need to use the following command:

`sudo usermod -a -G dialout $USER` to increase user rights.

6\. Start the program, please refer to step 4 and 5 of [**Run on a regular computer**](https://docs.petoi.com/applications/opencat-imitation-tutorial#run-on-a-regular-computer-mac-linux).&#x20;

Now the OpenCat imitation program can run on the Jetson Nano development board. You can refer to other relevant technical documents to improve the program's performance, such as [enabling openCV to support CUDA acceleration](https://jetsonhacks.com/2019/11/22/opencv-4-cuda-on-jetson-nano/).
