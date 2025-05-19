# NyBoard

Use the [**USB uploader for NyBoard**](https://docs.petoi.com/upload-firmware/nyboard)**.**

For more details, please refer to the [Connect NyBoard](https://docs.petoi.com/communication-modules/usb-downloader-ch340c#connect-nyboard) section in the USB uploader module for specific steps.

<figure><img src="../../.gitbook/assets/image (414).png" alt=""><figcaption><p>NyBoard</p></figcaption></figure>

## NyBoard Version

You can find the board version number on the NyBoard.

{% hint style="info" %}
Note:&#x20;

For **NyBoard V1\_1**, the board version number is here:

![](<../../.gitbook/assets/NyBoardV1_1 (3).jpg>)\


Dial the I2C switch(Sw2) to the "**Arduino**" side

<img src="../../.gitbook/assets/image (144).png" alt="" data-size="original">

The I2C switch changes the master of I2C devices (gyro/accelerometer, servo driver, external EEPROM). On default “Arduino”, NyBoard uses the onboard ATmega328P as the master chip; On “RPi”, NyBoard uses external chips connected through the I2C ports (SDA, SCL) as the master chip. Always select "Arduino" unless you can connect the I2C devices from the external chip.&#x20;
{% endhint %}

{% hint style="warning" %}
Notes：

* Sometimes, if you cannot go through the bootup stage, such as repetitively printing "IMU" and restarting, you may have accidentally dialed the switch to the "RPi" side.&#x20;
* Before uploading the firmware, please ensure that no I2C device is connected to the I2C interface of the mainboard. Otherwise, the firmware upload will fail. The location of the I2C interface is as shown below (in the red box): ![](../../.gitbook/assets/I2C接口.png)
{% endhint %}

## Uploading options

* **Factory Reset**\
  Our factory uses it to improve efficiency. However, it automatically resets all the parameters, including the calibration parameters of the servos and the IMU, so it's not recommended for regular users.&#x20;
* **Upgrade the Firmware**\
  It will upgrade both the **Parameters** and the **Main function** firmware.\
  It is mandatory if you just downloaded a new version of this desktop app.
* **Update the Mode Only**\
  If you have **upgraded the firmware** at least once after downloading a new version of this desktop app, you can switch between the modes without refreshing the parameters. It's faster by skipping the firmware upgrade stage.&#x20;

## **Upgrade the firmware** process for NyBoard

After clicking the **Upgrade the Firmware** button, the uploading process starts immediately. The status bar at the bottom shows the current progress in real time and the results of key processes.

After the **Parameters** firmware has been successfully uploaded, the board runs the configuration program. Some message windows will pop up in sequence for you to confirm or cancel:

*   Reset joint offsets? (Y/N)\


    <figure><img src="../../.gitbook/assets/image (408).png" alt=""><figcaption></figcaption></figure>

Select "Yes, " and the program will reset all servo calibration parameters to zero. The status bar will update the corresponding process and result in real time.

Select "No" to preserve the calibration value(so that you don't need to calibrate again if you have done so before). &#x20;

{% hint style="info" %}
For software version **1.0**, there is a warning message window of "Update Instincts? (Y/N)"   will pop up as follows:\
![](<../../.gitbook/assets/image (412).png>)

If you select "Yes," the program will upload all skill configuration parameters, and the status bar will update the corresponding process and result in real-time.

Select "No," and the program will skip this step.

If you upload this version of the software for the first time,  be sure to select "Yes"!

For software version **2.0**, this choice is automatically processed as Y in the background.&#x20;
{% endhint %}

*   Calibrate IMU? (Y/N)\


    <figure><img src="../../.gitbook/assets/image (409).png" alt=""><figcaption></figcaption></figure>

Select "Yes, " and the program will calibrate the gyroscope (IMU) to balance the robot correctly. The status bar will update the corresponding process and result in real time.

Select "No," and the program will skip this step.

{% hint style="danger" %}
Note:&#x20;

1. &#x20;Ensure the mainboard is positioned horizontally before clicking the "Yes" button.&#x20;
2. &#x20;When uploading this firmware version for the first time, click the "Yes" button!&#x20;
{% endhint %}

When all the steps are completed, a message window will appear showing "Parameter initialization complete!" You **must** confirm to proceed to the second round of uploading the **Main functional** firmware.&#x20;

<figure><img src="../../.gitbook/assets/image (410).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
### Calibrate the servo controller chip PCA9685 on the NyBoard.

When the above window pops up, there's an optional step to calibrate the servo driver before clicking OK. If you later find one of the servos stops working but can resume working after re-powering it, it's probably due to an inaccurate PWM driver signal. Please redo the previous upload, and this step **CANNOT** be skipped.&#x20;

This calibration makes the servo controller's (PCA9685 chip) angle signal more precise. A short jumper wire connects PWM pin 3 (the signal pin of one of the servo pins) and Grove pin A3, and the wire is steady. It doesn’t have to be a dedicated jumper wire. Any thin metal wire, such as a straightened paper clip, can work as long as it can connect the pins.

<img src="../../.gitbook/assets/jumper.jpg" alt="" data-size="original">

The program measures the pulse width of the signal and automatically calibrates the chip after successively getting three identical readings. It usually takes less than 2 seconds. The board will beep three times to indicate that the calibration is done. The calibration offset will be saved to the board for the next bootup. The process should be done at least once, and we have calibrated every board after October 2022. But you can still do it by yourself, just in case.&#x20;
{% endhint %}
