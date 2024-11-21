---
description: How to use python scripts to have fun with the robots
---

# 🐍 Python API

## Preparation

1. &#x20;Install python (version≥ 3.6, such as Anaconda3-5.2.0-Windows-x86\_64.exe)
2. &#x20;Install pyserial library (version 3.5)

## Connect the serial port

When using a [USB adapter](https://docs.petoi.com/communication-modules/usb-downloader-ch340c) to connect to the [NyBoard](https://docs.petoi.com/nyboard/overview) or USB type-C data cable to connect to the [BiBoard](https://docs.petoi.com/biboard/biboard-v0), there should be only one serial port number:

![USB serial port number](<../.gitbook/assets/打开设备管理器03\_En (1).jpg>)

When using the Bluetooth function, there can be two serial port numbers:

![Bluetooth serial port number](../.gitbook/assets/Device\_manager\_Bt\_en.png)

Download a fresh ​OpenCat repository from GitHub:&#x20;

[https://github.com/PetoiCamp/OpenCat](https://github.com/PetoiCamp/OpenCat)

Please utilize GitHub’s version control feature. Otherwise, make sure you download the **WHOLE OpenCat FOLDER** every time.

Open a Terminal (such as Anaconda Prompt) and enter the path where the Python API is located (\*\*\*/OpenCatPythonAPI). Then, run the two example scripts in the folder(_**petoiRobotExample.py**_ and _**ardSerialExample.py**_). The script will automatically identify the serial port number at the beginning and complete the connection.

{% hint style="info" %}
ardSerial.py contains the core communication functions. robot.py is a wrapper module that provides more user-friendly functions. Our Mind+ coding blocks is a graphical UI for this library.
{% endhint %}

## **Run the scripts**

### Run the **petoiRobotExample.py**

```
***\OpenCatPythonAPI>python3 petoiRobotExample.py
```

_**petoiRobotExample.py**_ demonstrates how to call the functions defined in _robot.py_（in the _\*\*\*/OpenCatPythonAPI/PetoiRobot_）

When the system recognizes that there are multiple serial port numbers, the script will automatically identify all serial port numbers that have been connected to the robot (you can send serial commands to multiple robots at the same time). When the script starts running, it will print out the following prompt information:

```python
2024-11-15 15:14:51,357 PetoiRobot.ardSerial - INFO - ardSerial date: Jun. 20, 2024
Mind+ date:  Oct 18, 2023
C:\Users\***\.config\Petoi already exists
C:\Users\***\.config\Petoi\SkillLibrary\Bittle already exists
C:\Users\***\.config\Petoi\SkillLibrary\Nybble already exists
C:\Users\***\.config\Petoi\SkillLibrary\BittleR already exists

*** Available serial ports: ***
COM3
Bittle X
B02_241105
2024-11-15 15:14:54,634 PetoiRobot.ardSerial - INFO - Connect to the serial port list:
2024-11-15 15:14:54,635 PetoiRobot.ardSerial - INFO - COM3
modelName: Bittle
*** The skill names you can call are as follows: ***
*  skillFileName
******************************
2024-11-15 15:15:05,134 PetoiRobot.ardSerial - INFO - close the serial port.
```

### Run  the _**ardSerialExample.py**_

```
***\OpenCatPythonAPI>python3 ardSerialExample.py
```

_**ardSerialExample.py**_ demonstrates how to call the functions defined in _ardSerial.py_（in the _\*\*\*/OpenCatPythonAPI/PetoiRobot_）

The list **testSchedule** in _ardSerialExample.py_ is used to test various serial port commands. Run the following script code to see the execution effect of each serial port command in the list:

```
for task in testSchedule:
    wrapper(task)
```

You can also refer to the content of the **testSchedule** list (in \*\*\*_**/serialMaster/demos/hlw.py**_), write a list of behaviors according to your actual needs, and realize your creativity.  🤩 It was used in a Halloween puppet show.&#x20;

{% embed url="https://youtu.be/53airP7kKd4?si=sYCyAKl4PvurzJDa" %}

<mark style="color:red;">**Note**</mark>: When running the scripts under the path of _**/serialMaster/demos,**_ you must first use the "**cd demos"** command to enter the path where the scripts are located (/serialMaster/demos) and then use the **python3** command to run the script (e.g., **"python3 hlw.py"**)

Explanation of the serial port commands in the list **testSchedule**:

#### **\['kup', 2]**

* 'kup' indicates the command to control Bittle to stand normally&#x20;
* 2 indicates the postponed time after finishing the command in seconds.
* m indicates the command to control the rotation of the joint servo&#x20;
* 0 indicates the index number of joint servo&#x20;
* \-20 indicates the rotation angle (this value is expressed relative to the reference 0 value used after calibration). The unit is in degrees.
* 1.5 indicates the postponed time after finishing the command in seconds. It can be a float number.

#### **\['m', \[0, 45, 0, -45, 0, 45, 0, -45], 2]**

**\['M', \[0, 45, 0, -45, 0, 45, 0, -45], 2]**

The meaning of this example is the same as the previous command.

{% hint style="info" %}
Using the 'm' control command, the index number of joint servo and rotation angle values are stored as ASCII strings.&#x20;

Using the 'M' control command, the index number of joint servo and rotation angle values is stored as a byte string, a byte sequence (binary form).
{% endhint %}

#### **\['d', 2]**

* d indicates the command to put the robot down and shut down the servos
* 2 indicates the postponed time after finishing the command in seconds

#### **\['c', 2]**

* c indicates the command to enter calibration mode&#x20;
* 2 indicates the postponed time after finishing the command in seconds. After these motion commands are completed, the next command will be executed after a 2-second delay.

#### **\['c', \[0, -9], 2]**

* c indicates the command to enter calibration mode&#x20;
* 0 indicates the index number of joint servo&#x20;
* \-9 indicates the rotation angle. The unit is in degrees.
* 2 indicates the postponed time after finishing the command in seconds

Using this format, you can enter the calibration mode to calibrate the angle of a specific joint servo. <mark style="color:red;">**Note**</mark>: If you want the correction value in this command to take effect, you need to enter the "**s"** command after executing this command.&#x20;

The meaning of this example is that the joint servo with serial number 0 rotates -9 degrees. After these motion commands are completed, the next command will be executed after a 2-second delay.

#### **\['m', \[0, -20], 1.5]**

* m indicates the command to control the rotation of the joint servo&#x20;
* 0 indicates the index number of joint servo&#x20;
* \-20 indicates the rotation angle (this angle refers to the origin rather than the additive). The unit is in degrees.
* 1.5 indicates the postponed time after finishing the command in seconds. It can be a float number.

#### **\['m',  \[0, 45, 0, -45, 0, 45, 0, -45], 2]**

Using this format, multiple joint servo rotation commands can be issued in a list. These commands are executed **sequentially**, not simultaneously. The joint angles are treated as ASCII characters so humans can enter them directly.&#x20;

This example means that the joint servo with index number 0 is first rotated to the 45-degree position, then to the -45-degree position, and so on. After these motion commands are completed, the following command will be executed after a 2-second delay.

#### **\['i', \[ 8, -15, 9, -20], 2]**

Using this format, multiple joint servo rotation commands can be issued in a list and executed **AT THE SAME TIME.** The joint angles are treated as **ASCII** characters so humans can enter them directly.&#x20;

The meaning of this example is that the joint servos with index numbers 8 and 9 are rotated to the -15 and -20 degree positions **simultaneously**. After these motion commands are completed, the following command will be executed after a 2-second delay.

#### **\['M', \[8, 50, 9, 50, 10, 50, 11, 50, 0, 0], 3]**

* M indicates the command to rotate multiple joint servos **SEQUENTIALLY**. The angles are encoded as **BINARY** numbers for efficiency.&#x20;
* 8, 9, 10, 11, and 0 indicate the index numbers of joint servos&#x20;
* 50, 50, 50, 50, 0 indicate the rotation angle (this angle refers to the origin rather than additive ). The unit is in degrees&#x20;
* 3 indicates the postponed time after finishing the command in seconds

#### **\['I', \[8, 50, 9, 50, 10, 50, 11, 50, 0, 0], 3]**

The meaning of this example is the same as the previous command.

{% hint style="info" %}
Using the 'i' control command, the index number of the joint servo and rotation angle values are stored as ASCII strings.&#x20;

Using the 'I' (the uppercase of the letter 'i')control command, the index number of the joint servo and rotation angle values are stored as a byte string.
{% endhint %}

#### **\['I', \[20, 0, 0, 0, 0, 0, 0, 0, 45, 45, 45, 45, 36, 36, 36, 36], 5]**

* 'I' indicates the command to control all joint servos to rotate **AT THE SAME TIME** (currently, the command supports 16 degrees of freedom, that is, 16 servos). The angles are encoded as **BINARY** numbers for efficiency.&#x20;
* 20,0,0,0,0,0,0,0,45,45,45,45,36,36,36,36 indicate the rotation angle of each joint servo corresponding to 0-15 (this angle refers to the origin, rather than additive). The unit is in degrees.
* 5 indicates the postponed time after finishing the command. The unit is in seconds.

{% hint style="info" %}
Here, 'l' is the lowercase form of the letter 'L'.
{% endhint %}

#### **\['b', \[10,2], 2]**

* b indicates the command to control the buzzer to beep
* 10 indicates the music tone&#x20;
* 2 indicates the lengths of duration, corresponding to 1/duration second
* 2 indicates the postponed time after completing the tone. The unit is in seconds

#### **\['b', \[0, 1, 14, 8, 14, 8, 21, 8, 21, 8, 23, 8, 23, 8, 21, 4, 19, 8, 19, 8, 18, 8, 18, 8, 16, 8, 16, 8, 14, 4], 3]**

* b indicates the command to control the buzzer to beep&#x20;
* 0, 14, 14, 21... indicate the music tones
* 1, 8, 8, 8 indicates the lengths of duration, corresponding to 1/duration second
* The last '3' indicates the postponed time after playing the music melody. The unit is in seconds.

Using this format, multiple-tone commands can be issued at once, and a simple melody can be played.

The meaning of this example is to play a simple melody and delay 3 seconds after the music melody is played.



ck = \[

&#x20;   \-3, 0, 5, 1,

&#x20;   0, 1, 2,

&#x20;   45,   0,   0,   0,   0,   0,   0,   0,  45,  35,  38,  50, -30, -10,   0, -20,     6, 1, 0, 0,

&#x20;  \-45,   0,   0,   0,   0,   0,   0,   0,  35,  45,  50,  38, -10, -30, -20,   0,     6, 1, 0, 0,

&#x20;    0,   0,   0,   0,   0,   0,   0,   0,  30,  30,  30,  30,  30,  30,  30,  30,     5, 0, 0, 0,

&#x20;       ]

#### **\['K', ck, 1]**

* 'K' indicates the skill data to send to Bittle in real-time
* The skill array is sent to the robot on the go and executed locally on the robot
* You may insert the skills in the skill library or InstinctX.h in this format

For the description of other serial port commands, please refer to [Serial Commands](https://docs.petoi.com/arduino-ide/serial-commands#arduino-ide-as-an-interface).

Please help the robots find their sparks. Wish you have fun! 😍

