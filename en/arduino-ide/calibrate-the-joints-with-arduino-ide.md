# Calibrate the joints with Arduino IDE

## Prepare to Enter the Calibration State

Please refer to the [preparation section](../desktop-app/joint-calibrator/#prepare-for-calibration) in the Joint Calibrator of the Petoi Desktop App according to the robot's mainboard.

## Calibration process

### 1. Enter the calibration state

You must plug the servos and external batteries into the mainboard and check the position and direction of all servos.&#x20;

&#x20;Send the serial command ‘**c**’ in the serial monitor to enter the calibration state.  Depending on their initial shaft direction, some may travel larger angles until stopping at the middle point.  There will be noise coming from the gear system of the servos. You will see a calibration table like the following:

![](../.gitbook/assets/caliTable.png)

The first row is the joint indexes; the second row is their calibration offsets:&#x20;

| **Index**  | 0  | 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 | 11 | 12 | 13 | 14 | 15 |
| ---------- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| **Offset** | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 | -1 |

Initial values are “-1” or “0” and should be changed by later calibration.&#x20;

{% hint style="info" %}
The servos use a potentiometer in the feedback loop for position control. When held at a static position, they tend to vibrate around the target angle. A Parkinson's-like vibration will develop after a short period of use. It won’t affect much during continuous motion. Better servos without these troubles could cost 10 times more, so replacing a failed unit is a more cost-effective solution. &#x20;
{% endhint %}

### 2. The rationale for calibration

### 2.1 Understand the zero state and the coordinate system

After typing ‘c’ in the serial monitor, with all servos rotated to their zero angles, attach the head, tail, and legs prepared in the previous section to the body. They are generally perpendicular to their linked body frames. The calibration pose is shown below:

![Nybble's Calibration State](<../.gitbook/assets/calibration_Nybble (2).png>)

![Bittle's Calibration State](<../.gitbook/assets/zero (2).png>)

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

![](<../.gitbook/assets/assets_bittle_-MTLzoDqllmeUcpCu5jV_-MTM-Wiv6R3xuNmAhgrE_37 (1).png>)

### 2.3 Attach body parts to the servos

#### Install the head

In the calibration state, place the head as close to the central axis as possible and insert its servo shaft into the servo arm of the neck.

<figure><img src="../.gitbook/assets/assets_bittle_cali_head01.jpeg" alt=""><figcaption></figcaption></figure>

Press down on the head so it is firmly attached to the neck.

<figure><img src="../.gitbook/assets/assets_bittle_cali_head02.jpeg" alt=""><figcaption></figcaption></figure>

#### Install the legs&#x20;

Install upper leg and lower leg components to the output teeth of the servos after the Bittle is powered on and in the calibrated neutral position. Please keep the torso, upper leg, and lower leg installed vertically as much as possible, and do not install the lower leg backward, as shown in the picture.&#x20;

<figure><img src="../.gitbook/assets/assets_bittle_cali_leg01.jpeg" alt=""><figcaption></figcaption></figure>

## 3. Fine-tune the calibration using the serial monitor

### 3.1 Joint Control Commands

The command for fine-tuning calibration (refer to the [serial protocol](https://app.gitbook.com/o/-M-_eWZUjFA4usjshHcZ/s/-MQ6a951Q6Jn1Zzt5Ajr-887967055/~/changes/DHad2hALnPq88oSLEuF1/serial-protocol)) is formatted as `cIndex Offset`. Notice that there’s a space between cIndex and Offset. The index number of the robot's joints is shown in the pictures below:

![Nybble](<../.gitbook/assets/jointIndexNybble (1).png>)

![Bittle](../.gitbook/assets/Bittle-joint-Index.png)

For example :

* `c8 6` This means giving the 8th servo an offset of 6 degrees.&#x20;
* `c0 -4` This means giving the 0th servo(the head) an offset of -4 degrees.&#x20;

{% hint style="warning" %}
The resolution of the correction amount is 1 degree; do not use decimals.
{% endhint %}

{% hint style="info" %}
If you find the absolute value of offset is more significant than 9, you are not attaching the limb closest to its zero states. That will decrease the servo's reachable range on either side. Please take off the limb and rotate it by one tooth. It will result in an opposite but smaller offset.&#x20;
{% endhint %}

{% hint style="info" %}
For example, if you have to use -9 as the calibration value, remove the limb, rotate it by one tooth, and then attach it back. The new calibration value should be around 5, i.e., the sum of their absolute values is 14. Avoid rotating the servo shaft during this adjustment.&#x20;
{% endhint %}

Find the best offset that can bring the limb to the zero states.  It's a process of trial and error.

{% hint style="info" %}
For the robotic arm, you can use the serial command "**c-2**" to [auto-calibrate](https://docs.petoi.com/extensible-modules/robot-arm#fine-calibration) the robotic claw joint.
{% endhint %}

After calibration, **remember to type ‘s’ to save the offsets**. Otherwise, they will be forgotten when exiting the calibration state. You can even save every time after you’re done with one servo.&#x20;

### 3.2 Use ‘L’ shaped joint tuner

When watching something, one's observations will change from different perspectives. When measuring length, one always wants to read directly above a referencing ruler.&#x20;

You must keep a parallel perspective when calibrating Bittle. Use the 'L'-shaped joint tuner as a parallel reference to avoid reading errors. Align the tips on the tuner with the center of the screws in the shoulder and knee joints and the little hole on the tip of the foot. Look along the co-axis of the centers. For each leg, calibrate the shoulder servos (index 8\~11) first, then the knee servos(index 12\~15). When calibrating the knee, use the matching triangle windows on both the tuner and shank to ensure parallel alignment.&#x20;

#### Nybble

![](<../.gitbook/assets/Nybble-L (1).jpg>)

#### Bittle

![](../.gitbook/assets/assets_bittle_-MSGw-I0q_j0kHosz8nz_-MSGx1sAobtzY1ucuddF_53.jpeg)

![Align the upper leg first](../.gitbook/assets/calib1.png)

![Pay attention to the reference edges for the lower leg](../.gitbook/assets/calib2.png)

### 3.3 Testing and validation

After calibration, type ‘d’ or ‘kup’ to validate the calibration. This will result in Bittle / Nybble symmetrically moving its limbs between the rest and stand states. &#x20;

You may need to do a few rounds of calibrations to achieve optimal states.

Take Bittle, for example, as follows:

![](<../.gitbook/assets/calibValidation_Bittle (1).png>)

### 3.4 Install the screws

After completing the joint calibration, install the center screws to fix the leg parts and servo gears.

### 3.5 Center of mass

Try to understand how the robot keeps balance even during walking. If you add new components to the robot, distribute its weight symmetrically about the spine. You may also need to slide the battery holder back and forth to find the best balance spot. Because the battery is heavier in the front, you can insert it in a reversed direction to shift the center of mass more toward the back.&#x20;

{% hint style="info" %}
You may need to recalibrate if there's a change to the center of mass.&#x20;
{% endhint %}

Please do not force the robot to add heavy objects, which may cause the servos to sweep or get stuck.
