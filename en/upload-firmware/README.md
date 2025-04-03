# Upload Firmware

## Connect to the mainboard

You must use the USB data cable to do firmware uploading.

{% hint style="warning" %}
* Some USB cables are just for charging and do not have data transfer capability. Using the original data cable in the kit is better for making the uploading successful. &#x20;
* Some new laptops only have USB-C ports, so users use a hub to connect standard USB-B to their computers. However, the intervening hubs prevent the app from recognizing the serial port. The solution was to connect the USB-C cable DIRECTLY to the computer using EITHER a USB-C to USB-C cable OR a tiny C to B adaptor (not a hub).
{% endhint %}

## Upload the firmware

There are two methods to Upload the firmware to the robot:

* The simplest method is to use the [**Petoi Desktop App**](https://docs.petoi.com/desktop-app/introduction). No programming is involved. You can play with some preset modes.&#x20;
* If you have some programming experience, you can use the [**Arduino IDE**](https://www.arduino.cc/en/software)[.](https://www.arduino.cc/en/software) You will be able to modify the open-source codes for your new projects.&#x20;
  * If you are using NyBoard, please refer to [**Upload Sketch for NyBoard**](https://docs.petoi.com/arduino-ide/upload-sketch-for-nyboard).
  * If you are using BiBoard, please refer to [**Upload Sketch for BiBoard**](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard).

{% hint style="danger" %}
If you have a NyBoard(with Bittle and Nybble), we highly recommend using the green USB programmer to upload the firmware. The Bluetooth dongle is not as stable and may cause the mainboard's bootloader to crash if interrupted in the middle.&#x20;

For BiBoard(with Bittile X), the USB/Bluetooth connections are built on the board already.
{% endhint %}
