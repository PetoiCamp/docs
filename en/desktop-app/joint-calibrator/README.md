---
description: Robots can be precisely calibrated using the Petoi Desktop App.
---

# Joint Calibrator

### \*\* Download the latest version of the [Petoi Desktop APP](https://github.com/PetoiCamp/DesktopAppRelease/releases). \*\*

{% hint style="info" %}
* After you download the compressed file(.zip), please unzip it first.
* Do **NOT** move the UI.exe to another location in Windows.
{% endhint %}

## Prepare for calibration

Please follow the instructions in the subpages to prepare according to the robot's mainboard.

{% hint style="info" %}
Only software version 2.0 can calibrate the joints via this App.
{% endhint %}

{% hint style="info" %}
For **Bittle X+Arm**, you must install the short wire servo in the servo slot on the robotic arm. For more information, please refer to [the instructions](https://app.gitbook.com/o/-M-_eWZUjFA4usjshHcZ/s/-MQ6a951Q6Jn1Zzt5Ajr-887967055/~/changes/650/desktop-app/joint-calibrator/bittle-x+arm/~/overview#prepare-for-calibration) in the subpage.
{% endhint %}

## Calibration process

### Enter the calibration state

{% hint style="info" %}
You must connect the battery to the mainboard and long-press the battery button for more than 3 seconds to power on the robot.
{% endhint %}

&#x20;After the robot is powered on by a battery, there are two methods to enter the calibration state:

*   It will enter the calibration state automatically when you click the **Joint Calibrator** button.<br>

    <figure><img src="../../.gitbook/assets/image (367).png" alt=""><figcaption></figcaption></figure>
* Click the **Calibrate** button in the calibrator interface. Take Bittle for example:

<figure><img src="../../.gitbook/assets/image (589).png" alt=""><figcaption></figcaption></figure>

### 2. The rationale for calibration

### 2.1 Understand the zero state and the coordinate system

After typing ‘c’ in the serial monitor, with all servos rotated to their zero angles, attach the head, tail, and legs prepared in the previous section to the body. They are generally perpendicular to their linked body frames. The calibration pose is shown below:

![Nybble's Calibration State](<../../.gitbook/assets/calibration_Nybble (2).png>)

![Bittle's Calibration State](<../../.gitbook/assets/zero (2).png>)

{% hint style="info" %}
If you are building the robot from a kit, install the servo-related components according to the picture above and try to ensure that they are perpendicular to each other (the upper leg is perpendicular to the torso, and the lower leg is perpendicular to the upper leg). Please refer to the related chapter in the user manual for the details:

* Nybble
* [Bittle](https://bittle.petoi.com/6-calibration)
{% endhint %}

{% hint style="warning" %}
Note: Insert the servo-related components directly into the servo output shaft; do not turn the output shaft during this process.
{% endhint %}

&#x20;Rotating the limbs counter-clockwise from their zero states will be positive (same as in polar coordinates). Viewed from the left side of the robot's body, the counter-clockwise rotation of the joint is defined as the positive direction.

{% hint style="info" %}
The only exception is the tilt angle for the head of Nybble. It’s more natural to say head up, while it’s the result of rotating clockwise.&#x20;
{% endhint %}

{% hint style="info" %}
However, from the right side of the robot's body, the rotation direction's positive and negative are just opposite.
{% endhint %}

### 2.2 Discrete angular intervals

If we look closer at the servo shaft, we can see it has a certain number of teeth. That’s for attaching the servo arms and avoiding sliding in the rotational direction. In our servo sample, the gears divide 360 degrees into 25 sectors, each taking **14.4** degrees(offset of -7.2\~7.2 degrees). That means we cannot always get a perfect perpendicular installation.&#x20;

![](<../../.gitbook/assets/assets_bittle_-MTLzoDqllmeUcpCu5jV_-MTM-Wiv6R3xuNmAhgrE_37 (1).png>)

### Installing and Fine-tuning

The joint calibration interface of different products is shown in the following subpages.

There are two kinds of kit: the **construction** kit and the **pre-assembled** kit.

* For the **construction** kit, you must install the components (such as the head, legs, and tail) after the robot enters the calibration state. For more details, please follow the suppage instructions.
* The **pre-assembled** kit already has the components adequately installed. You can do the joint calibration for fine-tuning.&#x20;

The included L-shaped tool can be used as a reference during calibration. For more details, please follow the instructions on the subpages.

### Validation and Save data

You can switch between  "**Rest**", "**Stand up**" and "**Walk**" to test the calibration effect.&#x20;

If you want to continue calibrating, please click the **Calibration** button, and the robot will be in the calibration state again (all servos will move to the calibration position immediately). take Bittle for example:

![Bittle /Bittle X](<../../.gitbook/assets/calibrBittle_cali_en (1).png>)

{% hint style="info" %}
Note:&#x20;

You may need a second round of calibrations to achieve optimal results.
{% endhint %}

After calibration, remember to click the "**Save**" button to save the calibration offset. Otherwise, click the "**Abort**" button to abandon the calibration data. You can save the calibration in the middle in case your connection is interrupted.&#x20;

{% hint style="info" %}
When you close this window, there is a message box shown below:

![](<../../.gitbook/assets/image (160).png>)

If you want to save the calibration data, please click the "**Yes**" button; otherwise, click the "**No**" button. Click the "**Cancel**" button to cancel or quit.
{% endhint %}

### Install the screws for the construction kit

After completing the joint calibration, install the center screws to fix the components and servo gears.
