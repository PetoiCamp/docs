# For BiBoard V1

### Connection

You can solder a 5-pin socket on BiBoard V1 to plug in a Raspberry Pi.

<figure><img src="../../.gitbook/assets/image (564).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/PANA3446.JPG" alt=""><figcaption></figcaption></figure>

<div align="left"><figure><img src="../../.gitbook/assets/PANA3447.JPG" alt="" width="375"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/PANA3448.JPG" alt="" width="375"><figcaption></figcaption></figure></div>

The white [Pi standoff](https://github.com/PetoiCamp/NonCodeFiles/blob/master/stl/RaspberryPiStandOff/Pi_StandOffRegular.stl) can be 3D printed.

You can 3D print a new [back cover](https://github.com/PetoiCamp/NonCodeFiles/blob/master/stl/BittleCover/Bittle_Cover_with_hole_for_Pi.stl) that fits the Raspberry Pi socket, as follows:

<figure><img src="../../.gitbook/assets/IMG_5885 2.jpeg" alt=""><figcaption></figcaption></figure>

After plug in the Raspberry Pi board , power on the BiBoard via USB data cable or Battery. Then open the [serial monitor](https://docs.petoi.com/arduino-ide/serial-monitor#biboard), and send serial command **XS** to enable the [Serail 2](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard#id-2.9-swith-working-mode-via-the-serial-commands-optional) working mode.

{% hint style="info" %}
You can also modify the source code (_**OpenCat.h**_) and [upload the sketch for BiBoard](https://docs.petoi.com/arduino-ide/upload-sketch-for-biboard) to enable the Serail 2 working mode:

![](<../../.gitbook/assets/image (565).png>)
{% endhint %}

### Serial port name on Pi

{% hint style="info" %}
Generally, the serial port name on Raspberry **Pi 3 and 4** is "**/dev/ttyS0**," and the one on Raspberry **Pi 5** is "**/dev/ttyAMA0**." If the Pi can't open the serial port after it is connected to the mainboard, you can uncomment the line of code as follows to check all the serial ports on the Raspberry Pi in the terminal when the Python script(ardSerial.py) is running.

![](<../../.gitbook/assets/image (570).png>)
{% endhint %}

