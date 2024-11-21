# Serial Monitor

## NyBoard

There are two ways to establish a serial port connection：

### Connect the USB Adapter

Connect the USB adapter to the mainboard and select the correct serial port. Refer to the [Connect NyBoard](https://docs.petoi.com/communication-modules/usb-downloader-ch340c#connect-nyboard) section in the USB Adapter(Uploader) Module for specific steps.

### Connect Bluetooth module(optional)

Please refer to the [Connect NyBoard section](https://docs.petoi.com/communication-modules/dual-mode-bluetooth#connection-with-nyboard) in the Dual-Mode Bluetooth Module for the specific steps.

{% hint style="warning" %}
On Mac, the Bluetooth may lose connection after several uploads. In that case, delete the connection and reconnect to resume the functionality.
{% endhint %}

{% hint style="warning" %}
The Bluetooth dongle is not included in the kit sold by Seeed Studio or its partners. Please write to support@petoi.com for more information.&#x20;
{% endhint %}

### Setup steps in the Arduino IDE

1. Select the port in the [Arduino IDE](https://www.arduino.cc/en/software)(recommend version **1.8.19**).

![](<../.gitbook/assets/USBserial (3).png>)

{% hint style="info" %}
If you can't determine which port is correct, unplug and re-plug the USB data cable on the computer side and check the difference in the _**Tools**_ menu.

You may install the [drivers](https://docs.petoi.com/technical-support/useful-tools#driver) if no new port is shown in the menu list.
{% endhint %}

2. Open the serial monitor.

You can choose the "Serial Monitor" in the _**Tools**_ menu bar or click the ![](<../.gitbook/assets/image (203).png>) button to open the serial monitor window:

![](<../.gitbook/assets/Open serial monitor01.png>) ![](<../.gitbook/assets/Open serial monitor.png>)

3. Config the parameter of the serial monitor.

In the serial monitor, set "_**No line ending**_" and the baud rate to _**115200**_.&#x20;

![](<../.gitbook/assets/monitor (2).png>)

With the USB adapter / Bluetooth module connecting NyBoard and computer, you have the ultimate interface - **Serial Monitor** to communicate with NyBoard and change every byte on it(via sending the serial commands based on the [serial protocol](https://app.gitbook.com/o/-M-\_eWZUjFA4usjshHcZ/s/-MQ6a951Q6Jn1Zzt5Ajr-887967055/\~/changes/DHad2hALnPq88oSLEuF1/serial-protocol)).

## BiBoard

There are two ways to establish a serial port connection：

* [Connect the mainboard](https://docs.petoi.com/upload-firmware#biboard) and computer using a USB type-C data cable(you should use the original one in the kit).&#x20;
* Connect the mainboard with a [computer ](https://docs.petoi.com/bluetooth-connection#for-biboard)/ [mobile app](https://docs.petoi.com/mobile-app/introduction#connect-to-your-robot) via Bluetooth.

The setup steps in the Arduino IDE are identical to those [in Ablove](serial-monitor.md#setup-steps-in-the-arduino-ide).

