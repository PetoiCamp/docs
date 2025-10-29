# Setup on NyBoard

The Petoi Web Coding Block can also be used for the robot, which uses the [NyBoard](https://docs.petoi.com/nyboard/overview) and the [WiFi module](../../communication-modules/wifi-esp8266/).

Please take a look at the related section in the Wi-Fi module for instructions on [hardware](../../communication-modules/wifi-esp8266/#id-1.-connection) and software setup ([2.1 Add ESP8266 source to the board manager](../../communication-modules/wifi-esp8266/#id-2.1-add-esp8266-source-to-the-board-manager) and [2.2 Configuration of the Module](../../communication-modules/wifi-esp8266/#id-2.2-configuration-of-the-module)).

## Upload the WiFi Firmware to the WiFi module

Project URL：

[https://github.com/PetoiCamp/OpenCat-Quadruped-Robot/tree/main/ModuleTests/WebCoding8266](https://github.com/PetoiCamp/OpenCat-Quadruped-Robot/tree/main/ModuleTests/WebCoding8266)

There are two files in the project:

* WebCoding8266.ino: Arduino sketch.
* README.md： help document.

Please open the **WebCoding8266.ino** in the Arduino IDE and install the library **WiFiManager**, **WebSockets**, and **ArduinoJson** in the Library Manager:

<figure><img src="../../.gitbook/assets/image (616).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (626).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (625).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (624).png" alt=""><figcaption></figcaption></figure>

Then connect the USB uploader, plugged into the WiFi module, to the computer via the USB data cable. Select the correct serial port and upload the sketch to the ESP8266 WiFi module as follows:

<figure><img src="../../.gitbook/assets/image (617).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (618).png" alt=""><figcaption></figcaption></figure>

After the sketch is uploaded to the WiFi module, open the serial monitor in Arduino IDE. Then, unplug and re-plug the WiFi module into the USB uploader.

<figure><img src="../../.gitbook/assets/image (621).png" alt=""><figcaption></figcaption></figure>

Open your smartphone's WiFi scanner and find an unencrypted access point named "Petoi-AP\*\*\*\*" (shown as in the serial monitor) and connect to it to configure the WiFi parameter of the module, let the WiFi module join the local network, and get a local IP address. For more details, please refer to the " [How to use](../../communication-modules/wifi-esp8266/#how-to-use)" section of the WiFi module.

<figure><img src="../../.gitbook/assets/image (622).png" alt=""><figcaption></figcaption></figure>

After the WiFi module gets the IP address (as shown in the serial monitor above). &#x20;

Unplug the WiFi module from the USB uploader, plug it into the NyBoard, power on the robot, and enter the WiFi module's IP address in the coding block.&#x20;

Now you can use the web coding page to run the program:

<figure><img src="../../.gitbook/assets/image (623).png" alt=""><figcaption></figcaption></figure>

\
