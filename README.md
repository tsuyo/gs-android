# Getting Started: Android Development Environment

What you'll build
-----------------

This guide walks you through installing the Android developer environment.

What you'll need
----------------

 - About 15 minutes
 - A favorite text editor or IDE
 - [JDK 6][jdk] or later

[jdk]: http://www.oracle.com/technetwork/java/javase/downloads/index.html


<a name="android-dev-env"></a>
Set up the Android development environment
----------------------------------------------

Building Android applications requires you to install the [Android SDK][sdk]. Installing the Android SDK also installs the AVD Manager, which provides a graphical user interface for creating and managing Android Virtual Devices (AVDs). 

### Install the Android SDK

1. Download the correct version of the [Android SDK][sdk] for your operating system from the Android web site

2. Unzip the archive to a location of your choosing. For example, on Linux or Mac, you could place it in the root of your user directory. See the [Android Developers] web site for additional installation details

3. Configure the `ANDROID_HOME` environment variable based on the location of the Android SDK. Additionally, consider adding `ANDROID_HOME/tools`, and  `ANDROID_HOME/platform-tools` to your PATH

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

The [Android SDK][sdk] download does not include specific Android platforms. To run the code in this guide, you need to download and install the latest SDK Platform. You do this by using the Android SDK and AVD Manager that was installed from the previous step.

1. Open the **Android SDK Manager** window:

    ```sh
    $ android
    ```

    > Note: If this command does not open the *Android SDK Manager*, then your path is not configured correctly.

2. Select the checkbox for **Tools**

3. Select the checkbox for the latest Android SDK, Android 4.2.2 (API Level 17) as of this writing

4. Select the checkbox for the **Android Support Library** from the **Extras** folder

5. Click the **Install packages...** button to complete the download and installation

    > Note: You may want to install all the available updates, but be aware it will take longer, as each API level is a large download.

<a name="android-virtual-device"></a>
Android Virtual Device
----------------------

If you do not have an Android device for testing, you can use an [Android Virtual Device (AVD)][avd]. To do this, you must first install the Android SDK and install the corresponding SDK platforms and packages. See [Install the Android Development Environment](#android-dev-env).

### Create an AVD

The following command creates a new AVD named "Default" that is based on Android 4.2.2 (API Level 17).

```sh
$ android create avd --name Default --target 29 --abi armeabi-v7a
```

### Start the AVD

Verify the AVD is working with the following command:

```sh
emulator -avd Default
```

Summary
-------

Congratulations! You have just installed the Android development environment which can be used with Spring.


[sdk]: http://developer.android.com/sdk/index.html
[Android Developers]: http://developer.android.com/sdk/installing/index.html
[Platforms and Packages]: http://developer.android.com/sdk/installing/adding-packages.html
