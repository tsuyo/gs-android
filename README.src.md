# Getting Started: Installing the Android Development Environment

What you'll build
-----------------

This guide describes how to install the Android developer environment.

What you'll need
----------------

 - About 15 minutes
 - A favorite text editor or IDE
 - [JDK 6][jdk] or later

[jdk]: http://www.oracle.com/technetwork/java/javase/downloads/index.html


<a name="android-dev-env"></a>
Set up the Android development environment
----------------------------------------------

Before you can build Android applications, you must install the Android SDK. Installing the Android SDK also installs the AVD Manager, a graphical user interface for creating and managing Android Virtual Devices (AVDs). 

### Install the Android SDK

1. From the [Android web site][sdk], download the correct version of the Android SDK for your operating system. 

2. Unzip the archive to a location of your choosing. For example, on Linux or Mac, you can place it in the root of your user directory. See the [Android Developers] web site for additional installation details.

3. Configure the `ANDROID_HOME` environment variable based on the location of the Android SDK. Additionally, consider adding `ANDROID_HOME/tools`, and  `ANDROID_HOME/platform-tools` to your PATH.

    Mac OS X:

    ```sh
    $ export ANDROID_HOME=/<installation location>/android-sdk-macosx
    $ export PATH=${PATH}:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
    ```

    Linux:

    ```sh
    $ export ANDROID_HOME=/<installation location>/android-sdk-linux
    $ export PATH=${PATH}:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
    ```

    Windows:

    ```sh
    set ANDROID_HOME=C:\<installation location>\android-sdk-windows
    set PATH=%PATH%;%ANDROID_HOME%\tools;%ANDROID_HOME%\platform-tools
    ```

### Install Android SDK platforms and packages

The [Android SDK][sdk] download does not include specific Android platforms. To run the code in this guide, you need to download and install the latest SDK Platform. You do this by using the Android SDK and AVD Manager that you installed in the previous section.

1. Open the **Android SDK Manager** window:

    ```sh
    $ android
    ```

    > **Note:** If this command does not open the *Android SDK Manager*, then your path is not configured correctly.

2. Select the **Tools** checkbox.

3. Select the checkbox for the **latest Android SDK**, Android 4.2.2 (API Level 17) as of this writing.

4. From the **Extras** folder, select the checkbox for the **Android Support Library**.

5. Click the **Install packages...** button to complete the download and installation.

    > **Note:** You may want to install all the available updates, but be aware it will take longer, as each API level is a large download.

<a name="android-virtual-device"></a>
If necessary, create an Android virtual device
----------------------------------------------

If you do not have an Android device for testing, you can use an Android virtual device.To do this, you must first install the Android SDK and install the corresponding SDK platforms and packages. See [Set up the Android development environment](#android-dev-env).

### Create an AVD

This command creates a new AVD named "Default" that is based on Android 4.2.2, API Level 17:

```sh
$ android create avd --name Default --target 29 --abi armeabi-v7a
```

As an alternative you may also use the android GUI tool to create an AVD.

Here is more information about some of the parameters used:

 - `--name` Name of the new AVD.
 - `--target` Target ID of the new AVD.
 - `--abi` The CPU/ABI to use for the AVD.

This command displays a list of available targets. Use these targets to create different AVDs based on different Android versions as appropriate.

```sh
$ android list target
```

You can see that the target value of "29" is associated with Android 4.2.2. Note the three ABIs (CPUs) available for this target ID. The command used earlier to create the AVD specified an ARM CPU.

```sh
       id: 29 or "android-17"
     Name: Android 4.2.2
     Type: Platform
API level: 17
 Revision: 2
    Skins: HVGA, QVGA, WQVGA400, WQVGA432, WSVGA, WVGA800 (default), WVGA854, WXGA720, WXGA800, WXGA800-7in
    ABIs : armeabi-v7a, mips, x86
```

View the list of available AVDs with this command:

```sh
$ android list avd
```

Here is the AVD that was just created:

```sh
  Name: Default
  Path: /Users/{user}/.android/avd/Default.avd
Target: Android 4.2.2 (API level 17)
   ABI: armeabi-v7a
  Skin: WVGA800
```

### Start the AVD

Verify that the AVD is working:

```sh
emulator -avd Default
```

Summary
-------

Congratulations! You have just installed the Android development environment, which can be used with Spring.


[sdk]: http://developer.android.com/sdk/index.html
[Android Developers]: http://developer.android.com/sdk/installing/index.html
[Platforms and Packages]: http://developer.android.com/sdk/installing/adding-packages.html
