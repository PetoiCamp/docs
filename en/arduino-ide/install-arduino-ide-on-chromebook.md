# Install Arduino IDE on Chromebook

After [turning on Linux](https://docs.petoi.com/apis/set-up-development-environment-on-chromebook#turn-on-linux) on the Chromebook, you can access the Linux environment via the terminal app.

Please follow the following steps to install the Arduino IDE:

## Check the type of your OS version

<figure><img src="../.gitbook/assets/image (481).png" alt=""><figcaption></figcaption></figure>

## Download package

Open the website ([www.arduino.cc/en/software](https://www.arduino.cc/en/software)) and download the corresponding type of Legacy Arduino IDE:

<figure><img src="../.gitbook/assets/image (482).png" alt=""><figcaption></figcaption></figure>

## Installation

After downloading complete, set the folder _**Downloads**_ in the file browser to share with Linux, as mentioned above. Use the following commands to install the **Arduino IDE,** e.g., _**arduino-1.8.19-linux64.tar.xz**_ is the downloading file.

```
cd /mnt/chromeos/MyFiles/Downloads/
sudo apt-get install xz-utils
sudo tar -C /opt -xf arduino-1.8.19-linux64.tar.xz
cd /opt
ls
cd arduino-1.8.19/
ls
sudo ./install.sh
```

## Set up the Arduino IDE development environment for the mainboard

You can open the **Arduino IDE** as follows:

<figure><img src="../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

### NyBoard

For more details, please refer to [Upload Sketch for NyBoard](https://docs.petoi.com/\~/changes/MnaoHQ6wOvffal3XIPZR/arduino-ide/upload-sketch-for-nyboard).

After using the USB uploader and USB data cable to connect the NyBoard and Chromebook, you will see a prompt: Please click _**Connect to Linux**_**.**

<figure><img src="../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

and check in the **Settings** interface, and it should be enabled as follows:

<figure><img src="../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
After downloading the project file **OpenCat-main.zip** from GitHub: [https://github.com/PetoiCamp/OpenCat](https://github.com/PetoiCamp/OpenCat), use the following commands to unzip it to the _**Downloads**_ folder.

<pre><code><strong>cd /mnt/chromeos/MyFiles/Downloads/
</strong><strong>sudo apt-get install unzip
</strong>unzip OpenCat-main.zip
</code></pre>
{% endhint %}

### BiBoard

For more details, please refer to [Upload Sketch for BiBoard](https://docs.petoi.com/\~/changes/MnaoHQ6wOvffal3XIPZR/arduino-ide/upload-sketch-for-biboard).

After using the USB data cable to connect the BiBoard and Chromebook, you will see a prompt: Please click _**Connect to Linux**_**.**

<figure><img src="../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

and check in the **Settings** interface, and it should be enabled as follows:

<figure><img src="../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

Use the following commands to install the library pyserial for uploading the sketch for BiBoard

```
sudo apt install python3 pip
python3 -V
pip -V
cd /usr/lib/python3.11/
sudo rm EXTERNALLY-MANAGED
sudo pip3 install pyserial
pip list
```

{% hint style="info" %}
After downloading the project file **OpenCatEsp32-main.zip** from GitHub: [https://github.com/PetoiCamp/OpenCatEsp32](https://github.com/PetoiCamp/OpenCatEsp32), use the following commands to unzip it to the _**Downloads**_ folder.

<pre><code><strong>cd /mnt/chromeos/MyFiles/Downloads/
</strong>sudo apt-get install unzip
unzip OpenCatEsp32-main.zip
</code></pre>
{% endhint %}
