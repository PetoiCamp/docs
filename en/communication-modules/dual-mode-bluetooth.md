# Dual Mode Bluetooth&#x20;

### Introduction

The Bluetooth module is a standard transparent transmission module, which sends serial port data to devices connected to Bluetooth.

You can wirelessly upload firmware or control the motion of the robot through a Bluetooth connection. You can even control the robot using our smartphone app [Petoi](https://docs.petoi.com/mobile-app/app-guide). We have included our official Bluetooth module in the standard robot kit. As shown below:

![](<../.gitbook/assets/bluetooth (3).png>)

### Connection with NyBoard

The connection between the Bluetooth module and the NyBoard is shown in the figure below, you need to plug the Bluetooth module into the 6-pin socket on the NyBoard. Note the pin order of the Bluetooth module. Once the battery is connected to the NyBoard, press and hold the button on the battery to power the robot. A blinking LED on the Bluetooth module indicates waiting for a connection.

![](<../.gitbook/assets/blue (4).jpg>)

### Connect the dongle with your phone

You need to connect the dongle within the Petoi App, rather than your phone's system Bluetooth settings. On some phones, you need to grant Bluetooth and location services permissions to the app.&#x20;

A more detailed setup can be found in the [mobile app](https://docs.petoi.com/mobile-app/app-guide) section.&#x20;

### Connect the dongle with your computer

In your system's Bluetooth settings, search for a Bluetooth device name started with Petoi or Bittle, and connect. The default PIN for pairing is “0000“ or “1234”. After the pairing is successful, the system will assign a serial port name.

{% hint style="info" %}
On Mac, go to System Preference -> Bluetooth, find a device name started with Petoi or Bittle, and connect.&#x20;
{% endhint %}

![](../.gitbook/assets/MacBlue.JPG)

{% hint style="info" %}
On Windows, add the Bluetooth device in the system settings.
{% endhint %}

![](../.gitbook/assets/bluetooth-config01.png) ![](../.gitbook/assets/bluetooth-config02.png)

![](../.gitbook/assets/bluetooth-config_en03.png)

![](../.gitbook/assets/bluetooth-config04.png) ![](../.gitbook/assets/bluetooth-config-en05.png)

![](../.gitbook/assets/bluetooth-config06.png)

![](<../.gitbook/assets/Device_manager_Bt_en (1).png>)

{% hint style="info" %}
For Win10 users, the system will assign the "incoming" COM port and the "outgoing" COM port to Bluetooth. Please use the "outgoing" COM port. For details, please check in the "More Bluetooth options" of Win10 as below:
{% endhint %}

![](../.gitbook/assets/Bluetooth_port_check01_en.jpg)

![](../.gitbook/assets/Bluetooth_port_check02_en.jpg)

You can then select it under **Tools**->**Port** in the Arduino IDE, using the same method as the USB uploader. After opening the serial monitor, please select: **No line ending**, and the baud rate is set to **115200**.

{% hint style="info" %}
The Bluetooth connection with the computer may occasionally drop. Keeping the serial monitor open can make it more stable. But note it will also occupy the port and block other applications that want to connect.&#x20;
{% endhint %}

### Configure the Bluetooth module

If you want to configure the Bluetooth module, please refer to "JDY-23 AT Command List". Plug the Bluetooth module into the USB adapter debugging interface. As shown below:

![](../.gitbook/assets/configBlue.jpeg)

The commonly used commands are listed below:

| Usage                        | Command                                           | Demo                                                                                            |
| ---------------------------- | ------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Check BT module version      | AT+VER                                            | <p>AT+VER</p><p>>+VER=JDY-23A-V2.21,Bluetooth V3.0+BLE</p><p>（BT module version infomation）</p> |
| Check BT broadcast name      | AT+NAME                                           | <p>AT+NAME</p><p>>+NAME=BITTLE</p>                                                              |
| Change BT broadcast name     | AT+NAME(name)                                     | <p>AT+NAMEPuppy</p><p>>+OK</p><p>AT+NAME</p><p>>+NAME=Puppy</p>                                 |
| Change BT BLE broadcast name | AT+NAM<mark style="color:red;">**B**</mark>(name) | <p>AT+NAMBPuppy</p><p>>+OK</p><p>AT+NAMB</p><p>>+NAMB=Puppy</p>                                 |
| Check serial baud rate       | AT+BAUD                                           | <p>AT+BAUD</p><p>>+BAUD=8 （8 = 115200， 7=57600）</p>                                             |
| Change serial baud rate      | AT+BAUD                                           | <p>AT+BAUD7</p><p>>+OK （Set serial monitor to 57600）</p><p>AT+BAUD</p><p>>+BAUD=7</p>           |

When you use the serial terminal like "Arduino serial monitor" to set JDY-23 with AT commands, you must set "**NL and CR**",  and the baud rate is set to **115200,** or the JDY-23 module will not identify any AT command you send.

![](<../.gitbook/assets/2 (4).png>)

{% hint style="info" %}
If you are a developer, you can use Lightblue or other tools to connect the dongle's BLE service.
{% endhint %}
