---
description: >-
  In this section, we will learn how to upload the model to the hardware and
  complete communication with the Petoi robot dog.
---

# Model deployment

Grove Vision AI V2 can be deployed via an online website, which itself has a rich resource of models for you to choose from, so in addition to training your own models you can also use the models directly from the website.

{% embed url="https://sensecraft.seeed.cc/ai/#/model" %}

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

At the top of the page, you will see three columns titled: AI Models, Device Workspace, and About SenseCraft AI. click on Device Workspace and select Grove - Vision AI V2.

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption><p>Select Grove - Vision AI V2</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Click the Connect button</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption><p>Click on the serial port you want to pair with, COM3 in the picture.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

In the Models area, you can select models provided by SenseCraft AI or upload your own trained models.

<figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption><p>Click ‘Select Model’ to select your favourite model.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

It takes a little while to upload the model, so you will need to be patient.

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

In the preview section, you can observe the output results of the Grove Vision V2 's inference in real time, for example, it successfully detects cats after downloading the pet detection function.

<figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

In the ‘Device Logger’ section, the device sends real-time inspection data to the computer, and the data in the ‘Boxes’ section is：

```
{ 
x; // 盒子中心的水平坐标 
y; // 盒子中心的垂直坐标 
w; // 识别框的宽度 
h; // 识别框的高度 
score; // 识别为目标的可信度 
target; // 目标
 }
```

Communicating with Petoi robot dogs using Grove Vision AI V2

You can use the Arduino IDE to modify our open source programme to use Grove Vision AI V2. Our programme integrates target tracking with Grove Vision AI V2. You only need to modify the code to enable this feature. For details on how to use it, see:&#x20;

[https://app.gitbook.com/o/-M-\_eWZUjFA4usjshHcZ/s/ntUipGYjnJE9HQWSovJT/](https://app.gitbook.com/o/-M-\_eWZUjFA4usjshHcZ/s/ntUipGYjnJE9HQWSovJT/).&#x20;

In addition, you can develop richer functionality using the APIs associated with the SSCMA library.
