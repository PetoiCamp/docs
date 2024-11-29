# Grove Vision AI V2

## Function introduction

Grove Vision AI V2 is based on the Arm Cortex-M55 and Ethos-U55 embedded vision module. The Ethos-U55 has 64 to 512 GOP/s of arithmetic power to meet the growing demand for downloading machine learning.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## BiBoard <a href="#biboard" id="biboard"></a>

### Hardware setup <a href="#hardware-setup-1" id="hardware-setup-1"></a>

#### BiBoard V0

![](../.gitbook/assets/GroveVisionAI_V2_B0.png)

#### BiBoard V1



Note: The position of the left and right switches (left: down and up; right: down and down) must be dialed to the position shown in the figure.

Fix the end connected to the camera to the robot's head (included in Bittle's / Bittle X's mouth).

### Software setup <a href="#software-setup-1" id="software-setup-1"></a>

#### **Petoi Desktop App**

You can use the [Firmware Uploader](https://docs.petoi.com/desktop-app/firmware-uploader#select-the-correct-options-to-upload-the-latest-firmware) within the Petoi Desktop App.

Please select the correct _**Product**_ type, _**Borard version**_, and _**Serial port**_. The mode should be **Standard**, so press the **Upgrade the Firmware** button. for example, Bittle, BiBoard\_V0\_2, COM5 as follows:

![](https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FaleqWtxk5PSH9bWe9CfF%252Fimage.png%3Falt%3Dmedia%26token%3Dc92b21ff-992f-4163-a981-86078e26eedd\&width=768\&dpr=4\&quality=100\&sign=308febb4\&sv=1)

After uploading, [open the serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) and use the serial command "_**XC**_" to switch to using the camera mode.

#### **Arduino IDE**

1. First, download and install the [MU camera library](https://github.com/mu-opensource/MuVisionSensor3) into the [Arduino IDE](https://www.arduino.cc/en/software).

![](https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FrwlwHLV03mwtrtqVazop%252FmuLib.png%3Falt%3Dmedia%26token%3Df7721966-efb2-4388-9563-002c9aa93c3a\&width=768\&dpr=4\&quality=100\&sign=bd37909a\&sv=1)![](https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FRN0NyFXOV0ct9IOI0AqU%252FaddZipLib.png%3Falt%3Dmedia%26token%3D4803980c-41cf-406c-907c-3aaff81672ec\&width=768\&dpr=4\&quality=100\&sign=2a74ceaa\&sv=1)

2\. Use Arduino IDE to [upload the sketch](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.-set-up-biboard)(_**OpenCatEsp32.ino**_).

Use the latest OpenCatESP32 source code to finish the setup. For example, to modify the code for _**Bittle**_ as shown below:

![](https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FGu37FwV2ge9LKHORqrUl%252Fimage.png%3Falt%3Dmedia%26token%3D6b0f5ed3-eb4b-4668-8f5a-3e7462718519\&width=768\&dpr=4\&quality=100\&sign=fa49fffa\&sv=1)

After uploading, [open the serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) and use the serial command "_**XC**_" to switch to using the camera mode.
