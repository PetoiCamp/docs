# BiBoard V0

Use the [**USB Type-C data cable for BiBoard V0**](https://docs.petoi.com/upload-firmware/biboard-v0)**.**

## **BiBoard V0 version**

<figure><img src="../../.gitbook/assets/image (413).png" alt=""><figcaption></figcaption></figure>

You can find the board version number on the BiBoard V0:

<figure><img src="../../.gitbook/assets/image (430).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
On the pre-assembled Bittle X, you can check the version information of BiBoard like this by taking a picture and zooming in to see the version information:

<img src="../../.gitbook/assets/BiBoard_Version.jpg" alt="" data-size="original">
{% endhint %}

## Uploading options

* **Factory Reset**\
  After upgrading the firmware, the board will enter the [**initialization startup mode**](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.8-program-initialization) and ask whether to clear the joint calibration parameters and calibrate the IMU.
* **Upgrade the Firmware**\
  It will upgrade the firmware, skip the clear joint calibration parameters,  calibrate the IMU steps (Send serial command "**n**"), and automatically enter the [**regular startup mode**](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.8-program-initialization).
* **Update the Mode Only**\
  It has the same function as the **Upgrade the Firmware** at present.

## **Factory reset** process

After clicking the **Factory Reset** button, the uploading process will start immediately. The board will enter the [**initialization startup mode**](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.8-program-initialization) after uploading the firmware. Some message windows will pop up in sequence for you to confirm or cancel:

1.  Reset joint offsets? (Y/N)\


    <figure><img src="../../.gitbook/assets/image (408).png" alt=""><figcaption></figcaption></figure>

Select **Yes**, and the program will reset all servo calibration parameters to zero. The status bar will update the corresponding process and result in real time.

Select **No** to preserve the calibration value(so that you don't need to calibrate again if you have already done so). &#x20;

2. Calibrate IMU? (Y/N)\


<figure><img src="../../.gitbook/assets/image (409).png" alt=""><figcaption></figcaption></figure>

Select **Yes**,  and the program will calibrate the gyroscope (IMU) to balance the robot correctly. The status bar will update the corresponding process and result in real time.

Select **No**, and the program will skip this step.

After that, the board will enter the [**regular startup mode**](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.8-program-initialization)**.**

{% hint style="danger" %}
Note:&#x20;

Ensure the mainboard is positioned horizontally for IMU calibration before clicking the "Yes" button.&#x20;
{% endhint %}
