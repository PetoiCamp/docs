# NyBoard Preparation

For [Nyboard](https://docs.petoi.com/nyboard/overview) products ([**Nybble**](https://nybble.petoi.com), [**Bittle**](https://bittle.petoi.com)), there are two ways to upload the firmware (Mind+ mode), which supports the Mind+ extension library:

*   [Using the Petoi Desktop App](../../desktop-app/firmware-uploader/)<br>

    <figure><img src="../../.gitbook/assets/image (380).png" alt=""><figcaption></figcaption></figure>

    * If you just downloaded a new version of this Desktop App. You should click the **Upgrade the Firmware** button. You can select 'N' to preserve the calibration values.
    * If you have upgraded the firmware at least once after a new download, You can click the **Update the Mode Only** button. It's faster to only switch the modes without refreshing the parameters.
*   [Using the Arduino IDE](../../arduino-ide/upload-sketch-for-nyboard.md)\
    Please download the latest code from [GitHub](https://github.com/PetoiCamp/OpenCat). Follow the steps for [uploading](https://docs.petoi.com/arduino-ide/upload-sketch-for-nyboard#upload). [Set up the configuration mode](https://docs.petoi.com/arduino-ide/upload-sketch-for-nyboard#2.-setup-the-configuration-mode) and activate this line of code in **OpenCat.ino**\
    &#xNAN;**`#define MAIN_SKETCH`**

    **`#define GROVE_SERIAL_PASS_THROUGH`**

    Then, upload [the major functionalities sketch](https://docs.petoi.com/arduino-ide/upload-sketch-for-nyboard#10.-upload-the-major-functionalities-sketch) and power on the robot. Use the data cable and [USB uploader](https://docs.petoi.com/communication-modules/usb-downloader-ch340c) to connect with the computer or [the Bluetooth module](https://docs.petoi.com/communication-modules/dual-mode-bluetooth) and complete the pairing.

Note that the gyroscope function is turned off with the Mind+ mode on NyBoard to save memory space.  The robot won't be able to self-balance and auto-recover.

{% hint style="warning" %}
If you don't use the "[Read or Write analog/digital pin](nyboard-preparation.md#write-analog-value)" function block, you can upload [the Standard mode sketch](https://docs.petoi.com/arduino-ide/upload-sketch-for-nyboard#11.-the-module-macro-in-the-code) for Bittle / Nybble and use the Mind+ extension library.\
**Note:**

When the robot is in Mind+ mode, the gyroscope function is turned off, and the robot cannot balance or auto-recover.
{% endhint %}

#### After uploading the firmware, plug in the battery to the NyBoard, install it to the chassis and long-press the battery button to power on the robot.

#### Connect method

* Wired connection: The kit includes a [**USB Adapter and USB data cable**](https://docs.petoi.com/communication-modules/usb-downloader-ch340c) connecting the robot's mainboard to the computer.
* Wireless connection(Bluetooth)： The kit includes a [**Bluetooth module**](https://docs.petoi.com/communication-modules/dual-mode-bluetooth) connecting the robot's mainboard to the computer.
