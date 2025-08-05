---
description: >-
  In the ‘Model Training’ section, we explained how to train a yolov8 model, but
  in order to deploy it on Grove Vision V2, we need to further quantify the
  model. This section is described below:
---

# Model quantification

* Model INT8 quantification
* Model optimisation

## Model INT8 quantification

First of all, we need to get the pt model file. In ‘Model Training’, I explained that we can get the trained pt model file through local training and cloud training.

<figure><img src="../../.gitbook/assets/image (34) (1).png" alt=""><figcaption><p>local</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (35) (1).png" alt=""><figcaption><p>cloud</p></figcaption></figure>

Here's the translation:

Create a new environment using Anaconda (for example, you can name it `petoi_convert_local`), and in the new environment, execute the following commands in sequence:

```
pip install ultralytics
pip install tensorflow
```

<mark style="color:red;">(! Note: We have used anaconda to create a new petoi\_train\_local environment in the model training section, while the petoi\_convert\_local environment and petoi\_train\_local environment used in this section are two different environments, and petoi\_train\_local environment must not be used for the following operations.)</mark>

Next, we need to quantify the model and execute it:

```
yolo export model=${your model path} format=tflite imgsz=192 int8
```

You will see a `yolov8n_saved_model folder` in the current folder containing the `yolov8n_full_integer_quant.tflite` model file.

<figure><img src="../../.gitbook/assets/image (36) (1).png" alt=""><figcaption></figcaption></figure>

## Model optimisation

Next, we will perform model optimization. If you are using a Windows computer, you need to install Microsoft C++ Build Tools. If you are a Mac or Linux user, you do not need to install it."

{% embed url="https://visualstudio.microsoft.com/zh-hans/visual-cpp-build-tools/" %}

Execute：

```
pip3 install ethos-u-vela
```

This tool is used to compile a [TensorFlow Lite for Microcontrollers](https://www.tensorflow.org/lite/microcontrollers) neural network model into an optimised version that can run on an embedded system containing an [Arm Ethos-U NPU](https://www.arm.com/products/silicon-ip-cpu).

Create vela\_config.ini, copy the following to vela\_config.ini

```
; file: my_vela_cfg.ini ; ----------------------------------------------------------------------------- 
; Vela configuration file ; ----------------------------------------------------------------------------- 
; System Configuration 

; My_Sys_Cfg 
[System_Config.My_Sys_Cfg] 
core_clock=400e6 
axi0_port=Sram 
axi1_port=OffChipFlash 
Sram_clock_scale=1.0 
Sram_burst_length=32 
Sram_read_latency=16 
Sram_write_latency=16 
Dram_clock_scale=0.75 
Dram_burst_length=128 
Dram_read_latency=500 
Dram_write_latency=250 
OnChipFlash_clock_scale=0.25 
OffChipFlash_clock_scale=0.015625 
OffChipFlash_burst_length=32 
OffChipFlash_read_latency=64 
OffChipFlash_write_latency=64 
; ----------------------------------------------------------------------------- 
; Memory Mode 
; My_Mem_Mode_Parent 
[Memory_Mode.My_Mem_Mode_Parent] 
const_mem_area=Axi1 
arena_mem_area=Axi0 
cache_mem_area=Axi0
```

Execute in the terminal：

```
vela --accelerator-config ethos-u55-64 --config vela_config.ini --system-config My_Sys_Cfg --memory-mode My_Mem_Mode_Parent --output-dir ${Save path of the optimized model} ${The path of the tflite model that needs to be optimized}
```

Replace _**`${Save path of the optimised model}`**_ with the directory you want to output to.&#x20;

Replace _**`${The path of the tflite model that needs to be optimised}`**_ with the quantized model file you just got.

You will then get the model ending in ‘\_vela’, which is the model file that can be used for deployment on Grove Vision V2.

<figure><img src="../../.gitbook/assets/image (37) (1).png" alt=""><figcaption></figcaption></figure>

