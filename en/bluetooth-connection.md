# Bluetooth Connection

If you want to use [Joint Calibrator](https://docs.petoi.com/desktop-app/joint-calibrator), [Skill Composer](https://docs.petoi.com/desktop-app/skill-composer) in the Petoi Desktop App, or a coding block in [Mind+](https://docs.petoi.com/block-based-programming/petoi-coding-blocks) via computer Bluetooth, you need to pair the mainboard Bluetooth on the computer first.

## Connection Steps

### For BiBoard

1. Power on the mainboard via the battery (plug in the battery to the mainboard, and long-press the battery button > 3 seconds); after powering on, the mainboard's <mark style="color:blue;">blue</mark> LED and <mark style="color:yellow;">yellow</mark> LED should be on.
2.  For **Windows**, Open the Bluetooth & other devices  setting page, and turn on the Bluetooth button as follows:\


    <figure><img src=".gitbook/assets/image (502).png" alt=""><figcaption></figcaption></figure>
3.  Add the BiBoard Bluetooth for the first time as follows:\


    <figure><img src=".gitbook/assets/image (503).png" alt=""><figcaption></figcaption></figure>

    <figure><img src=".gitbook/assets/image (504).png" alt=""><figcaption></figcaption></figure>

    Select the one with the name <mark style="color:blue;">**Bittle\*\*\_BLE**</mark>:

<figure><img src=".gitbook/assets/image (505).png" alt=""><figcaption></figcaption></figure>

After paired successfully, it shows：

<figure><img src=".gitbook/assets/image (506).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (507).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you have already added the BiBoard Bluetooth before, after powering off and powering on the robot, you should remove both of the two devices in the list as follows:

![](<.gitbook/assets/image (511).png>)\
Then re-do the _**Step 3**_.
{% endhint %}

{% hint style="danger" %}
**Don't** add the one with the name Bittle\*\*\_SSP that auto-generates a PIN code:\
![](<.gitbook/assets/image (512).png>)\
Click the button _**Cancel**_ to quit.
{% endhint %}

Check the **outgoing** port. We will use it later in the Mind+ or Petoi Desktop App:

<figure><img src=".gitbook/assets/image (508).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (509).png" alt=""><figcaption></figcaption></figure>

4.  Test in Mind+:\


    <figure><img src=".gitbook/assets/image (510).png" alt=""><figcaption></figcaption></figure>

### For NyBoard

Please refer to the [Bluetooth module](https://docs.petoi.com/communication-modules/dual-mode-bluetooth#connection-with-nyboard) for NyBoard.