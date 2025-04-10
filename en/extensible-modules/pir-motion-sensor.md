# PIR Motion Sensor

{% embed url="https://youtu.be/_3CZfGW3Ngw" %}

## Function introduction

This sensor allows you to detect animals' movement, usually humans' movement within its detection range. Just connect it to the NyBoard and program it, and when anyone moves within its detection range, the sensor will output a high potential on its **SIG** pin.

<figure><img src="../.gitbook/assets/PIR_New (1).png" alt=""><figcaption></figcaption></figure>

## NyBoard

### Software setup

#### Petoi Desktop App

*   You can use the [Firmware Uploader ](https://docs.petoi.com/desktop-app/firmware-uploader#select-the-correct-options-to-upload-the-latest-firmware)within the Petoi Desktop App.

    <figure><img src="../.gitbook/assets/image (495).png" alt=""><figcaption></figcaption></figure>

#### Arduino IDE

* You can use [Arduino IDE](https://www.arduino.cc/en/software)  to upload and modify the source code.&#x20;

The code using this sensor has been integrated into the [**OpenCat**](https://github.com/PetoiCamp/OpenCat) project. Uncomment the line **`#define PIR`**  in the **OpenCat.ino**, as shown in the figure below, and use the Arduino IDE to upload the sketch to the robot main board, which can reproduce the example function of integrating the robot action.

#### Prepare the Arduino UNO development environment.

With **NyBoard V1\_\***, you can choose **Arduino Uno**.&#x20;

<figure><img src="../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

#### Modify the code in the OpenCat.ino

<figure><img src="../.gitbook/assets/image (451).png" alt=""><figcaption></figcaption></figure>

### Hardware setup

Connecting to the NyBoard with wire as shown in the following picture:

<figure><img src="../.gitbook/assets/PANA0493-恢复的.jpg" alt=""><figcaption></figcaption></figure>

## &#x20; BiBoard

### Software setup

#### Petoi Desktop App

*   You can use the [Firmware Uploader](https://docs.petoi.com/desktop-app/firmware-uploader#select-the-correct-options-to-upload-the-latest-firmware) within the Petoi Desktop App.\
    Please select the correct _**Product**_ type, _**Borard version**_, and _**Serial port**_. The mode should be **Standard**, so press the **Upgrade the Firmware** button. for example, Bittle, BiBoard\_V0\_2, COM5 as follows:

    <figure><img src="https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FaleqWtxk5PSH9bWe9CfF%252Fimage.png%3Falt%3Dmedia%26token%3Dc92b21ff-992f-4163-a981-86078e26eedd&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=308febb4&#x26;sv=1" alt=""><figcaption></figcaption></figure>

    After uploading, [open the serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) and use the serial command "_**XI**_" to switch to using the PIR motion sensor mode.

#### Arduino IDE

*   You can use [Arduino IDE](https://www.arduino.cc/en/software) to [upload the sketch](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.-set-up-biboard)(_**OpenCatEsp32.ino**_).\
    Use the latest OpenCatESP32 code to finish the setup. For example, to modify the code for _**Bittle**_ as shown below:\


    <figure><img src="https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FGu37FwV2ge9LKHORqrUl%252Fimage.png%3Falt%3Dmedia%26token%3D6b0f5ed3-eb4b-4668-8f5a-3e7462718519&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=fa49fffa&#x26;sv=1" alt=""><figcaption></figcaption></figure>

    \
    After uploading, open the [serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) and use the serial command "_**XI**_" to switch to using the PIR motion sensor mode.&#x20;

### Hardware setup

<figure><img src="../.gitbook/assets/PIR_BiBoard.png" alt=""><figcaption></figcaption></figure>

For specific use, the end connected to the sensor can be fixed on the robot's head (included in Bittle's mouth or attached to the top of Nybble's head). Of course, you can also use your creativity to meet your needs.

## Testing code

If you want to test a PIR motion sensor's function alone or learn more about its principles. You can use the Arduino IDE to upload the demo sketch(**test\_Touch\_Reflection\_PIR.ino**):

* [For NyBoard](https://github.com/PetoiCamp/OpenCat/tree/main/ModuleTests/test\_Touch\_Reflection\_PIR)
* [For BiBoard](https://github.com/PetoiCamp/OpenCatEsp32/tree/main/ModuleTests/test\_Touch\_Reflection\_PIR)

This demo sketch implements real-time printing of sensor detection results in the [serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor) - when anyone moves within its detection range, print 1; otherwise, print 0.

<figure><img src="../.gitbook/assets/image (211).png" alt=""><figcaption></figcaption></figure>
