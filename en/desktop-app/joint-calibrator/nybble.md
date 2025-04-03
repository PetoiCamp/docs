# Nybble

The joint calibration interface for Nybble in the Petoi Desktop App is as follows:

<figure><img src="../../.gitbook/assets/image (585).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The servo slider is not available in the light yellow background area in the interface.
{% endhint %}

## Installation

After entering the calibration state, , with all servos rotated to their zero angles, attach the head, tail, and legs prepared in the previous section to the body. They are generally perpendicular to their linked body frames. The calibration pose is shown below:

![Nybble's Calibration State](<../../.gitbook/assets/calibration_Nybble (2).png>)

&#x20;Install the servo-related components according to the picture above and try to ensure that they are perpendicular to each other (the upper leg is perpendicular to the torso, and the lower leg is perpendicular to the upper leg).&#x20;

## Fine-tuning

Use the included L-shaped tool as a reference during calibration. According to the index numbers of the joints shown at the top of the interface (when calibrating the servos, adjust the upper leg first, then adjust the lower leg). Drag the corresponding slider (below the index number), or click the blank part of the slider track to fine-tune the joint to right angles.

![](<../../.gitbook/assets/Nybble-L (2).jpg>)

{% hint style="info" %}
If the offset is more than +/-9 degrees, you need to remove the corresponding leg and reinstall it by rotating one tooth and then dragging the corresponding slider. For example, when it is adjusted to +9 and still not right, remove the corresponding leg and shift one tooth when attaching it. Then, you should get a smaller offset in the opposite direction.&#x20;
{% endhint %}
