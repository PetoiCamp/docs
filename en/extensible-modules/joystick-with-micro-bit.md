# 🎮 Joystick with Micro: Bit

This remote controller is a Micro: Bit-based gamepad. It includes a 4-direction joystick and four undefined buttons. To enhance the gaming experience, it is also paired with a buzzer and vibration motor. It is compact in appearance, comfortable in hand, and can be remotely controlled.

<figure><img src="../.gitbook/assets/image (557).png" alt=""><figcaption></figcaption></figure>

## Hardware

{% hint style="info" %}
Micro: Bit V1 has a smaller memory. So, the full functionality requires **Micro: Bit V2**.
{% endhint %}

## Software setup

The Joystick's source code is now open-sourced. It can control Bittle X, Bittle X+Arm (Bittle with a robotic arm), and Nybble Q. For more information, please refer to our [GitHub repository](https://github.com/PetoiCamp/ESP32_Microbit_Controller).

You can download the program file([microbit-JoyStick.hex](https://github.com/PetoiCamp/ESP32_Microbit_Controller/blob/main/microbit-JoyStick.hex)), then import the program to [the programming platform makecode](https://makecode.microbit.org) as follows:

{% hint style="info" %}
We recommend you use the **Chrome** browser.
{% endhint %}

<figure><img src="../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Download the program to the Micro: Bit V2

Connect your PC to the Micro: Bit V2 using a USB cable.

![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/connect-microbit.gif)

After a successful connection, a disk drive named `MICROBIT` is recognized on the computer.

![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/microbit-drive.png)

Click on the bottom left corner of the ![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/download-01.png) button， Select `Connect Device`.

![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/download-02.png)

Click ![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/download-03.png) button.

![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/download-04.png)

Click![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/download-05.png)

![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/download-06.png)

Select `BBC micro:bit CMSIS-DAP` in the pop-up window and then select Connect. At this point, our Micro: Bit has connected successfully.

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Click to download the program.

![](https://wiki-media-ef.oss-cn-hongkong.aliyuncs.com/docs/microbit/interesting-case/microbit-smart-climate-kit/cases-libraries/images/download-08.png)

## How to use&#x20;

1. [Upload the newest firmware](https://docs.petoi.com/upload-firmware) to the robot (mainboard type: **BiBoard**)
2. Install 2 x #7 AAA batteries and plug in the Micro: Bit V2 to the remote controller. Then power on the remote controller as follows:\
   ![](<../.gitbook/assets/image (5) (1).png>)\

3. Power on the robot. During the bootup, it can connect to the controller automatically via Bluetooth.\
   If there are many remote controllers and robots, the connection is one-to-one and first-come-first-served.

{% hint style="info" %}
After a successful Bluetooth connection, the robot automatically disconnects every 20 minutes (indicated by an hourglass animation on the LED matrix). To re-establish the Bluetooth connection, touch the Micro: Bit's logo (a touch button) and hold the controller vertically with the left joystick at the lower side, as shown in the figure:\
![](<../.gitbook/assets/image (550).png>)\
After a successful reconnection, you will hear a prompt tone, and the LED matrix will play an animated hourglass flowing reversely.
{% endhint %}

## Controller function introduction

### To control Bittle X+Arm (with robot arm):

<figure><img src="../.gitbook/assets/BittleR_en.png" alt=""><figcaption></figcaption></figure>

### To control Bittle X:

<figure><img src="../.gitbook/assets/BittleX_en.png" alt=""><figcaption></figcaption></figure>

### To control Nybble Q:

<figure><img src="../.gitbook/assets/NybbleQ_en.png" alt=""><figcaption></figcaption></figure>
