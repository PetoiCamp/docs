---
description: This chapter is for Advanced users with programming experience.
---

# Upload Sketch for BiBoard

## 1. Read the Quick Start Guide

For the specific parameters of each functional module of BiBoard, please refer to：

* [BiBoard V0 Guide](https://docs.petoi.com/biboard/biboard-v0#id-2.-modules-and-functions)
* [BiBoard V1 Guide](https://docs.petoi.com/biboard/biboard-v1-guide)

## 2. Set up BiBoard&#x20;

### 2.1 Prepare the ESP32 development environment

{% hint style="info" %}
Note:

* Arduino IDE 2.\*.\* **cannot** add the large\_spiffs\_16MB (4.5MB APP with OTA/6.93MB SPIFFS) configuration option currently.&#x20;
* The [SPIFFS file upload plugin](https://github.com/me-no-dev/arduino-esp32fs-plugin/releases/tag/1.0) in Arduino IDE 1.8.\* is written in Java. And Arduino IDE 2.0 is written in a different language (TypeScript + Golang), so the previous upload plugin cannot be used in Arduino IDE 2.\*.\* There is no support for the Arduino IDE 2.0 SPIFFS file upload plugin currently.

If you need to use more SPIFFS functions, it is recommended to install and use the [Arduino IDE 1.8](https://www.arduino.cc/en/software) temporarily; we strongly recommend the legacy version **1.8.19**. Otherwise, the latest version 2.\*.\* is OK.
{% endhint %}

Open **Preferences** in Arduino, add the ESP32 development board URL:

`https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`

<figure><img src="../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (599).png" alt=""><figcaption></figcaption></figure>

Click **OK** button to save it.

Open **Boards Manager...** and wait for updates from external board support links. Search “**esp32**” and install the support package.

{% hint style="warning" %}
Please install version **2.0.12**. Installing version 2.0.13 and above may cause the mainboard to fail to start up.
{% endhint %}

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (598).png" alt=""><figcaption></figcaption></figure>

After showing **INSTALLED**, the BiBoard board support package is finished.

### 2.2 Modify the code file in the package

* #### sdkconfig.h

{% hint style="info" %}
- For Windows:\
  C:\Users\\{username}\AppData\Local\Arduino15\packages\esp32\hardware\esp32\2.0.\*\tools\sdk\esp32\qio\_qspi\include\sdkconfig.h
- For Mac:\
  /Users/{username}/Library/Arduino15/packages/esp32/hardware/esp32/2.0.\*/tools/sdk/esp32/qio\_qspi/include/sdkconfig.h
- For Ubuntu:\
  Arduino root directory/.arduino15 (hidden file)/packages/esp32/hardware/esp32/2.0.12/tools/sdk/esp32/qio\_qspi/include/sdkconfig.h
{% endhint %}

Append a line of code at the end of the file:

```cpp
#define CONFIG_DISABLE_HAL_LOCKS 1
```

### 2.3 Setup the options

Please review the option list to configure the board's (ESP32 Dev Module)  upload speed, CPU frequency, and other settings.&#x20;

There is a setting for the **Flash Size** and **Partition Scheme** among the options. For more information, refer to the next section.&#x20;

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### 2.4 Choose hardware partition

The **BiBoard V0** uses an ESP32 with a **16M** flash. To simplify, you can use the **Minimal SPIFFS (1.9MB APP with OTA/190KB SPIFFS)** partition map without a problem. There's plenty of programming space for the standard OpenCatEsp32 firmware.&#x20;

The **BiBoard V1** uses an ESP32 with a **4M** flash.

#### 4 MB partition

You can use the **Minimal SPIFFS (1.9MB APP with OTA/190KB SPIFFS)**.&#x20;

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

#### 16 MB partition

Suppose you want to fully utilize the 16 MB flash of **BiBoard V0** (it's unnecessary and takes a longer uploading time). You can read the user manual for the [Add hardware partition configuration option in Arduino IDE](https://docs.petoi.com/biboard/demo-applications/13.-add-hardware-partition-configuration-option-in-arduino-ide).

### 2.5 Download the source code & install the library

{% hint style="info" %}
We keep updating the codes as an open-source project. You can star-mark and follow our GitHub repository to get the newest features and bug fixes. You can also share your codes with worldwide OpenCatEsp32 users.&#x20;
{% endhint %}

1. Download the ​OpenCatEsp32 repository from GitHub repository: [https://github.com/PetoiCamp/OpenCatEsp32](https://github.com/PetoiCamp/OpenCatEsp32)\
   We suggest you utilize GitHub’s version control feature. Otherwise, make sure you download the **WHOLE OpenCatEsp32 FOLDER** every time. All the codes have to be the same version to work together.&#x20;

<figure><img src="../.gitbook/assets/downloadEsp32Repo.png" alt=""><figcaption></figcaption></figure>

2. If you download the Zip file of the codes, you will get an **OpenCatEsp32-main** folder after unzipping. Please rename it to **OpenCatEsp32** before opening the **OpenCatEsp32.ino** so that the two names match.&#x20;

{% hint style="warning" %}
No matter where you save the folder, the file structure should be:

![](<../.gitbook/assets/OpenCatEsp32_tree (1).png>)&#x20;
{% endhint %}

* There are several **test\*\*\*.ino** codes in the **ModuleTests** folder. You can upload them separately to test specific modules (I recommend using **testBuzzer.ino** as your first test sketch).

3.  Install the libraries:&#x20;

    1. Download and install the [MU Vision Sensor library](https://github.com/mu-opensource/MuVisionSensor3) into the Arduino IDE.

    <figure><img src="https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FrwlwHLV03mwtrtqVazop%252FmuLib.png%3Falt%3Dmedia%26token%3Df7721966-efb2-4388-9563-002c9aa93c3a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=852f24b1&#x26;sv=2" alt=""><figcaption></figcaption></figure>

    <figure><img src="https://docs.petoi.com/~gitbook/image?url=https%3A%2F%2F1565080149-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MQ6a951Q6Jn1Zzt5Ajr-887967055%252Fuploads%252FRN0NyFXOV0ct9IOI0AqU%252FaddZipLib.png%3Falt%3Dmedia%26token%3D4803980c-41cf-406c-907c-3aaff81672ec&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=13cd3321&#x26;sv=2" alt=""><figcaption></figcaption></figure>

    b. Install **ArduinoJson** in the Library Manager:

<figure><img src="../.gitbook/assets/image (559).png" alt=""><figcaption></figcaption></figure>

\


<figure><img src="../.gitbook/assets/image (560).png" alt=""><figcaption></figcaption></figure>

### 2.6 [Connect to BiBoard](../upload-firmware/#biboard) via USB type-C data cable

Set the serial port in the Arduino IDE:

<figure><img src="../.gitbook/assets/image (461).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you cannot find the serial port after connecting to your computer:

*   for BiBoard V0:

    You need to install [the driver](https://docs.petoi.com/technical-support/useful-tools#biboard-driver-to-access-the-serial-port) for the CP210x chip.&#x20;
*   For BiBoard V1:

    You need to install the driver as below:

    * Windows: [https://www.wch-ic.com/downloads/CH343SER\_EXE.html](https://www.wch-ic.com/downloads/CH343SER_EXE.html)
    * Mac: [https://www.wch-ic.com/downloads/CH34XSER\_MAC\_ZIP.html](https://www.wch-ic.com/downloads/CH34XSER_MAC_ZIP.html)
* If the battery powers on the BiBoard, please long-press the button on the battery >=3s to power off the BiBoard, so that the BiBoard is only powered through the USB cable and only the blue LED is lit up.&#x20;
{% endhint %}

### 2.7 Compile and upload the sketch

Modify the device type macro definition in **OpenCatEsp32.ino** according to the device type.

```cpp
#define BITTLE    //Petoi 9 DOF robot dog: 1 on head + 8 on leg
//#define NYBBLE  //Petoi 11 DOF robot cat: 2 on head + 1 on tail + 8 on leg
//#define CUB
```

Modify the motherboard model macro definition in OpenCatEsp3&#x32;**.ino** according to the [mainboard (BiBoard) version](https://docs.petoi.com/desktop-app/firmware-uploader#biboard-for-bittle-x).

```cpp
// #define BiBoard_V0_1  //ESP32 Board with 12 channels of built-in PWM for joints
#define BiBoard_V0_2
// #define BiBoard_V1_0
```

if the robot(Bittle X+Arm) with the robotic arm, you should also activate the macro definition as follows:

```cpp
#define ROBOT_ARM                 // for attaching head clip arm
```

Otherwise, please comment out this line code.

After the modification is completed, you can click the **Upload** button (as below) to upload the sketch **OpenCatEsp32.ino**, and the changes in the code file will be automatically saved.

<figure><img src="../.gitbook/assets/image (515).png" alt=""><figcaption></figcaption></figure>

### 2.8 Program Initialization

If the **version date** of the currently uploaded sketch is **newer** than the version date of the mainboard firmware, it will automatically enter the **initialization startup mode** after the sketch upload is completed.

{% hint style="warning" %}
Please open the serial monitor and set the configuration parameters of the serial port monitor to **115200** baud rate and **No line ending**.\
![](<../.gitbook/assets/image (563).png>)\


<img src="../.gitbook/assets/image (561).png" alt="" data-size="original">
{% endhint %}



* You can check the version date of the currently uploaded sketch in the source code file (OpenCatEsp32/src/OpenCat.h):\
  `#define DATE "250218"  // YYMMDD`
* You can send the serial command "**?**" in the serial monitor to check the version date of the mainboard firmware:\
  ![](<../.gitbook/assets/image (562).png>)

When the mainboard is powered on, open the serial monitor and you will see the startup information:

```
ets Jun  8 2016 00:22:57

rst:0xc (SW_CPU_RESET),boot:0x1b (SPI_FAST_FLASH_BOOT)
configsip: 0, SPIWP:0xee
clk_drv:0x00,q_drv:0x00,d_drv:0x00,cs0_drv:0x00,hd_drv:0x00,wp_drv:0x00
mode:DIO, clock div:1
load:0x3fff0030,len:1344
load:0x40078000,len:13964
load:0x40080400,len:3600
entry 0x400805f0
k
Flush the serial buffer...

* Start *
Bittle X
Software version: B02_250121
Scanning I2C network...
- I2C device found at address 0x54:	EEPROM
- I2C device found at address 0x5C:	Misc.
- I2C device found at address 0x68:	MPU6050
- I2C device found at address 0x69:	ICM42670
- I2C device found at address 0x7E:	Misc.
- done
GroveVisionQ	0
MuQ	0
Set up the new board...
Unmute and set volume to 5/10
Using constants from I2C EEPROM
- Name the new robot as: Bittle45
```

{% hint style="info" %}
If you do not see the startup information after opening the serial monitor, please short press the **Reset** button on the mainboard.
{% endhint %}

Next you will see the following prompt questions:

```cpp
Reset the joints' calibration offsets? (Y/n): 
```

* Send '**Y**' to the question, which means resetting all servo corrections to zero.
* &#x20;Send "**n**" to skip this step.

{% hint style="info" %}
If you want to keep the previous joint calibration data, please send '**n**'.
{% endhint %}

```cpp
- Calibrate the Inertial Measurement Unit (IMU)? (Y/n): 
```

* Send '**Y**' to the question, which means calibrating the IMU, i.e. the gyro/accelerometer sensor.
* &#x20;Send "**n**" to skip this step.

{% hint style="info" %}
If you want to keep the previous IMU calibration data, please send '**n**'.
{% endhint %}

{% hint style="warning" %}
Halts at the connection stage. To restart it, you can close and reopen the serial monitor or press the reset button on BiBoard. Put the BiBoard **FLAT** on the table, and don't touch it during calibration.

Sometimes, the program halts at the connection stage. To restart it, you can close and reopen the serial monitor or press the reset button on BiBoard.&#x20;

The program starts calibration after playing the melody 6 times.
{% endhint %}

```
Run factory quality assurance program? (Y/n)        
```

Input '**n**' and press **Enter** to continue. Or you can do nothing, it will Auto skip in 5 seconds.

The details of serial port printing information are as follows：

```cpp
* Start *
Scanning I2C network...
- I2C device found at address 0x54  !
- I2C device found at address 0x68  !
- done
Set up the new board...
// 蓝牙连接时使用的设备名称
- Name the new robot as: BittleED    
Reset the joints' calibration offsets? (Y/n): 
Y
Buzzer volume: 5/10
- Calibrate the Inertial Measurement Unit (IMU)? (Y/n): 
Y

Put the robot FLAT on the table and don't touch it during calibration.

Initializing MPU6050...
OK
If the program stucks, reinstall Arduino ESP32 boards version 2.0.12. Newer version may cause bugs!
- Testing MPU connections...attempt 0
- MPU6050 connection successful
- Initializing DMP...
MPU offsets: 2691	1893	1181	72	-57	0	
Calibrate MPU6050...
>....................>....................
MPU offsets:
//           X Accel  Y Accel  Z Accel   X Gyro   Y Gyro   Z Gyro
//OFFSETS     2759,    1871,    1173,      73,     -56,      -4
- Enabling DMP...
- DMP ready! Waiting for the first interrupt...
BLE:		Bittle45_BLE
Waiting for a BLE client connection to notify...
SSP:		Bittle45_SSP
The SSP device is started, now you can pair it with Bluetooth!
Setup ESP32 PWM servo driver...
Calibrated Zero Position
135	225	135	135	190	80	190	80	190	80	80	190	
Build skill list...88
Run factory quality assurance program? (Y/n)
(Auto skip in 5 seconds)
5...4...3...2...1...n
TaskQ
rest
11
Init voice
Number of customized voice commands on the main board: 
10
Turn on the audio response
Show Petoi Logo color
S,	A,	T,	L,	D,	I,	B,	U,	G,	C,	Q,	
0,	1,	0,	0,	0,	0,	0,	0,	0,	0,	0,	
Ready!
g
rest
d
XAaXAc
Switch English

```

When the string "<mark style="color:green;">**Ready!**</mark>" is output in the serial monitor, the program will enter the **regular startup mode**.

Every time the mainboard is powered on, it compares the BIRTHMARK in the EEPROM to determine whether the program has been initialized. If the program has already been initialized, it will **not enter** the **initialization startup mode** again.

{% hint style="info" %}
**Note:** When the mainboard is powered on, the music melodies played in the **regular startup mode** and the **initialization startup mode** are completely different. This is convenient for users (no need to open the serial monitor) and can also identify the startup mode.&#x20;

If you need to clear the calibration parameters of the servo and recalibrate the joint servo, or recalibrate the IMU, you can send the serial command "<mark style="color:red;">**!**</mark>" in the serial monitor, and the program will **re-enter** the **initialization startup mode**.
{% endhint %}

### 2.9 Swith working mode via the serial commands (Optional)

The default code runs the **Standard** mode (including the **Voice command** function). If you want to switch modes, Please open the serial monitor and send the following serial commands:

<table><thead><tr><th width="172">Serial command</th><th>Function</th></tr></thead><tbody><tr><td>XA</td><td>Voice. For <strong>BiBoard V0</strong>, the switch on the extension hat should be dialed to the <strong>Voice command</strong> side （<strong>default mode</strong>）</td></tr><tr><td>XU</td><td>Ultrasonic. For <strong>BiBoard V0</strong>, the switch on the extension hat should be dialed to the <strong>Uart2</strong> side; voice control will not work.</td></tr><tr><td>XC</td><td>Camera</td></tr><tr><td>XL</td><td>Light</td></tr><tr><td>XT</td><td>Touch</td></tr><tr><td>XI</td><td>PIR</td></tr><tr><td>XG</td><td>Gesture</td></tr><tr><td>XD</td><td>IR distance</td></tr><tr><td>XQ</td><td>Quick demo</td></tr><tr><td>XS</td><td>Enable the Serial 2(Tx2, Rx2). For <strong>BiBoard V0</strong>, the switch on the extension hat should be dialed to the <strong>Uart2</strong> side; voice control will not work. </td></tr><tr><td>XB</td><td>Enable the back touch funtion. </td></tr><tr><td>X</td><td>Disable all the module functions above.</td></tr><tr><td>z</td><td>RandomMind (On/Off)</td></tr></tbody></table>

{% hint style="info" %}
The behavior of the official modules is defined in separate header files in **OpenCat/src/**. You can find them in **OpenCat/src/io.h** **-> readSignal()**. The behavior of **Quick demo** mode is defined in **OpenCat/OpenCat.ino ->  quickDemo()**. You can study the example code to write your functions.&#x20;

You can learn about the function of each module through the [**EXTENSIBLE MODULES**](https://docs.petoi.com/extensible-modules/introduction).
{% endhint %}

### 2.10 Power on

* Long-press the battery button and boot up the robot with one side up. It will enter the calibration state automatically in the **regular startup mode**. The picture below shows the head, the upper and lower legs installed after the robot enters the calibration state.

![](<../.gitbook/assets/SideUp (1).jpg>)

Please refer to [Chapter 5 🔌 Connect Wires](https://bittle.petoi.com/5-connect-wires) and [Chapter 6 📐 Calibration](https://bittle.petoi.com/6-calibration) for the complete calibration process.

* If you power on the robot and it is upright (with its back upward), the robot will start from the "rest" posture (fold the legs and unlock the servos)  in the **regular startup mode**.

### 3. Configuration with App

The BiBoard has built-in Bluetooth, and you can connect it with the [mobile app](https://docs.petoi.com/mobile-app/introduction) to do [joint calibration](https://docs.petoi.com/mobile-app/calibrator) and [remote control](https://docs.petoi.com/mobile-app/controller).

You can check the update history information in the [**ChangeLog.md**](https://github.com/PetoiCamp/OpenCatEsp32/blob/main/ChangeLog.md)**.**
