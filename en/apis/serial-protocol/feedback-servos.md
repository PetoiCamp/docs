# Feedback servos

We introduced the position feedback feature for servos manufactured after March 2024. This feature utilizes the same PWM signal wire to return the servo's actual position, opening up a new control interface for the robot.&#x20;

All servos with labels or laser marks after May 2024 should have this feature. If the labels are missing, they may still have it. To check it, you need to upgrade your robot's firmware. Enter the serial command 'f' in Arduino's serial monitor or the mobile app's customized button. If it keeps printing values that change when you move the servos, they are position feedback. The count of columns corresponds to the number of servos with feedback.&#x20;

The servos have to be all feedback servos to perform the following features:

1. Enter 'F' in the serial monitor, then slowly drag one of the legs. The other legs will follow the motion.&#x20;
2. &#x20;Enter 'c16'. The robot will enter its resting posture. Push the robot down flat to the table, move its head straight towards the front, and enter any character in the serial monitor. The robot will automatically set the calibration values of all its joints. Some joints can still be off and require standard calibration, but it saves most of the time.&#x20;
3. Enter '**xl**', which means **learning new movements**. Move the legs to your intended starting position, then keep the robot steady for about 2 seconds. The robot will count down and then beep slightly to indicate that it has started recording. It won't record small movements, so you can pause in the middle. After 124 frames, or if you enter any character in the serial monitor or stop moving it for more than 2 seconds, it will stop recording. Enter '**xp**', which means **perform** to recall the taught movement. The skill will also be printed on the serial monitor so that you can import it into the SkillComposer and the smartphone app.

{% embed url="https://youtu.be/vlHBf_dN4R0" %}

\
