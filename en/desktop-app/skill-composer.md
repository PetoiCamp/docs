---
description: >-
  Skill Composer is a skill development tool specially developed by Petoi for
  robots (Bittle, Nybble). Good tools are the prerequisite to the success of a
  job.
---

# Skill Composer

## A Brief Introduction to the Interface

{% embed url="https://www.youtube.com/playlist?list=PLHMFXft_rV6MTs8HMxSOvRAQektoXtaMG" %}

### See [the video tutorials](https://www.youtube.com/playlist?list=PLHMFXft\_rV6MTs8HMxSOvRAQektoXtaMG).

### Connection method

To run the Skill Composer, you can use the following methods to connect the robot's mainboard to the computer:

#### NyBoard

* Wired connection: The kit includes a [**USB Adapter and USB data cable**](https://docs.petoi.com/communication-modules/usb-downloader-ch340c) connecting the robot's mainboard to the computer.
* Wireless connection(Bluetooth)： The kit includes a [**Bluetooth module**](https://docs.petoi.com/communication-modules/dual-mode-bluetooth) connecting the robot's mainboard to the computer.

#### BiBoard

* Wired connection: The kit includes a **USB Type-C data cable** connecting the robot's mainboard to the computer.
* Wireless connection(Bluetooth)： The motherboard's [**built-in Bluetooth**](https://docs.petoi.com/bluetooth-connection) communication module allows you to establish a wireless connection between the robot motherboard and the computer.

### \*\* Download the latest version of the [Petoi Desktop APP](https://github.com/PetoiCamp/OpenCat/releases). \*\*

{% hint style="info" %}
* After downloading the compressed file(.zip), please unzip it first.
* Do **NOT** move the UI.exe to another location in Windows.
{% endhint %}

{% hint style="danger" %}
The robot must be powered by the battery and running the OpenCat 2.0 firmware to be recognized by the Petoi Desktop App. Before opening the software, please install the battery, and long-press the button on the battery to power the Nybble / Bittle.&#x20;
{% endhint %}

Open the [**Petoi Desktop App**](https://github.com/PetoiCamp/OpenCat/releases) (for Windows: UI.exe / for Mac: Petoi Desktop App), click the "**Skill Composer**" button, and open the skill composer interface.&#x20;

![](<../.gitbook/assets/image (382).png>)

### The Skill Composer Interface

#### Nybble

<figure><img src="../.gitbook/assets/image (400).png" alt=""><figcaption></figcaption></figure>

#### Bittle

<figure><img src="../.gitbook/assets/image (319).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Note: Most of the buttons on the interface have a tooltip when the mouse hovers over.
{% endhint %}

### Menu Options

*   Model

    * Nybble
    * Bittle

    Nybble cat and Bittle dog have different back leg joint directions. Their skill data are not interchangeable. Select the correct model before operating the Skill Composer. Otherwise, some joints may conflict with the robot's body.
*   Language

    Currently, there are English, 中文, and Italian. You may contribute to the [translation script](https://github.com/PetoiCamp/OpenCat/blob/main/pyUI/translate.py).
*   Utility

    We will keep adding small gadgets to the utility tab. We have an eye color picker for the Nybble cat's ultrasonic sensor with built-in LEDs. We also have an entry where you can add your creator credential to the skills you create.

### Connection and State Dials

<figure><img src="../.gitbook/assets/image (252).png" alt=""><figcaption></figcaption></figure>

#### Listening / Connect button

Connect the robot to your computer through either the [USB uploader](https://docs.petoi.com/communication-modules/usb-downloader-ch340c#connect-nyboard) or system [Bluetooth settings](https://docs.petoi.com/communication-modules/dual-mode-bluetooth#connection-with-nyboard), then open up this desktop app. It should automatically detect and connect to the robot. The robot's serial port will appear in the following drop-down menu. The button should turn from "<mark style="color:yellow;">**Listening**</mark>" to "<mark style="color:green;">**Connected**</mark>". If the robot fails to connect for the first time, you can click the "<mark style="color:yellow;">**Listening**</mark>" button to disconnect all the ports, then press the "<mark style="color:red;">**Connect**</mark>" button again.

{% hint style="info" %}
Note: The desktop app will keep listening to the serial port and send a handshake signal to the newly added device. If the device responds with a pre-defined signal, it will be recognized as a Petoi device and added to the drop-down menu.
{% endhint %}

#### Servo

The robot's joints will hold position when the force is on. You should **NOT** rotate them by hand. Turning it off can allow you to rotate the robot's joints freely. It's helpful to quickly pose the robot to plan its center of mass for balancing.

#### Gyro

The robot has a gyroscope to detect its body angle and movements. It's used for balancing and roll-recovering. Turning it off can avoid unexpected reactions when rotating the robot.

#### Random

In certain experimental modes (e.g. [RandomMind mode](https://docs.petoi.com/desktop-app/firmware-uploader#click-the-firmware-uploader-button-to-open-the-firmware-uploader-interface)), the robot will move randomly. This button can toggle the behavior on/off.

### Send a serial command

<div align="left">

<figure><img src="../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>

</div>

Like the [serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor), you can enter a [serial command](https://docs.petoi.com/apis/serial-protocol) in the text box and send it to the robot by pressing the **Enter** key or clicking the **Send** button.

### Preset Postures

![](<../.gitbook/assets/image (334).png>)

A few preset static postures move the robot's joints to specific positions. You can use them as a starting point to build your motion sequence. We usually start with the "balance" posture, with the robot standing on all four legs.

You can switch between different postures and observe how the sliders in the **Joint Controller** area update to reflect the changes in joint angles.

### Joint Controller

![](<../.gitbook/assets/image (360).png>)

The angle sliders can show the robot's current joint angles. They can reversely rotate the robot's joints if you change their values. You can drag the slider bar for large angle adjustments or click above or below the slider bar for fine adjustments (by 1 degree). Some joints will have smaller accessible ranges than the sliders. Try to use angles between -125 and 125 degrees. Sending larger angles will increase the response time.

The sliders correspond to the robot joints if you look down at the robot's body with its head pointing forward. Joints closer to the body are closer to the center of the panel. The robot's joints can be mapped to your own body and become your avatar.

{% hint style="info" %}
Note: Some sliders with a light yellow background are disabled for joints that don't exist on specific models.
{% endhint %}

You can control multiple joints by clicking the dial "**+**" or "**-**" on each slider. All sliders with their "**+**" pressed will change by the same increments. Sliders with their "**-**" button pressed will change by the negative increments. The button can be toggled on and off. Click the "<mark style="color:red;">Unbind All</mark>" button to disengage all the joints at once.

You can also control the robot's whole body joints with the sliders in the center panel. You can tune these central sliders to adjust the robot's global orientation and translation. The neutral "**balance**" posture can generate better results than other tilted postures.

| Global Orientation and Translation | Effect                          |
| ---------------------------------- | ------------------------------- |
| Pitch                              | Adjust the pitch angle          |
| Roll                               | Adjust the roll angle           |
| Spinal                             | Move in the spinal direction    |
| Height                             | Raise or lower the robot's body |

### Skill Editor

<figure><img src="../.gitbook/assets/image (295).png" alt=""><figcaption></figcaption></figure>

The previous functions can modify a single posture. The Skill Editor is a stop-motion animation scheduler. You can add, delete, and insert frames of poses and make the robot perform continuous and smooth motions.

Every frame has a row of buttons and input fields as parameters. The first static row contains the column header to indicate the parameters' names.

## Basic Operation

### The Activated Frame

You can click the "<mark style="color:blue;">**=**</mark>" button (**the 2nd item** of a frame) to activate the corresponding frame and move the robot to the frame's posture. The frame will hold all your new edits on the robot's current posture. The "<mark style="color:blue;">**=**</mark>" symbol will become bold, and the button will become larger. The "=" symbol will become a red "!" mark if the current frame is edited. You can click this button to save your edits. Otherwise, the current edits will be abandoned if you click the "<mark style="color:blue;">**=**</mark>" buttons of the other frames.

### Add a Frame

You can click the "<mark style="color:green;">**v**</mark>" button (**the 9th item** of a frame) to add a frame after the current frame and activate it. The new frame will be identical to the **previous activated frame**.&#x20;

{% hint style="info" %}
Note: The new frame doesn't necessarily copy the "<mark style="color:green;">**v**</mark>" button's frame.
{% endhint %}

### Insert a Frame

You don't always add a new frame after the last frame. You can click the "<mark style="color:green;">**v**</mark>" button (**the 9th item** of a frame) of any intermediate frames to insert a new frame below the "<mark style="color:green;">**v**</mark>" button. The new frame carries information identical to the previously **activated frame**.

### Mirror a frame

You can mirror the activated frame's posture by clicking the ">|<" button.

### Delete a Frame

You can click the "<mark style="color:red;">**<**</mark>" button (**the 8th item** of a frame) to delete the current frame holding the button. All the following frames will shift up. If **the activated frame** is deleted, its preceding frame will be activated. If **the activated frame** is the first frame and is deleted, its following frame will be activated.

### Add a Note to a Frame

You may lose track of what each frame holds with multiple edits to the frame list. Switching to individual frames can be time-consuming. We provide a "**Note**" field (**the 7th item** of a frame) where you can add short keywords to identify the frames. By default, a random animal name will be added to a frame when created.

<figure><img src="../.gitbook/assets/image (385).png" alt=""><figcaption></figcaption></figure>

### Bound joints and passed-through edits

If a joint's angle is the same in the current frame and the next frame, editing and saving its angle will also update the angles in the following frames until the angle differs. For example, if joint 8's angles are 4,4,4,4,6,7 in all the frames, changing the angle in the second frame to 8 will update the sequence to 4,8,8,8,6,7.

### Play the Skill Sequence

Besides manually clicking the "<mark style="color:blue;">**=**</mark>" button (**the 2nd item** of a frame) to view the single posture, you can click the "<mark style="color:green;">**Play**</mark>" button to show the postures in order starting from **the activated frame**. During playing time, the button's text becomes "<mark style="color:red;">**Stop**</mark>" to allow you to stop in the middle.

### Export the skill

After clicking the "<mark style="color:blue;">**Export**</mark>" button, you can choose a location and filename to save the skill (from **the activated frame**. If **the activated frame** is the last action frame, all action frames in the action frame list are exported) as a text file. You can cancel the savings to skip. The desktop app will still send the skill to the robot for real-time performance. And you can call the last exported skill by the serial token "**T**." There are two ways:

* Open [the serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor) and input the serial command "**T**."
* Open [the mobile app](https://docs.petoi.com/mobile-app/app-guide), use the [Create Command](https://docs.petoi.com/mobile-app/controller#create-a-single-command) function, and enter the serial port command "**T**" in the **Code** text box.

{% hint style="info" %}
The last skill exported by the Skill Composer is stored in temporary memory. It can stay after the power is off and rebooted but **will be overwritten by a new export**.&#x20;

From version **1.1.3**, When exporting a skill, the desktop app automatically saves it to /Users/{username}/.config/Petoi/SkillLibrary/. Note the .config is a hidden directory but can be visited in the terminal or through a specific view setting. Therefore, you can easily manage the skills in [Mind+](https://docs.petoi.com/block-based-programming/petoi-coding-blocks#perform-the-skill-in-the-file).

The [Skill Creation](../applications/skill-creation.md) chapter focuses on the code and data structure so that you can integrate any number of new skills into the source code. The skill data array in the exported text file (\*.txt or \*.md) content _can be copied and pasted into the Instinct_\*\*.h file to be used as a skill array.
{% endhint %}

* [Export the skill ](../mobile-app/controller.md#import-new-skills-as-a-customized-button)as a customized button in the mobile app. It can be **permanent** even if you create multiple skills.&#x20;

### Import the Skill

You will see a pop-up window after clicking the <mark style="color:blue;">"Import"</mark> button. It allows you to copy-paste a skill data array in the text editor or import an existing skill file you or other users created. You can find example skill data in OpenCat/src/**InstinctBittle.h** or **InstinctNybble.h**. A complete skill format should include the "**{ }**" pair and the numbers between them. Only **the first one** will be imported if there are multiple skill arrays. The importer will do some simple format checks.

{% hint style="info" %}
[The SkillLibrary folder](https://github.com/PetoiCamp/OpenCat/tree/main/SkillLibrary) in Github is a collection of new skills of the OpenCat robot, which can be used for your reference (after downloading, use the import function to save a single skill to the robot's memory, and then use the [play](skill-composer.md#play-the-skill-sequence) or [export](skill-composer.md#export-the-skill) to view the specific effect).&#x20;

You are welcome to share your new skills by sending merge requests to this folder.
{% endhint %}

### Reset the Skill Editor

You can use the "<mark style="color:red;">**Restart**</mark>" button to clear the Skill Editor panel and start over.

## Advanced operation

### Set up Action Frame Loops

If you need some consecutive action frames in [the action frame list](skill-composer.md#skill-editor) to run multiple times in a loop, you can first enter the number of loops in the **Repeat** text box above [the action frame list](skill-composer.md#skill-editor) (on the **left side** of the label "**Set**"), and then use the left mouse button to select them in turn, The index numbers (**the 1st item** of a frame) of the **first** and **last** two frames of the continuous action frame that want to achieve cyclic motion (the index number button will appear in a recessed state after selection), as shown in the following figure:

<figure><img src="../.gitbook/assets/image (215).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you enter **-1** in the **Repeat** text box, the looping action frames will keep looping forever unless you press the reset button on the main board of the robot.
{% endhint %}

### Set Movement Speed

In [the action frame list](skill-composer.md#skill-editor), you can set the running speed of each frame of action (**the 3rd item** of a frame). There are the following 9 options for you to choose from (speed up the running speed in the order of numerical value):

1，2，4，8，12，16，32，48，max

{% hint style="info" %}
Note:

* In the options box, you can also enter any integer value in the range of 0\~125 (0 means max).
* By clicking the "<mark style="color:green;">**Play**</mark>" button in the "**Skill Editor**" area, you can **NOT** see the real running speed effect of the action; only after clicking the "<mark style="color:blue;">**Export**</mark>" button will you see the real running speed effect.
* Moving at the fastest speed for a long time will cause damage to the servo, so it is generally recommended **NOT** to set it to "**max**".
* When the "<mark style="color:green;">**Gyro**</mark>" button in the "[**State Dials**](skill-composer.md#connection-and-state-dials)" area is turned on (the font color is <mark style="color:green;">green</mark>), after adjusting the joint angle value in the action frame or the running speed of the action frame, [<mark style="color:green;">**play**</mark>](skill-composer.md#play-the-skill-sequence) it to view the debugging effect, or [<mark style="color:blue;">**export**</mark>](skill-composer.md#export-the-skill) the action behavior, the robot It will try to maintain its own body balance in real-time, so it may be seen that when the robot is doing preset actions (especially when running relatively violent actions), its body will shake back and forth or even overturn, and the robot will automatically recover. Action may disrupt your original operation steps. Therefore, it is recommended that you click the "<mark style="color:green;">**Gyro**</mark>" button when designing the action to turn off the gyroscope (the font color changes to <mark style="color:red;">red</mark>), and the robot will not perform balance feedback actions in real-time. When turning on the gyroscope, click the "<mark style="color:red;">**Gyro**</mark>" button again.
{% endhint %}

### Set Delay

In [the action frame list](skill-composer.md#skill-editor), the "**Delay**" option (**the 6th item** of a frame) in each action frame indicates how long the robot delays before doing the next frame of action after the action of this frame is completed.

There are **17** presets for you to choose from: 0，50，100，200，300，400，500，600，700，800，900，1000，2000，3000，4000，5000，6000.

Of course, you can also enter any integer value in the range of 0\~6000 in the "**Delay**" option box. The unit is milliseconds (ms).

### Set Trigger and Angle

<figure><img src="../.gitbook/assets/trigger (1).jpeg" alt=""><figcaption></figcaption></figure>

The "**Trigger**" option (**the 4th item** of a frame) in the action frame is used to set the body rotation direction when the robot triggers the next action frame. There are the following **5** setting options:

* **None** means that there is no trigger and the angle condition is set
* **Pitch** means the robot body rotates nose-down
* **-Pitch** means the robot body rotates nose-up
* **Roll** means that the robot body rolls to its left side (counter-clockwise when looking from the tail)
* **-Roll** means the robot body rolls to its right side (clockwise when looking from the tail)

The "**Angle**" option (**the 5th item** of a frame) is defined with reference to the angle of the polar coordinate system. As shown in the figure above, when the body is horizontal, the angle of the polar coordinate axis is 0 degrees. If the polar coordinate axis rotates counterclockwise, the angle is positive and gradually increases. The angle setting range is an integer value between **-125\~125**.

When a specific trigger and angle are set in the action frame, the next frame of action will be triggered only when the robot rotates over the trigger angle in the trigger's direction. If a delay time is also set in this action frame, it will delay an additional time after the trigger condition is met before moving to the next frame.

When creating actions related to the rotation of the robot body (such as backflips, doing high bar exercises, etc.), it's vital to trigger the motion at a certain body angle whose timing can be hard to estimate, and it may also change during the motion. We can use the gyroscope to monitor the rotation angle of the robot body in real-time, so that the robot can trigger the joint servo at the exact time of the trigger event.&#x20;

### Export Mirror Actions

When exporting the action frames, if you want to mirror all the action frames in [the action frame list](skill-composer.md#skill-editor) (the robot's left and right side joints will be exchanged, as if seen in a mirror), you can first click the "[<mark style="color:blue;">**MirrorAll**</mark>](skill-composer.md#skill-editor)" button, and then click the "[**Export**](skill-composer.md#export-the-skill)" button. If you want to cancel the mirrored export, you can deselect the "<mark style="color:blue;">**MirrorAll**</mark>" button.

### Behavior and Gait Options

Before exporting action frames, select the "**Behavior**/**Gait**" options in the "[**Skill Editor**](skill-composer.md#skill-editor)" area as "<mark style="color:blue;">**Behavior**</mark>". After clicking the "[<mark style="color:blue;">**Export**</mark>](skill-composer.md#export-the-skill)" button, the program will run on the robot and automatically interpolate between these action frames to make the robot move smoothly. All action frames will execute for only one round.

If the "<mark style="color:blue;">**Gait**</mark>" option is selected before you click the "[<mark style="color:blue;">**Export**</mark>](skill-composer.md#export-the-skill)" button, the robot will continue to execute in a loop, and each action frame will run at the fastest speed; **NO** interpolation between action frames will be added. The motion can be quite brutal. Therefore, it is recommended that beginners always use the "**Behavior**" option to develop new skills.

When importing some pre-built skill array, the desktop app will automatically select the "**Behavior**/**Gait**" option according to the data format. The frames will be loaded into the frame editor, and the robot will automatically move to the first frame's posture.

{% hint style="info" %}
After sending a command, the desktop app will wait for the robot to return a confirmation token. It may freeze if the robot's program halts or the connection is lost. You don't need to close the desktop app and lose the unsaved action frames but press the "**reset**" button on the robot's main board to break the app's waiting loop. If the program still does not respond, you can click a posture button in the "[**Preset Postures**](skill-composer.md#preset-postures)" area or try to reconnect the robot using the "Connect/Listening" button.
{% endhint %}

### Simultaneous Control of Multiple Robots

The desktop app supports the connection of multiple robots through their own [serial ports](https://docs.petoi.com/communication-modules/usb-downloader-ch340c#connect-nyboard) (such as [the Bluetooth communication module](https://docs.petoi.com/communication-modules/dual-mode-bluetooth#connection-with-nyboard)) to achieve simultaneous control of multiple robots. After a physical connection, the app can only recognize a serial port as a robot. So after the robot is powered on normally:

* USB

First, connect the USB uploader to the main board of the robot, and then use the data cable to connect it to the computer's USB interface.

* Bluetooth

First, plug the Bluetooth module into the main board of the robot (no need for the ESP32-based board) and pair the board with the computer's Bluetooth setting interface. The desktop app will keep detecting if there is a new serial port connection. When multiple serial ports are successfully connected, the serial port option button in the "[**State Dials**](skill-composer.md#connection-and-state-dials)" area will change to "<mark style="color:blue;">**All**</mark>." Click the drop-down list to view all serial ports that have been successfully connected. All robots will be synchronized in real-time in this way. You can also select any one of the serial ports to control the corresponding robot.&#x20;

If you unplug a USB serial port on the computer (or disconnect the Bluetooth module in the Bluetooth setting interface), the corresponding serial port will be removed from the drop-down list in real-time.

If you unplug all USB serial ports (disconnect all Bluetooth modules), the serial port option button displays "**None**," and the left button displays "<mark style="color:yellow;">**Listening**</mark>." The desktop app still automatically detects whether there is a serial port connection. When a robot is reconnected to the computer through the serial port, the button on the left side of the drop-down menu will display "<mark style="color:green;">**Connected**</mark>." The corresponding serial port name is displayed in the serial port option button.

If you want the desktop app to stop detecting serial connections, click the "<mark style="color:green;">**Connected**</mark>" / "<mark style="color:yellow;">**Listening**</mark>" button. The text in the button will change to "<mark style="color:red;">**Connect**</mark>," and all serial connections will be disconnected. Click the "<mark style="color:red;">**Connect**</mark>" button again to restart the real-time detection function.

## Professional extensions

You can modify the source code of the Skill Composer in **OpenCat/pyUI/SkillComposer.py**.&#x20;

## Teach by pulling legs using the Feedback servo

{% hint style="warning" %}
This function requires the servos after March 2024, the BiBoard, and the latest firmware.&#x20;
{% endhint %}

We have added the position feedback feature to recent batches of Petoi servos. The servo can reply to a specific PWM pulse (3500µs) with its current position in the form of pulse length. The central controller (BiBoard) can convert the signal to angles for more interaction.

{% embed url="https://youtu.be/vlHBf_dN4R0" %}

First, send the robot a serial command "xl" to start the learning process. In the demo, it's triggered by our customized voice command. The robot's servo driver will switch to reading mode. Joint jigs can occur during this transition. Organize the robot's legs and then hold it still. The learning starts when no significant movements are detected.

Pull the legs, and the movement will be recorded. Stopping in the middle is okay because identical postures will be skipped. The recording will stop if the maximal frame is reached or the robot's joints are not moved for 2 seconds.

The recorded command can be called by "xp" to replay. The skill data is also printed to the screen so you can save it and import it into the Skill Composer or other OpenCat interfaces.

The control logic is defined in **OpenCatEsp32/src/reaction.h** and **motion.h**.
