# Robot Arm

Bittle can be equipped with a robotic arm, which we will call it Bittle X+Arm. This robotic arm gripper has more functions than Bittle and can perform more complex skills, such as grabbing objects for display or moving them to different places.

{% hint style="danger" %}
When the robot arm is in motion, please do not put your hands between the robot claws to avoid being pinched.
{% endhint %}

<figure><img src="../../.gitbook/assets/001.png" alt=""><figcaption></figcaption></figure>

## Installation

You must use the neck part with a J-hook (as pictured below) to use this robot arm.

<figure><img src="../../.gitbook/assets/image (594).png" alt=""><figcaption></figcaption></figure>

This robot arm is already fully assembled. You need to install the servo with the neck structure in the servo slot with two M2\*5 self-tapping screws.

<figure><img src="../../.gitbook/assets/Neck.jpeg" alt=""><figcaption></figcaption></figure>

## Upload the firmware

In the [**Petoi Desktop App**](https://docs.petoi.com/desktop-app/introduction), choose the model **Bittle X+Arm**, then click the **Firmware Uploader** button to upload the firmware for the robot with an arm.

<div align="left"><figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/BittleX+Arm_FU01.jpeg" alt=""><figcaption></figcaption></figure></div>

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Joint Calibration

The robot arm must be finely calibrated to make it more precise when performing actions and to prevent the robot claw from jamming and overheating.

You can use the [**Petoi Desktop App**](https://docs.petoi.com/desktop-app/joint-calibrator) to calibrate it.

### Prepare for calibration <a href="#prepare-for-calibration" id="prepare-for-calibration"></a>

You must connect the motherboard to the computer via a USB data cable or [Bluetooth](https://docs.petoi.com/bluetooth-connection#for-biboard) wireless.

Then, install the battery and long-press the button on the battery to power the robot.

### Enter the calibration state

After the robot is powered on, there are two methods to enter the calibration state:

*   It will enter the calibration state automatically when you click the **Joint Calibrator** button.\
    \


    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Click the **Calibrate** button in the calibrator interface.

**BiBoard\_V1\_\***

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
BiBoard\_V0\_\*\
![](<../../.gitbook/assets/image (4) (1) (1).png>)
{% endhint %}

{% hint style="info" %}
The servo slider is not available in the interface's light yellow background area.
{% endhint %}

### Fine calibration

Click the corresponding slider track of the robot arm and adjust the robot arm by calibrating the posture as shown below：

<figure><img src="../../.gitbook/assets/rotationDirections.jpeg" alt=""><figcaption></figcaption></figure>

The joint index corresponding to the claw is 2. It can be auto-calibrated by pressing the **Auto** button or inputting the serial command "**c-2**" on the [serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) of Arduino IDE. You can also manually click the corresponding slider track and adjust the gear on the servo output shaft to the position shown in the figure above.

## How to use

### Voice command

The robot program defaults to voice mode. Before controlling the robotic arm with voice commands, you must say "**Start learning**" to activate the custom voice command mode. Then, follow the voice prompts to [record your voice commands](https://docs.petoi.com/extensible-modules/voice-command-module#record-customized-voice-commands) in the following order to call predefined skill actions:

1. "**Learn skill**"
2. "**Play skill**"
3. "**Follow**"
4. "**Pick up**"
5. "**Put it down**"
6. "**Hunt**"
7. "**Show off the object**"
8. "**Put away**"
9. "**Throw away**"
10. "**Shoot**"

Once you have finished recording your voice commands, say "**Stop learning**" to exit the custom voice command mode.

The meaning of the voice commands:

"**Learn skill**": This command de-energizes the robot servos, enabling continuous manipulation of the robot's body pose for skill motion capture.

"**Play skill**": This command allows for the playback of the captured skill motion.

"**Follow**": This command de-energizes the robot servos, enabling you to manipulate any leg, with the other legs copying its motion.

"**Pick up**": To pick up the object.

&#x20;"**Put it down**": To put the object down.

"**Hunt**": To grab the object quickly.

"**Show off the object**": To show off the object.

"**Put away**": To put away the object.

"**Throw away**": To throw the object aside.

&#x20;"**Shoot**":  To throw the object forward.

### Mobile app

Please install the latest version of the [mobile app](https://docs.petoi.com/mobile-app/introduction) and download the robotic arm skill config file (as below) , and save it on your smartphone:

{% file src="../../.gitbook/assets/RoboticArmSkills_EN.json" %}

Then you can press the Import commands button in the menu list (as following) to import the skills via config file (.json) .

<figure><img src="../../.gitbook/assets/image (606).png" alt=""><figcaption></figcaption></figure>

### Mind+

You can use the **Perform robot arm skill** block in the [**Petoi Coding Blocks**](https://docs.petoi.com/block-based-programming/petoi-coding-blocks) to do some pre-defined skills.

For example:

<figure><img src="../../.gitbook/assets/image (533).png" alt=""><figcaption></figcaption></figure>

### Serial command

After connecting the motherboard to the computer via a USB data cable or [Bluetooth](https://docs.petoi.com/bluetooth-connection#for-biboard) wireless, you can use the following commands in the Arduino IDE [serial monitor.](https://docs.petoi.com/arduino-ide/serial-monitor#biboard)

```cpp
  "kpickD",      // Pick up the object under the robotic arm.
  "kpickF",      // Pick up the object in front of the robotic arm.
  "kpickL",      // Pick up the object to the left of the robotic arm.
  "kpickR",      // Pick up the object to the right of the robotic arm.
  "kputD",       // Place the grasped object under the robotic arm.
  "kputF",       // Place the grasped object in front of the robotic arm.
  "kputL",       // Place the grasped object to the left of the robotic arm.
  "kputR",       // Place the grasped object to the right of the robotic arm.
  "klaunch",     // Launch the grasped object forward.
  "ktossF",      // Throw the grasped object forward.
  "ktossL",      // Throw the grasped object to the left.
  "ktossR",      // Throw the grasped object to the right.
  "khunt",       // Quickly grasp the object in front.
  "kshowOff",    // Show the grasped object.
  "kclap",       // Make a clapping motion with the robotic gripper.
```

### Skill and directional combinations

| Skill Name | Front | Left   | Right | Down           |
| ---------- | ----- | ------ | ----- | -------------- |
| pick       | pickF |  pickL | pickR | pickD          |
| drop       | dropF | dropL  | dropR | dropD          |
| put        | putF  | putL   | putR  | putD           |
| toss       | tossF | tossL  | tossR | tossD = launch |
| hunt       |       |        |       |                |
| showOff    |       |        |       |                |
| clap       |       |        |       |                |

{% hint style="info" %}
**Note**:\
When using the serial port commands in the table, you need to prepend a lowercase English letter "**k**", for example, "**kpick**", "**kpickF**".\
When using serial port commands that do not end with a directional character ("F", "L", "R", "D"), such as "**kpick**", the robot will randomly execute any one of the four directional actions corresponding to this skill.
{% endhint %}

## Advanced Usage

### Create new skill

You can use the [Skill Composer](https://docs.petoi.com/desktop-app/skill-composer) in the Petoi Desktop App to create new skills for the robot arm and [export](https://docs.petoi.com/desktop-app/skill-composer#export-the-skill) them to the mobile app, the [Mind+ program](https://docs.petoi.com/block-based-programming/petoi-coding-blocks#perform-the-skill-in-the-file),  or the [source code](https://docs.petoi.com/applications/skill-creation).

<figure><img src="../../.gitbook/assets/image (530).png" alt=""><figcaption></figcaption></figure>

### Extensional application

This robot arm can be used in combination with other sensors. The installation method is shown in the figure below. e.g., adding the [Grove Vision AI V2](https://docs.petoi.com/extensible-modules/advanced-development-and-application-of-ai-vision-modules) module:

<figure><img src="../../.gitbook/assets/image (531).png" alt=""><figcaption></figcaption></figure>

The source code also needs to be modified. The sample demo code is being written, so stay tuned.

