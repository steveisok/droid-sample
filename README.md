# Getting Your App to Run on linux-bionic

This is how you can get a simple project to run on an Android device or emulator without the Dalvik VM.

## Building and running

The project in this repo is a plain old console app created via `dotnet new console`.

Here are the steps to get things running:

1. Publish your app

Open a terminal and in your project's directory, type:

`dotnet publish -r linux-bionic-<target-arch>` 

Where `target-arch` is arm64 or x64 depending on what device/emulator you are targeting.

2. Copy the artifacts to the device / emulator via `adb push`

`adb` is a platform-tool in the Android SDK.  Using this tool, you can copy all of the artifacts to your device/emulator.

`adb push bin/<configuration>/net7.0/linux-bionic-<target-arch>/publish/ /data/local/tmp/droid-sample`

3. Execute the application using `adb shell`

Now you can run the application with:

`adb shell /data/local/tmp/droid-sample/droid-sample`

