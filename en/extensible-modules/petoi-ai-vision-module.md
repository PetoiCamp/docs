# Petoi AI Vision Module

## Function introduction

Petoi AI Vision Module is based on the Arm Cortex-M55, and Ethos-U55 embedded vision module. The Ethos-U55 has 64 to 512 GOP/s of arithmetic power to meet the growing demand for downloading machine learning.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

## BiBoard <a href="#biboard" id="biboard"></a>

### Hardware setup <a href="#hardware-setup-1" id="hardware-setup-1"></a>

#### BiBoard V0

<figure><img src="../.gitbook/assets/image (536).png" alt=""><figcaption></figcaption></figure>

#### BiBoard V1

<figure><img src="../.gitbook/assets/image (537).png" alt=""><figcaption></figcaption></figure>

Fix the end connected to the camera to the robot's head (included in Bittle's / Bittle X's mouth or Bittle R's robotic arm).

### Software setup <a href="#software-setup-1" id="software-setup-1"></a>

#### **Petoi Desktop App**

You can use the [Firmware Uploader](https://docs.petoi.com/desktop-app/firmware-uploader#select-the-correct-options-to-upload-the-latest-firmware) within the Petoi Desktop App.

Please select the correct _**Product**_ type, _**Borard version**_, and _**Serial port**_. The mode should be **Standard**, so press the **Upgrade the Firmware** button. for example, Bittle, BiBoard\_V0\_2, COM5 as follows:

<figure><img src="https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FaleqWtxk5PSH9bWe9CfF%252Fimage.png%3Falt%3Dmedia%26token%3Dc92b21ff-992f-4163-a981-86078e26eedd&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=308febb4&#x26;sv=1" alt=""><figcaption></figcaption></figure>

After uploading, [open the serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) and use the serial command "_**XC**_" to switch to using the camera mode.

#### **Arduino IDE**

1. Download the latest **Seeed\_Arduino\_SSCMA** library(.zip) from the [GitHub repository](https://github.com/Seeed-Studio/Seeed_Arduino_SSCMA/releases).&#x20;

Then, add the library to your Arduino IDE by selecting **Sketch** > **Include Library** > **Add .ZIP Library** and choose the downloaded file.

Or you can install the library in the Library Manager of the Arduino IDE as follows:

<figure><img src="../.gitbook/assets/image (539).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (538).png" alt=""><figcaption></figcaption></figure>

2\. Use Arduino IDE to [upload the sketch](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.-set-up-biboard)(_**OpenCatEsp32.ino**_).

Use the latest OpenCatESP32 source code to finish the setup. For example, to modify the code for _**Bittle**_ as shown below:

<figure><img src="https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FGu37FwV2ge9LKHORqrUl%252Fimage.png%3Falt%3Dmedia%26token%3D6b0f5ed3-eb4b-4668-8f5a-3e7462718519&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=fa49fffa&#x26;sv=1" alt=""><figcaption><p><em><strong>OpenCatEsp32.ino</strong></em></p></figcaption></figure>

<figure><img src="../.gitbook/assets/AI vision module code.png" alt=""><figcaption><p>src/camera.h</p></figcaption></figure>

After uploading, [open the serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) and use the serial command "_**XC**_" to switch to using the camera mode.