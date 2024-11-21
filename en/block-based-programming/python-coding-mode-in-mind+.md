# Python coding mode in Mind+

If you are familiar with the Petoi coding blocks and Python language, you can change to the **Code** mode in Mind+ as follows:

<figure><img src="../.gitbook/assets/image (417).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (419).png" alt=""><figcaption></figcaption></figure>

The **Code** mode is a Python3 development environment. You can write any Python script in it and call all the API interfaces of the PetoiRobot library imported by Mind+.&#x20;

You can find the PetoiRobot library in the following directory, there are all the definitions of API interfaces in the **PetoiRobot.py**

* Windows\
  C:\Users\\{username}\AppData\Local\DFScratch\extensions\petoi-robot-thirdex\python\libraries\PetoiRobot.py
* MacOS\
  /Users/{username}/Library/DFScratch/extensions/petoi-robot-thirdex/python/libraries/PetoiRobot.py

Below are the supported functions in the library. You may refer to the auto-generated Python code in the **Blocks** mode to learn its formats.

```python
# use to print debug information
def printH(head, value)

# deactivate the Gyro
def deacGyro()

# get the current angle list of all joints
def getAngleList()
    return angleList

# get the current angle value of a joint 
def getCurAng(index)

# creat an absolut value list
def absValList(num1, num2)

# rotate angle from relative value to absolute value
# creat an offset value list
def relativeValList(index, symbol, angle)

# rotate the joints sequentially or simultaneously
def rotateJoints(token, var, delayTime)

# play tones
def play(token, var, delayTime)

# encode the character to bytes
def encode(in_str, encoding='utf-8')
 
def printSkillFileName()

# open the serial port 
def openPort(port)

# auto connect serial ports
def autoConnect()

# send a short skill string
def sendSkillStr(skillStr, delayTime)

def loadSkill(fileName, delayTime):

# send a command string
def sendCmdStr(cmdStr, delayTime)

def sendLongCmd(token, var, delayTime)

# get the analog value of a pin
def readAnalogValue(pin)

# get the digital value of a pin
def readDigitalValue(pin)

# set the analog value of a pin
def writeAnalogValue(pin, val)
 
# set the digital value of a pin
def writeDigitalValue(pin, val)

# close the serial port
def closePort()
```

Here is a sample code :

```python
# The code starts here
from PetoiRobot import *    # must import the PetoiRobot library

# enter the code below
# auto connect serial ports
autoConnect()

# call the APIs to control the Petoi robot
sendSkillStr('ksit', 0.5)
sendCmdStr('T', 0.5)
loadSkill("skillFileName", 0.2)

# close the serial port
closePort()
```

You can also copy the code in the **Auto Generate** area in the **Blocks** mode and then paste it into the code file in the **Code** mode. Then you can edit and run the code.
