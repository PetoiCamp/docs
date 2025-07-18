# For BiBoard V0

### Hardware Connection

Please connect the corresponding pins of the Raspberry Pi and the [BiBoard extension hat](https://docs.petoi.com/biboard/biboard-extension-hat) as follows:

5V power --> 5V

Ground --> GND

GPIO 14 (TXD) --> RX2

GPIO 15 (RXD) --> TX2

Dial the switch on the BiBoard extension hat to the UART2 side.

<figure><img src="../../.gitbook/assets/image (604).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (603).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
To ensure a good connection, you may need to solder the wires.
{% endhint %}

The [software setup](for-biboard-v1.md#software-setup) and [serial port name on Pi](for-biboard-v1.md#serial-port-name-on-pi) are the same as BiBoard V1.
