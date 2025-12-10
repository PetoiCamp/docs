# 🔧 Burn Bootloader for NyBoard

If you cannot upload sketches to the NyBoard (the "not in sync error") and verify that the serial connection is all good, the NyBoard's bootloader might be crashed during the last upload.&#x20;

{% hint style="info" %}
Verify that the serial connection is all good means:

1. The USB cable has data wires rather than just the power wires. The USB cable included in the Petoi package should be good.&#x20;
2. You have the proper driver for the uploader, or your computer can automatically install the driver. You can see and select the serial port in the Arduino IDE -> Tools -> Port.
3. All the contacts along the loop are connected firmly.&#x20;
4. You have successfully uploaded sketches previously.
{% endhint %}

There could be several reasons why the NyBoard's bootloader crashes. Some of the common causes include:

1. Uploading the sketch at a high baud rate
2. Using a malfunctioning USB cable
3. Using a power source that is not sufficient
4. Using a low-quality or damaged Uno board
5. Disrupting the upload process by pressing the reset button or unplugging the board
6. Memory overflow

In the specific case of Petoi robots, the sketch size and errors in the code are major causes of the crashed bootloader. Uploading a sketch to the Uno replaces the existing bootloader code with the new sketch. If the sketch is too large to fit in the memory or if there are errors in the code causing memory overflow, the bootloader may corrupt.&#x20;

## Use the Simple Bootloader Resetter

From August 2023, we will ship a simple bootloader resetter with the NyBoard. If you got an earlier batch and need to reset the bootloader, please write to [support@petoi.com](mailto:support@petoi.com) to request a free shipment.&#x20;

<figure><img src="../.gitbook/assets/新版Bootloader烧录器.jpg" alt=""><figcaption></figcaption></figure>

{% embed url="https://www.youtube.com/watch?v=R_rrP5Q_L-I" %}



{% hint style="info" %}
The old version:



<img src="../.gitbook/assets/simpleBootloader.png" alt="" data-size="original"><br>

{% embed url="https://youtu.be/ExJ0LOG8z9I" %}
{% endhint %}

{% hint style="info" %}
If the light ends up <mark style="color:red;">red</mark>, it means the resetting operation fails. It's probably a malfunction of either the NyBoard or the bootloader resetter.
{% endhint %}

## Use Arduino UNO Board

1.  &#x20;Open the sketch **ArduinoISP.ino**.<br>

    <figure><img src="../.gitbook/assets/image (169).png" alt=""><figcaption></figcaption></figure>
2.  &#x20;Select the items in the menu bar **Tools > Board** (Arduino UNO) and **Port** that connect to the UNO board.<br>

    <figure><img src="../.gitbook/assets/image (199).png" alt=""><figcaption></figcaption></figure>



    <figure><img src="../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure>



    <figure><img src="../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>
3.  &#x20;Upload the sketch **ArduinoISP.ino** to the **UNO** board.<br>

    <figure><img src="../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>
4.  &#x20;Wire the UNO board with NyBoard.<br>

    <figure><img src="../.gitbook/assets/ConnectWire03.png" alt=""><figcaption></figcaption></figure>
5.  &#x20;Select the **Arduino as ISP** in the menu bar **Tools>Programmer**.<br>

    <figure><img src="../.gitbook/assets/image (388).png" alt=""><figcaption></figcaption></figure>
6.  &#x20;Click the menu **Burn Bootloader**.<br>

    <figure><img src="../.gitbook/assets/image (245).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
At Step 6, you'd better push the jumpers with your fingers to ensure good contact.

![](<../.gitbook/assets/image (389).png>)
{% endhint %}

{% embed url="https://youtu.be/gXjgVTsqSlM" %}

{% hint style="info" %}
Since the NyBoard uses the same chip as a regular Arduino Uno, if you have two Nyboards, you can use one as a **programmer**(upload the sketch **ArduinoISP.ino**) to burn the bootloader to another one as the **target**. The steps are similar to the above, but you need to assign the **RESET** pin to 6 in the **ArduinoISP.ino** as follows:

![](<../.gitbook/assets/image (292).png>)\
The jumper connection is as follows:\
![](<../.gitbook/assets/image (189).png>)
{% endhint %}

## Use USBtinyISP or USBasp

* USBtinyISP\
  ![](<../.gitbook/assets/image (152).png>)    ![](<../.gitbook/assets/image (134).png>)

Connect the USBtinyISP programmer and NyBoard.  The pins connection map is as follows:

MI --> MISO          V --> VCC

SC --> SCK        MO --> MOSI

R --> Reset           G --> GND

Connect the USBtinyISP programmer to the computer with a USB port. After installing the driver as follows:

<figure><img src="../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

The driver is as follows:

{% file src="../.gitbook/assets/usbtinyisp_libusb_1.2.6.0.zip" %}

With NyBoard V1\_\*, you can simply choose **Arduino Uno** under the **Tool** menu of Arduino IDE, then burn the bootloader as follows:

<figure><img src="../.gitbook/assets/image (396).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
While Burning the bootloader, you'd better push the UsbtinyISP with your fingers to ensure good contact.

![](<../.gitbook/assets/image (165).png>)
{% endhint %}

{% embed url="https://youtu.be/NrZt8MZRhMc" %}

* USBasp\
  ![](<../.gitbook/assets/image (218).png>)    ![](https://ci5.googleusercontent.com/proxy/JDotWsy3hqC5zFUgWHgEh_QkMlCo2TmRtADW7Eh7WLIRFkQh-DrosRejloNvdrr7_AeIn86uQkZXJHhEp4d0kc0HJtkS-7LIq8Of-bd1uhAr6vdWmKUuXNmJTnik3h6WZp_ce3Aj5tjsH3DRRTzIKsg3lt_vLUBRZ-WBI9YlrpqAbfYUIbBPVp4Wo7GIZ2dvc-47qvoPqm84eyoqyT5Jia1JMgo_M1CyubNaM_owb67L07RpJcoNIARFLGC0W1kS6INgWCieLpt7oKdISR0NaQ=s0-d-e1-ft#https://static.wixstatic.com/media/4a8c7f_b354037432ea4fe38fca66734cf29fa9~mv2.png/v1/fill/w_820,h_303,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/4a8c7f_b354037432ea4fe38fca66734cf29fa9~mv2.png)<br>

Connect the USBasp programmer and NyBoard. The pins connection map is as follows:

MISO --> MISO       VCC --> VCC

SCK --> SCK           MOSI --> MOSI

Reset --> Reset      GND --> GND

Connect the USBasp programmer to the computer with a USB port. Afer installing the driver as follows:

<figure><img src="https://ci3.googleusercontent.com/proxy/53CtBbDXpfETcS_cIRn9REmlBvM3nnH7haJp80ouUSKjqB6h3LsMP8mZwN6LIFLYE37kc5xLpO9h0vy1smuZQVjHnlo2j5JCQFe_9AOra7oi9FmYRj-OnCTmdpKRvpA-l5OAiPqRrdpZahuwJeBb3mOdrSn-nlWagm3DA-N42ab2MKAjApVQG37RORkrgdNZf9ruuhcNARu8uKd6lc2x9zJ4eppgoKB3f6OcXCo6Bk7KBsFLajX7hWQSx2dx5boluZb5jiN2lCGKiF_hVsHeOQ=s0-d-e1-ft#https://static.wixstatic.com/media/4a8c7f_f7cae08f0498430390abfbb9ffc2d6df~mv2.png/v1/fill/w_820,h_535,al_c,q_90,usm_0.66_1.00_0.01,enc_auto/4a8c7f_f7cae08f0498430390abfbb9ffc2d6df~mv2.png" alt=""><figcaption></figcaption></figure>

The driver installer is as follows:

{% file src="../.gitbook/assets/zadig-2.8.zip" %}

With NyBoard V1\_\*, you can simply choose **Arduino Uno** under the **Tool** menu of Arduino IDE, then burn the bootloader as follows:

<figure><img src="https://ci4.googleusercontent.com/proxy/VULLBuDSOvGNH1mNZ4X1soEuLPfmZaxeOrufnl1FEnTi55UiaEE1cgWm0DEcKboiOreegpjqUG1SL5MYxEsCujMRKQzkFpJQiQ5oaLu3tlGJFRRI8XPRw9i8oUP9bqd8NV2RYGjpGBmSxFnCg9E4JoV3ar4fKZqQ7kyxjXKBegirA8kxM5JJjtIkGcUcd4UMVXWzj7mreqRIVsrAQonFrXn4GEt6AfveF3Qm4P3-C_X1n6X_oCqfGAZn6zGMbrhUXURMILTw4DTnhEhspP_tsQ=s0-d-e1-ft#https://static.wixstatic.com/media/4a8c7f_e10bd7b427364d57940544e5c11c69ab~mv2.png/v1/fill/w_820,h_734,al_c,q_90,usm_0.66_1.00_0.01,enc_auto/4a8c7f_e10bd7b427364d57940544e5c11c69ab~mv2.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The socket from the USBasp programmer to ICSP on NyBoard is not compatible. In this case, You need to use female-to-male jumper wires to connect the pins on each side as follows (It's a one-time operation, so there is no need for soldering)\
![](https://ci3.googleusercontent.com/proxy/AwPSNxZRSxTM8CZe4FvW2yiSG_b3uJGubsn5NZ7SpcaPhDg9sYQI3ATc8OrfN1NU59q3ToloLyus6eaeWl-LzVM26QakPcOz2LIpSbx1-VYudmlPqg0GTESyden7JbXWypgzX4JMj10GNmJ0RaFc9OL5K9cfA_77yOf2wdObKXXoxGLaZ1CH2Aji6HfEWM4qVOEO0wsnvKI4-bIkh6a_5fN7946iwvJcJtd8KbTwiwvJELaJFIauwKmyk8tKN2UdwRh-YrsO5_FgyvaX4N_gFQ=s0-d-e1-ft#https://static.wixstatic.com/media/4a8c7f_74acbb2a822e461886e7969a1ac92f3a~mv2.png/v1/fill/w_820,h_568,al_c,q_90,usm_0.66_1.00_0.01,enc_auto/4a8c7f_74acbb2a822e461886e7969a1ac92f3a~mv2.png)

While Burning the bootloader, make sure they have good contact. You can press the jumpers slightly to ensure the connections.
{% endhint %}

For details about how to use the USBasp programmer, you can refer to:

{% embed url="https://youtu.be/ToKerwRR-70" %}

## \* Upload sketches using a Programmer&#x20;

{% hint style="warning" %}
You may also use the Programmer to upload sketches to the board.&#x20;

<img src="../.gitbook/assets/programmerUpload_En.png" alt="" data-size="original">

It allows larger sketches because the bootloader takes about 2 KB on the flash. However, it will overwrite the default bootloader, and you WON'T be able to upload sketches using the regular USB uploader. And uploading sketches using the programmer is also slower. So it's not recommended unless your serial uploading routine is broken.&#x20;
{% endhint %}
