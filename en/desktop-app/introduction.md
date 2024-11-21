# Introduction

Petoi Desktop App provides a neat graphical user interface to configure the firmware, calibrate the robot, and design customized motions for your robot. The major function modules are the [Firmware Uploader](https://docs.petoi.com/desktop-app/firmware-uploader), [Joint Calibrator](https://docs.petoi.com/desktop-app/calibrator), and [Skill Composer](https://docs.petoi.com/desktop-app/skill-composer).

<figure><img src="../.gitbook/assets/image (378).png" alt=""><figcaption></figcaption></figure>

## Download & Installation

You can download the [latest version](https://github.com/PetoiCamp/OpenCat/releases) of the desktop App and unzip it.

Before running the app, you must use the included USB adapter or the Bluetooth dongle to connect to a Petoi robot.

### Windows

Run the UI.exe in the unzipped folder.  Do NOT move the UI.exe to another location in Windows.

### Mac

After downloading the Mac version, you must drag it into the Application folder.&#x20;

If you see the error message that "Petoi Desktop App" cannot be opened because the developer cannot be verified, you can right-click the icon, hold the **Shift** key and click **Open**.

![](<../.gitbook/assets/right open.JPG>)

### Linux

Please see the next chapter to run the app from a terminal

## Run the app from the Terminal

In the case of compatibility issues, or if you want to modify the source and test, you can also run the code from the Terminal.

The Terminal is a built-in interface on Mac or Linux machines. The equivalent environment on Windows machines is called the Command-Line Tool (CMD). It's recommended that you install [Anaconda](https://www.anaconda.com/) to manage your Python environment. It can also provide the Powershell as a Terminal for older Windows machines.

Depending on your existing Python configuration, you may need to upgrade to Python3 and install the following libraries:

* pyserial
* pillow

You can install them by entering `pip3 install pyserial pillow` in the Terminal or use the package manager in Anaconda.

To run the code:

1. In the Terminal, use the `cd` command to navigate to the `OpenCat/pyUI/` folder. You can use the Tab key to auto-complete the path name.
2. After entering the pyUI/ folder, enter `ls` and ensure you can see the UI.py and other python source codes listed.
3. Enter `python3 UI.py`.

{% hint style="info" %}
For Linux system users,  if you encounter the python error message "\_tkinter.TclError: no display name and no $DISPLAY environment variable", you can try to install **python3-tk**, **tk-dev**, taking Debian / Ubuntu as an example, the command is as follows:

`apt install python3-tk`

`apt install tk-dev`

After the installation is complete, reboot the computer.
{% endhint %}

## Open Source Codes

The source code is written with Tkinker in Python3 and is[ open source](https://github.com/PetoiCamp/OpenCat/tree/main/pyUI).

UI.py is the general entry for all the modules:

* UI.py

\-> FirmwareUploader.py

\-> Calibrator.py

\-> SkillComposer.py

\-> translate.py provides multi-language support for the UI. You may help to translate the UI into your language.
