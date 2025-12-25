# 💻 Set up Development Environment on ChromebookU

## Set up Linux on your Chromebook

Linux is a feature that lets you develop software using your Chromebook. Install Linux command line tools, code editors, and IDEs (integrated development environments) on your Chromebook. These can be used to write code, create apps, and more.&#x20;

**Important:** If you use your Chromebook at work or school, you might be unable to use Linux. For more information, [contact your administrator](https://support.google.com/a/users/answer/15593939?visit_id=639022248360781300-3009579349\&rd=1\&hl=en\&sjid=2033080317536039223-NC).

### Turn on Linux

Linux is off by default. You can turn it on at any time from Settings.

1. On your Chromebook, at the bottom right, select the time.
2. Select Settings ![](https://storage.googleapis.com/support-kms-prod/EhnJKCYnCpUVMQvn9LxVpGRY4fJAjUYOfZGt) ![and then](https://lh3.googleusercontent.com/3_l97rr0GvhSP2XV5OoCkV2ZDTIisAOczrSdzNCBxhIKWrjXjHucxNwocghoUa39gw=w36-h36) **Advanced** ![and then](https://lh3.googleusercontent.com/3_l97rr0GvhSP2XV5OoCkV2ZDTIisAOczrSdzNCBxhIKWrjXjHucxNwocghoUa39gw=w36-h36) **Developers**.
3. Next to "Linux development environment," select **Turn On**.
4. Follow the on-screen instructions(default settings). Setup can take 10 minutes or more.
5. A terminal window opens. You have a Debian 11 (Bullseye) environment. You can run Linux commands, install more tools using the APT package manager, and customize your shell.

### **Accessing Linux environment:**

*   You can access your Linux environment through the terminal app in your Chromebook launcher.\
    ![](<../.gitbook/assets/image (474).png>)

    <figure><img src="../.gitbook/assets/image (477).png" alt=""><figcaption></figcaption></figure>
*   Files created in Linux are stored in a container and are separate from Chrome OS files. You can access them using the "Linux files" app.\
    ![](<../.gitbook/assets/image (475).png>)

    <figure><img src="../.gitbook/assets/image (476).png" alt=""><figcaption></figcaption></figure>
*   You can set the shared folders in the file browser and manage them in the Settings![](<../.gitbook/assets/image (485).png>):<br>

    <figure><img src="../.gitbook/assets/image (478).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../.gitbook/assets/image (479).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../.gitbook/assets/image (480).png" alt=""><figcaption></figcaption></figure>

## Update and install development tools:

Once the setup is complete, a terminal window will open. You can use the following commands to update the package list and install basic development tools:

```
sudo apt update
sudo apt upgrade
```
