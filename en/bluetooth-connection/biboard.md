# BiBoard

## Connection steps

1. Power on the mainboard via the battery (plug in the battery to the mainboard, and long-press the battery button > 3 seconds); after powering on, the mainboard's <mark style="color:blue;">blue</mark> LED and <mark style="color:yellow;">yellow</mark> LED should be on.
2.  For **Windows**, Open the Bluetooth & other devices  setting page, and turn on the Bluetooth button as follows:<br>

    <figure><img src="../.gitbook/assets/image (502).png" alt=""><figcaption></figcaption></figure>
3.  Add the BiBoard Bluetooth for the first time as follows:<br>

    <figure><img src="../.gitbook/assets/image (503).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../.gitbook/assets/image (504).png" alt=""><figcaption></figcaption></figure>

    Select the one with the name <mark style="color:blue;">**Bittle\*\*\_BLE**</mark>:

<figure><img src="../.gitbook/assets/image (505).png" alt=""><figcaption></figcaption></figure>

After paired successfully, it shows：

<figure><img src="../.gitbook/assets/image (506).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (507).png" alt=""><figcaption><p>Windows 10</p></figcaption></figure>

{% hint style="info" %}
For **Windows 11**, after the initial Bluetooth pairing, the device might show “not connected” as follows. However, as long as the robot is not rebooted after the pairing, the associated COM port is still registered in the system. You can connect to the serial port within the Petoi application, such as the Desktop app and the Mind+.

<img src="../.gitbook/assets/not_connected.png" alt="" data-size="original">
{% endhint %}

Check the **outgoing** serial port, which we will use later in the Mind+ or Petoi Desktop App in the **More Bluetooth options**:

<figure><img src="../.gitbook/assets/image (508).png" alt=""><figcaption><p>More Bluetooth options</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (509).png" alt=""><figcaption><p>Bluetooth Settings</p></figcaption></figure>

{% hint style="info" %}
If you have already added the BiBoard Bluetooth before, after powering off and powering on the robot, you should remove both of the two devices in the list as follows:

![](<../.gitbook/assets/image (511).png>)\
Then re-do the _**Step 3**_.
{% endhint %}

{% hint style="danger" %}
**Don't** add the one with the name Bittle\*\*\_SSP that auto-generates a PIN code:\
![](<../.gitbook/assets/image (512).png>)\
Click the button _**Cancel**_ to quit.
{% endhint %}

4.  Test in Mind+:<br>

    <figure><img src="../.gitbook/assets/image (510).png" alt=""><figcaption></figcaption></figure>
