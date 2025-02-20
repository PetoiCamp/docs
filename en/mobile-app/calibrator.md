# Calibrator

## Calibrate the joints

### Nybble

![Calibration Interface](../.gitbook/assets/Nybble\_Cali\_En.png)

### Bittle



![Calibration Interface](../.gitbook/assets/calibPanel.png)

{% hint style="info" %}
The above interfaces will be displayed when you calibrate for the first time. You can also click to open the upper-right menu in the control panel and select **Calibrate** to re-access.

![](../.gitbook/assets/Control\_Cali\_en.jpg)
{% endhint %}

## Prepare for calibration

{% hint style="info" %}
Make sure you have uploaded the OpenCat [**Main function**](https://docs.petoi.com/desktop-app/firmware-uploader#uploading-process) firmware before calibrating.

Only the software version 2.0 is supported to calibrate the joints via this App.
{% endhint %}

You need to connect the [**Bluetooth module**](https://docs.petoi.com/communication-modules/dual-mode-bluetooth#connection-with-nyboard) (for NyBoard only) with computer, install the battery and long-press the button on the battery to power the robot.

## Enter the calibration state

After the robot is powered on, there are 2 methods to enter the calibration state:

*   Click the **Start Calibration** button.\


    <figure><img src="../.gitbook/assets/image (241).png" alt=""><figcaption></figcaption></figure>
*   Click the **Calibration** button in the calibration interface.\


    <figure><img src="../.gitbook/assets/image (314).png" alt=""><figcaption></figcaption></figure>

### Install the head

In the calibration state, place the head as close to the central axis as possible and insert its servo shaft into the servo arm of the neck.

<figure><img src="../.gitbook/assets/assets_bittle_cali_head01.jpeg" alt=""><figcaption></figcaption></figure>

Press down on the head so it is firmly attached to the neck.

<figure><img src="../.gitbook/assets/assets_bittle_cali_head02.jpeg" alt=""><figcaption></figcaption></figure>

### Install the legs&#x20;

Install upper leg and lower leg components to the output teeth of the servos when the Bittle is powered on and in the calibration state. Please keep the torso, upper leg, and lower leg installed vertically as much as possible, and do not install the lower leg backward, as shown in the picture.&#x20;

<figure><img src="../.gitbook/assets/assets_bittle_cali_leg01.jpeg" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The pre-assembled robot should already have the legs properly installed. You can do the joint calibration for fine-tuning.&#x20;
{% endhint %}

**Use the included L-shaped tool as a reference!**

#### Nybble

![](<../.gitbook/assets/Nybble-L (2).jpg>)

#### Bittle

![](<../.gitbook/assets/assets\_bittle\_-MSGw-I0q\_j0kHosz8nz\_-MSGx1sAobtzY1ucuddF\_53 (2).jpeg>)

![Align the upper leg first](../.gitbook/assets/calib1.png)

![Pay attention to the reference edges for the lower leg](../.gitbook/assets/calib2.png)

When calibrating, first select the index number of the joint servo from the diagram(when adjusting the leg servo, adjust the thigh first, and then adjust the calf), and then click the "+" or "-" button to fine-tune the joint to the right angle state.&#x20;

{% hint style="info" %}
If the offset is more than +/- 9 degrees, you need to remove the corresponding part of the servo and re-install it by rotating one tooth, and then press the "+" or "-" button.

For example, if you have to use -10 as the calibration value, take the limb off, rotate by one tooth then attach it back. The new calibration value should be around 4, i.e.,  they sum up to 14. Avoid rotating the servo shaft during this adjustment.&#x20;
{% endhint %}

You can click the skill buttons to switch between **Rest**, **Stand**, and **Walk** to test the calibration effect.&#x20;

![Bittle](../.gitbook/assets/calibValidation\_Bittle.png)

If you want to continue calibrating, please click the **Calibration** button, and the robot will be in the calibration state again (all servos will move to the calibration position immediately).&#x20;

{% hint style="info" %}
Note:&#x20;

You may need a second round of calibrations to achieve optimal results.
{% endhint %}

After calibration, remember to click the "Save" button to save the calibration offset. Otherwise, click "<" in the upper left corner to abandon the calibration.

### Install the screws

After completing the joint calibration, install the center screws to fix the leg parts and servo gears.
