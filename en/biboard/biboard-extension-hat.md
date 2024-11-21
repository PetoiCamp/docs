# BiBoard Extension Hat

## Overview

BiBoard Hat V1.0 is the extension board of BiBoard V0, which allows for convenient connection of the voice command and other Grove extensible modules.

## Connection to the BiBoard

<figure><img src="../.gitbook/assets/image (487).png" alt=""><figcaption></figcaption></figure>

## Peripherals

The extension hat has an onboard voice command module and four grove sockets.

* 1x Serial2 port (GPIO16, 17).You must dial the slide switch to UART2 to free it for regular serial communication or GPIO. In that case, the Tx pin (GPIO 17) can be used to write.&#x20;
* 1x I2C port （GPIO21, 22). It's already used by the main program to read sensors. If you use the BiBoard as a regular ESP32 board without Bittle's firmware, they can be configured as regular GPIO pins to read and write.&#x20;
* 2x input-only pins (GPIO 34, 35, 36, 39).

<figure><img src="../.gitbook/assets/image (209).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="93.33333333333331">No.</th><th width="272">Module</th><th>Introducion</th></tr></thead><tbody><tr><td>1</td><td><a href="https://docs.petoi.com/extensible-modules/voice-command-module">Voice command module</a></td><td>A built-in module on the BiBoard</td></tr><tr><td>2</td><td>UART2/Voice command switch</td><td>Connect grove port to UART2 or the Voice command module</td></tr><tr><td>3</td><td>4 Gove sockets</td><td></td></tr><tr><td>4</td><td>Inter-board connectors</td><td>Connect the Grove ports to the top BiBoard</td></tr></tbody></table>

## Introduction to the onboard components

### Voice command module&#x20;

It's equivalent to the independent Grove voice module introduced in the [extensible modules](https://docs.petoi.com/extensible-modules/voice-command-module).&#x20;

### Grove sockets

We adopted the Grove sockets for convenient plug-and-play connections. There are three types of sockets:

<table data-header-hidden><thead><tr><th width="204.33333333333331">Grove Socket</th><th width="239">Pin Number</th><th>Function</th></tr></thead><tbody><tr><td>Grove Socket</td><td>Pin Number</td><td>Function</td></tr><tr><td>G1</td><td>I2C: SDA (GPIO21), SCL (GPIO22)</td><td>I2C with 3.3V logic signal</td></tr><tr><td>G2</td><td>TX (GPIO17), RX (GPIO16)</td><td>UART2 (Serial2 port) with 3.3V logic signal</td></tr><tr><td>G3</td><td>I34, I35</td><td>Analog input; 0-3.3V logic, 5V power</td></tr><tr><td>G4</td><td>I36, I39</td><td>Analog input; 0-3.3V logic, 5V power</td></tr></tbody></table>

{% hint style="info" %}
BiBoard provides the 5V power supply of the grove sockets, while the 5V comes from the battery. So the devices connected to the Grove sockets can only work when connected to the BiBoard and powered by the battery.&#x20;

BiBoard's 3.3V powers the voice module. The 3.3V can be supplied from the USB. So it can work without battery power.&#x20;
{% endhint %}

### UART2 / Voice command switch

UART2 shares the GPIO ports with the voice command module. When the switch is dialed to **VOICE COMMAND**,  the Serial2 port can **NOT** be used. You can dial the slide switch to **UART2** to free it for regular serial communication or GPIO.&#x20;

The function of the switch is shown in the figure below：

<figure><img src="../.gitbook/assets/image (465).png" alt=""><figcaption></figcaption></figure>

