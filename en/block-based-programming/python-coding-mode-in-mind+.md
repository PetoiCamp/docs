# Python coding mode in Mind+

## Switch to the Python coding mode

If you are familiar with the Petoi coding blocks and Python language, you can change to the **Code** mode in Mind+ as follows:

<figure><img src="../.gitbook/assets/image (417).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (419).png" alt=""><figcaption></figcaption></figure>

The **Code** mode is a Python3 development environment. You can write any Python script in it and call all the API interfaces of the PetoiRobot library imported by Mind+.&#x20;

You can find the PetoiRobot library in the following directory. There are all the [definitions of API interfaces](../apis/python-api.md#available-apis) in the **PetoiRobot.py**

* Windows\
  C:\Users\\{username}\AppData\Local\DFScratch\extensions\petoi-robot-thirdex\python\libraries\PetoiRobot.py
* MacOS\
  /Users/{username}/Library/DFScratch/extensions/petoi-robot-thirdex/python/libraries/PetoiRobot.py

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
