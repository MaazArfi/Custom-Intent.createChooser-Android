<div align="center">
    <p><b>A library that lets you display your choice of app in Intent.createChooser() without any restriction above Android N.</b></p>
</div>

<div align="center">
    <p>
    <h3>
      <b>
        This library is partially written in Java, Kotlin, C++, Cmake
      </b>
    </h3>
  </p>
  <p>
    <b>
      Display your choice of App in your Actionview Intent Using My Repository 😉
    </b>
    <br/>
  </p>
  <p>

[![contributions welcome](https://img.shields.io/badge/Contributions-welcome-brightgreen?logo=github)](CODE_OF_CONDUCT.md) [![Website](https://img.shields.io/badge/Website-available-brightgreen?logo=e)](https://github.com/MaazArfi/Custom-android.intent.action.VIEW)
  </p>
  <p>
    <sub>
      Made with ❤︎ by
      <a href="https://github.com/MaazArfi">
        Maaz Arfi
      </a>
    </sub>
  </p>
  <br />
  <p>
    <a href="https://twoyi.io">
      <img
        src="https://github.com/MaazArfi/Custom-Intent.createChooser-Android/blob/main/msf_screen.jpeg?raw=true"
        alt="Screenshot"
        width="25%"
      />
    </a>
  </p>
</div>

## Introduction

This library is a lightweight. It runs as a normal app on Android. Additionally, it supports Android 5.0 ~ 14.

## Capability

1. Display your choice of app in android Intent.createChooser().
2. Support root and non-rooted devices.
3. Implement additional system components such as passing data by put extra method.
4. Do security research such as dynamic string array for passing android app packages.

## Features

1. Root and no root both support.
2. Android 5.0 and Android 14 will be supported.
3. Starting up app is very fast (within three seconds) except for the initialization process.
4. This is an open source project.
5. The internal system of this app will be fully customizable. Because its system is open source, you can fork the project to compile your own system. You can also customize the class components, such as the dynamic string array for app packages and other special features.

## Why this library ? and its Use cases 

As we know android operating system dosent give clear cut display of our choiced app in "**Intent.createChooser()**"

The Way Android system is designed when you use the ACTION_SEND intent with Intent.createChooser(), Android displays a system dialog that lists all the apps capable of handling the action. Users can then choose from the available options but sometimes we dont want to display every app we need a set of applications only due to code complexcity with data parameters and other issues.

In this libraray we implement a **Intent.createChooser()** within app with possiblity of our choice of app all you need is just pass the unlimited no of apps packages.

`Its Use cases :`
1. [Recent Case study Swiggy](https://bytes.swiggy.com/detecting-app-cloning-location-spoofing-on-android-452dd420f390)
2. Specific code logic work with any specific list of app.
3. Write your own strong logic for intent choosers.
4. etc.



### How integrate it?

  ```sh
   Download "aar" https://msftechsolutions.co.in/Library/MSFCustomIntentLibrary.aar
   ```

<img
        src="https://github.com/MaazArfi/Custom-android.intent.action.VIEW/blob/master/app/src/main/assets/msf_screen.jpeg?raw=true"
        alt="Screenshot"
        width="25%"
      />

### Build the App manually

#### Stacks

This app is partially written in Java,Kotlin,c++,Cmake so it's nessesary to [install and configure the NDK and CMake](https://developer.android.com/studio/projects/install-ndk) first.

#### Install android-ndk

Please refer to [any specificandroid-ndk](https://developer.android.com/studio/projects/install-ndk#specific-version).

You can check if it is installed by running `./gradlew cargoBuild`. If it succeeded, you will see libtwoyi.so in `app/src/main/jniLibs/arm64-v8a`.

PS. Prefferd is to use ndk v25 or lower, otherwise it may fail.

#### Configure a specific version of CMake

To set the CMake version, add the following to your module's build.gradle file:

android {
    ...
    externalNativeBuild {
        cmake {
            ...
            version "cmake-version"
        }
    }
}

### Configure the NDK in your project

Specify the version using the android.ndkVersion property in the module's build.gradle file, as shown in the following code sample.

android {
    ndkVersion "major.minor.build" // e.g.,  ndkVersion "21.3.6528147"
}

### Download this repository

Download this repository and copy paste code or use it as "aar" library.

### Build the app with Android Studio

Build it with Android Studio normally.

## Contact Me

maaz.dev.x@msftechsolutions.co.in 
