# Back Touch Sensor

The back touch sensor is a flexible printed circuit (FPC) attached to the inside of the back cover for touch functionality. It can only be plugged into the [**BiBoard V1**](https://docs.petoi.com/biboard/biboard-v1-guide).

## Installation&#x20;

Under normal circumstances, there is no need to remove it. If you wish to detach the back cover FPC from the microcontroller completely, please follow these steps:

* After opening the back cover, please note the relative orientation of the mainboard (BiBoard V1) with respect to the back cover. There is a flip tab on the connector - lift this tab upward. Once the tab is flipped open, the cable beneath it can be fully detached along with the back cover and microcontroller.

Reconnecting the cable to the mainboard is the reverse process: align the cable, ensuring proper orientation, and press it firmly into place.

The installation for Bittle X V2 / Bittle X+Arm and Nybble Q is on the subpage.

## **How to use the back touch mode**

By default, the back touch mode is enabled for the **Bittle X V2**. There are two ways to enable/disable this mode manually:

* In the [serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor), send the serial command "**XB**" to enable; Send the serial command "**Xb**" to disable.
* In the [mobile app](https://docs.petoi.com/mobile-app/controller#create-a-single-command), create a customized command with code "**X66**" to enable; Create a customized command with code "**X98**" to disable.

The touch area layouts for Bittle X V2 / Bittle X+Arm and Nybble are on the subpage.

{% hint style="warning" %}
Usage Tips\
Once the mode is enabled:

1. The robot will not execute new actions if the same spot is touched repeatedly or if two touch points are pressed simultaneously.
2. Wait for the current action to complete before triggering a new command to ensure smooth interaction.
{% endhint %}
