# For BiBoard V1

### Connection

You can solder a 5-pin socket on BiBoard V1 to plug in a Raspberry Pi.

<figure><img src="../../.gitbook/assets/image (564).png" alt=""><figcaption></figcaption></figure>

After plug in the Raspberry Pi board , power on the BiBoard via USB data cable or Battery. Then open the [serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard), and send serial command **XS** to enable the [Serail 2](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.9-swith-working-mode-via-the-serial-commands-optional) working mode.

{% hint style="info" %}
You can also modify the source code (_**OpenCat.h**_) and [upload the sketch for BiBoard](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard) to enable the Serail 2 working mode:

![](<../../.gitbook/assets/image (565).png>)
{% endhint %}

### For Raspberry Pi 5

The serial port on Raspberry Pi 5 is **ttyAMA0**, So you need to modify the source code in _**ardSerial.py**_ as following:

<figure><img src="../../.gitbook/assets/image (566).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}



{% endhint %}

