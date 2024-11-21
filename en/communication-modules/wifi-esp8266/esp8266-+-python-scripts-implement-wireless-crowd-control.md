# ESP8266 + Python Scripts Implement wireless crowd control

### Setup environment

Please refer to the instruction of the [WiFi ESP8266](https://docs.petoi.com/communication-modules/wifi-esp8266) and use the [Arduino IDE](https://www.arduino.cc/en/software) to open the sample program (ESP8266WiFiController.ino) to upload the WiFi control firmware for the ESP8266 moudle.

Install Python3, and download [the Python scripts](https://github.com/PetoiCamp/wifi\_control) to control the robot.

### Script introduction

For Python 3.8 and above, the calling syntax is different for the definition of type. This script is compatible with this, but you need to comment and uncomment several corresponding statements in the script according to the version of Python you have installed. For example, the following script supports Python versions below 3.8:

```python
"""
In Python 3.8 and earlier, the name of the collection type is
capitalized, and the type is imported from the 'typing' module
"""
# from typing import Union, Optional             # for Python 3.9+
from typing import Union, Dict, List, Optional   # for Python 3.7
```

This script can control only one robot alone, or control multiple robots at the same time, which can be realized by modifying the following statement in example.py:

```python
# ip = "192.168.0.108"                     # for only one robot
ip = ["192.168.0.110", "192.168.0.108"]    # for multiple robots
```

### How to Use

Refer to [the instruction](https://docs.petoi.com/communication-modules/wifi-esp8266#how-to-use) of the WiFi ESP8266 to assign the IP address to the ESP8266 module and then insert it into the main board of the robot. After the robot is powered on normally, you can use python to run the script example.py to control the robot wirelessly. You can modify the following script statements (modify the content of the list) according to your actual needs to make the robot perform various actions:

```python
cmds = [
        Command.sit, Command.balance, Command.stepping, Command.pee,
        Command.stop
    ]
```

For currently supported skill action commands, please refer to the code file actions.h (in [ESP8266WiFiController](https://github.com/PetoiCamp/OpenCat/tree/main/ModuleTests/ESP8266WiFiController)).
