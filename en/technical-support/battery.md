# 🔋 Battery

## The robot battery&#x20;

Though you can program BiBoard directly or NyBoard with the USB uploader, external power is required to drive the servos separately.&#x20;

When the mainboard is powered by USB, the blue LED lights up. When external batteries power the mainboard, the yellow LED lights up.

<figure><img src="../.gitbook/assets/image (404).png" alt=""><figcaption></figcaption></figure>

### Parameters

Rechargeable Li-ion Battery

Model: ZCF503060

Rated Capacity: 1000mAh/7.4Wh

Input: 5V-1.5A

The servos require 7.4\~8.4V external power to move. Our customized Li-ion battery has a built-in charging and protection circuit. **Clicking** the battery's button will show its status. <mark style="color:blue;">**Blue**</mark> light indicates it has power, and <mark style="color:red;">**red**</mark> means the power is low. **Long-pressing** the button for 3 seconds to power on/off the battery.  &#x20;

### Connection and Power On

Be careful with the polarity when connecting the power supply. The terminal on the main board has an anti-reverse socket, so you won't be able to plug in the wrong direction.  See [here](https://bittle.petoi.com/4-Assemble-The-Frame#4.2.7-battery) for the detailed connection instructions. Before powering, insert the battery's plug into the main board's terminal.&#x20;

{% hint style="danger" %}
**Reversed connection may damage your NyBoard!**
{% endhint %}

### Battery Life

It can last hours if you're mainly coding and testing postures or less than 30 minutes if you keep Bittle running.&#x20;

<table><thead><tr><th width="392.3333333333333">Use senario</th><th>Battery life</th></tr></thead><tbody><tr><td>Stand by</td><td>several hours</td></tr><tr><td>Mainly coding and testing postures</td><td>a couple of hours</td></tr><tr><td>Stepping at the orignal spot</td><td>more than an hour</td></tr><tr><td>Running</td><td>less than 0.5 hours </td></tr></tbody></table>

The battery light will turn <mark style="color:red;">**red**</mark> when the power is low and will soon be cut off automatically.&#x20;

### Charging

Use a **5V-1A** USB charger to charge the battery. We don't recommend using fast chargers. The battery will **NOT** supply power during charging. Keep the battery in your sight when charging.&#x20;

During the charging process, the <mark style="color:red;">**red**</mark> LED light is on.&#x20;

When the charging is finished, the <mark style="color:green;">**green**</mark> LED light is on.

<figure><img src="../.gitbook/assets/Battery充电.jpg" alt=""><figcaption></figcaption></figure>

**WARNING**:&#x20;

* The battery should be charged under adult supervision, for battery charged using a battery charger for use by children, the battery is only to be charged by persons of at least **eight** years old.
* The supply terminals are not to be short-circuited.

### After Using

After using, remember to turn off the battery. The blue LED will stay light if the USB power still powers it. You can check if the <mark style="color:yellow;">**yellow**</mark> LED on the main board is turned off.&#x20;

### Attaching the Battery to the body

The battery can be attached to the robot's body conveniently without any screws. Check the following video:

{% embed url="https://youtu.be/aWU1mOPHKWk?si=IE3Py2yr1avZAk0X" %}

{% embed url="https://youtu.be/-IqF1hEATaM" %}

## The infrared remote control's battery

<figure><img src="../.gitbook/assets/IRnotes.jpeg" alt=""><figcaption></figcaption></figure>

The infrared remote control's battery is a coin battery. Its model is **CR2025**.

Please remove the plastic insulator when opening the package for the first time and using the remote control.

To remove and install the battery, please follow the diagram on the back of the remote control.

* This coin battery is not to be recharged;
* The battery is to be inserted with the **correct** polarity (**+** and **-**);
* Exhausted battery is to be removed from the remote control;&#x20;
* The supply terminals are not to be short-circuited.

**WARNING:** Contains coin battery. Hazardous if swallowed - see instructions.

**WARNING:** This product contains a coin battery. If swallowed, the battery can cause serious internal chemical burns.

**WARNING:** Dispose of used batteries immediately. Keep new and used batteries away from children. If you think batteries might have been swallowed or placed inside any part of the body, seek immediate medical attention.

{% hint style="danger" %}
WARNING:

This product contains a Coin Cell Battery. A swallowed Coin Cell Battery can cause internal chemical burns in as little as two hours and lead to death. Dispose of used batteries immediately. Keep new and used batteries away from children. If you think batteries might have been swallowed or placed inside any part of the body, seek immediate medical attention.
{% endhint %}
