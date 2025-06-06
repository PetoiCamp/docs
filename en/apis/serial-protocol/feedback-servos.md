# Feedback servos

We introduced the position feedback feature for servos manufactured after March 2024. This feature utilizes the same PWM signal wire to return the servo's actual position, opening up a new control interface for the robot.&#x20;

This feature should be present on all servos with labels or laser marks after May 2024. If the labels are missing, they may still have it. However, the feature is only available on ESP32-based BiBoards (not NyBoards).

To check it, you need to upgrade your robot's firmware. Enter the serial command '**f**' in [Arduino's serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) or the [mobile app's customized button](https://docs.petoi.com/mobile-app/controller#customized-commands). If the monitor keeps printing values that change when you move the servos, they are position feedback. The number of columns corresponds to the number of servos with feedback.&#x20;

The servos have to be all feedback servos to perform the following features:

### Do joint calibration automatically

* Serial Monitor: Send serial command "**c16**". The robot will enter its resting posture. Push the robot down flat onto the table, move its head straight forward, and send a space character(‘ ’) in the serial monitor. The robot will automatically set the calibration values of all its joints. Some joints can still be off and require standard calibration, but it saves most of the time.&#x20;
* Mobile app: Create [a mobile app command](https://docs.petoi.com/mobile-app/controller#create-a-single-command) called "**Auto calibrate**"(customizable) and use the code: `c16` . The robot will enter its resting posture. Push the robot down flat onto the table, and and move its head straight forward.\
  Create [a mobile app command](https://docs.petoi.com/mobile-app/controller#create-a-single-command) called "**Quit**"(customizable) and use the code: "`d`" to continue to the automatic calibration step. The robot will automatically set the calibration values of all its joints. Some joints can still be off and require standard calibration, but it saves most of the time. \


{% embed url="https://youtu.be/gcXt9TIwvOg" %}

### Movement following

* Serial Monitor: Send the serial command "**fF**", then slowly drag one of the legs. The other legs will follow the motion.\
  Send another serial command to quit.
* Mobile app: Create [a mobile app command](https://docs.petoi.com/mobile-app/controller#create-a-single-command) called "**following**"(customizable) and use the code: `fF`\
  Create [a mobile app command](https://docs.petoi.com/mobile-app/controller#create-a-single-command) called "**Quit**"(customizable) and use the code: `d` to quit this mode.

{% embed url="https://youtu.be/xn_gRAWqvWc" %}

### Learn a new skill by rotating servos

* Serial Monitor: Send serial command '**fl**', which means **learning new movements**. Move the legs to your intended starting position, then keep the robot steady for about 2 seconds. The robot will count down and then beep slightly to indicate that it has started recording. It won't record small movements, so you can pause in the middle. After 124 frames, if you enter any character in the serial monitor or stop moving it for over 2 seconds, it will stop recording. Send serial command '**fr**', which means **replay** to recall the taught movement.&#x20;
* Mobile app: Create [a mobile app command](https://docs.petoi.com/mobile-app/controller#create-a-single-command) called "**start learning**"(customizable) and use the code: `fl` which means **learning new movements**. Move the legs to your intended starting position, then keep the robot steady for about 2 seconds. The robot will count down and then beep slightly to indicate that it has started recording. It won't record small movements, so you can pause in the middle. After 124 frames, if you enter any character in the serial monitor or stop moving it for over 2 seconds, it will stop recording. \
  Create [a mobile app command](https://docs.petoi.com/mobile-app/controller#create-a-single-command) called "**replay**"(customizable) and use a space character as the code: `fr`  to which means **replay** to recall the taught movement.&#x20;
*   The skill will also be printed on the [serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard) (as pictured below), and you can import it into [SkillComposer](https://docs.petoi.com/desktop-app/skill-composer#import-the-skill) and the [smartphone app](https://docs.petoi.com/mobile-app/controller#import-your-local-customized-skill-created-by-the-skill-composer).\


    <figure><img src="../../.gitbook/assets/image (593).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://youtu.be/vlHBf_dN4R0" %}

If you wish to write new applications based on the feedback servo, refer to the source codes in OpenCatEsp32/src/espServo.h.
