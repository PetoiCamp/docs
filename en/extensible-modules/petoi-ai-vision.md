# Petoi AI Vision

## Function introduction

Petoi AI Vision Module is based on the Arm Cortex-M55, and Ethos-U55 embedded vision module. The Ethos-U55 has 64 to 512 GOP/s of arithmetic power to meet the growing demand for downloading machine learning.

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Hardware setup <a href="#hardware-setup-1" id="hardware-setup-1"></a>

### BiBoard V0

<figure><img src="../.gitbook/assets/image (596).png" alt="Bittle X: BiBoard V0 with AI vision module"><figcaption><p>Bittle X</p></figcaption></figure>

### BiBoard V1

<figure><img src="../.gitbook/assets/image (605).png" alt="Bittle X: BiBoard V1 with AI vision module"><figcaption><p>Bittle X</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (605) (1).png" alt="Bittle X+Arm: BiBoard V1 with AI vision module"><figcaption><p>Bittle X+Arm</p></figcaption></figure>

Fix the end connected to the camera to the robot's head (included in Bittle's / Bittle X's mouth or attached to Bittle X+Arm's robotic arm).

{% hint style="info" %}
If you use the version of Petoi Desktop App <= **V1.2.5**,  you need to connect the Petoi AI vision module to the following Grove socket:\
<img src="../.gitbook/assets/image (597).png" alt="Bittle X" data-size="original"><br>

<img src="../.gitbook/assets/image (595).png" alt="Bittle X+Arm" data-size="original">
{% endhint %}

## Software setup <a href="#software-setup-1" id="software-setup-1"></a>

There are two methods to upload the firmware :

* Using the Petoi Desktop App
* Using the Arduino IDE

### **Petoi Desktop App**

You can use the [Firmware Uploader](https://docs.petoi.com/desktop-app/firmware-uploader#select-the-correct-options-to-upload-the-latest-firmware) within the Petoi Desktop App.

Please select the correct _**Product**_ type, _**Board version**_, and _**Serial port**_ according to your actual use. \
The mode should be **Standard**, so press the **Upgrade the Firmware** button. \
For example, Bittle, BiBoard\_V0\_2, COM5 as follows:

<figure><img src="https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FaleqWtxk5PSH9bWe9CfF%252Fimage.png%3Falt%3Dmedia%26token%3Dc92b21ff-992f-4163-a981-86078e26eedd&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=308febb4&#x26;sv=1" alt=""><figcaption></figcaption></figure>

### **Arduino IDE**

For more details, please refer to [Upload Sketch for BoBoard](../arduino-ide/upload-sketch-for-biboard.md).

After uploading, there are two methods to _**activate/deactivate**_ the camera mode:

* Serial Monitor
  * [Open the serial monitor](../arduino-ide/serial-monitor.md#biboard) and use the serial command "_**XC**_" to activate the camera mode.
  * Open the serial monitor and use the serial command "_**Xc**_" to deactivate the camera mode.
* Mobile App
  * Create [a mobile app command](https://docs.petoi.com/mobile-app/controller#create-a-single-command) called "**Activate camera**" and use the code: _`X67`_
  * Create a mobile app command called "**Deactivate camera**" and use the code: _`X99`_

### Web debug GUI

Combined with the empowerment of the web debug GUI ([SenseCraft AI Model Assistant](https://sensecraft.seeed.cc/ai/device/local/36)), you can easily upload a wide variety of co-created models and directly observe the results.

{% hint style="info" %}
The camera is already plugged in. After opening the web debug GUI, simply connect Petoi AI Vision to your computer using a Type-C cable and then click the **Connect** button.
{% endhint %}

For how to use this web debug GUI, please refer to:

[https://wiki.seeedstudio.com/grove\_vision\_ai\_v2\_software\_support/#step-2-connect-the-module-and-upload-a-suitable-model](https://wiki.seeedstudio.com/grove_vision_ai_v2_software_support/#step-2-connect-the-module-and-upload-a-suitable-model)

{% hint style="info" %}
If the camera mode can't be activated, as follows:

<img src="../.gitbook/assets/image (551).png" alt="" data-size="original">

You can use the [web debug GUI ](https://sensecraft.seeed.cc/ai/#/device/local)to upgrade the camera firmware and upload the Face Detection model.

<img src="../.gitbook/assets/image (552).png" alt="" data-size="original">
{% endhint %}

{% hint style="warning" %}
To run the example code (inference.ino) in the library [Seeed\_Arduino\_SSCMA](https://github.com/Seeed-Studio/Seeed_Arduino_SSCMA/releases), you should add the library to your Arduino IDE by selecting Sketch > Include Library > Add .ZIP Library and choosing the downloaded file.

Or you can install the library in the Library Manager of the Arduino IDE as follows:

<img src="https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FQGc7naMMVovRINWe5Dmr%252Fimage.png%3Falt%3Dmedia%26token%3D173d8e90-f3b1-4e1c-94de-da12bdd6b79f&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=661a539a&#x26;sv=2" alt="" data-size="original">\
\
![](<../.gitbook/assets/image (556).png>)
{% endhint %}

## More Application

The Petoi AI vision module also supports taking photos and transmitting images via Wi-Fi, but it needs to be installed on a MCU with more powerful computing power (such as ESP32S3, ESP32C3, etc.). For the specific development process, please refer to the wiki technical documentation:

{% embed url="https://wiki.seeedstudio.com/grove_vision_ai_v2_demo/" %}

{% embed url="https://wiki.seeedstudio.com/grove_vision_ai_v2_webcamera/" %}

{% embed url="https://wiki.seeedstudio.com/vision_ai_v2_crowd_heat_map/" %}
