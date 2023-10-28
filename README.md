<div align="center">
    <p><b>A library that lets you display your choice of app in Intent without any restriction above Android N.</b></p>
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
      Display your choice of App in your Actionview Intent or Intent.createChooser() Using this libray 😉
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
    <a href="https://github.com/MaazArfi/Custom-Intent.createChooser-Android/blob/main/msf_screen.jpeg">
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

<h2>How to integrate the library in your app?</h2>

In order to import a .aar library:</br>

```Download Library
Download ".AAR" https://msftechsolutions.co.in/Library/MSFCustomIntentLibrary.aar
```


After Downloading Switch to project view right click on project then :</br>
1) New>Directory</br>
2) Create a directory called "Library" and paste the downloaded "MSFCustomIntentLibrary.aar" file.</br>
3) Sync Project..</br>

It will look like as shown below.

<img
src="https://github.com/MaazArfi/Custom-Intent.createChooser-Android/blob/main/directory-library-installation.png?raw=true"
alt="Screenshot"
width="25%"/>

<b>Gradle Dependecy</b></br>

```gradle
dependencies {
        implementation files ('../library/MSFCustomIntentLibrary.aar')
}
```

### Create Instance object

Create Instance of library engine:
```
MSFCustomIntentLibraryEngine msfCustomIntentLibraryEngine;
```

### Initialise

Initialise the engine with object:

Initialising the engine will take 2 parameters.
1. Context  (Pass the current context or its object).
2. boolean  (Pass true or false passing true will make the library work else passing false will make the library silent or pause).

```java
msfCustomIntentLibraryEngine = new MSFCustomIntentLibraryEngine(MainActivity.this, true); 
```

### Add Packages

Add application packages by pointing the declared engine object and call method: setApplicationPackage().

Please note : You can pass unlimited number of package names as much as you want there is no limit take a look at the sample code below.

```java
msfCustomIntentLibraryEngine.setApplicationPackage("com.instagram.android");
msfCustomIntentLibraryEngine.setApplicationPackage("com.klook");
msfCustomIntentLibraryEngine.setApplicationPackage("com.whatsapp");
msfCustomIntentLibraryEngine.setApplicationPackage("com.snapchat.android");
```

### Calling Custom Intent Finally

Call Custom Intent by LoadMSFCustomIntentLib() method.
This method will take 2 parameters and has 1 interface attached.

1. Parameters  (1st Pass the current context or its object and 2nd Pass a text it will show on the bottom of intent or if you dont want pass null otherwise).
2. Interface  (As soon as you pass these 2 params it will ask for interface implementation just write "new" it will autoshow "new AppsAdapter.OnItemClickListener {...}" just hit enter).

PS :- This custom intent is buld on "BottomSheetDialogFragment" inside library so at the end of method you need to call ".show();" method of BottomSheetDialogFragment.

This method will take 2 parameters.
1. FragmentManager (Just simply pass "getSupportFragmentManager()").
2. String tag  (Simply enter **MSF_SHEET_LIBRARY_TAG**).
   
**Important note** in the String Tag you cannot pass any tag.

This ibrary will only allow "MSF_SHEET_LIBRARY_TAG" as tag.

Otherwise it will show a toast message "Wrong initialisation tag used."

Look at the sample code below.

```java
new LoadMSFCustomIntentLib(MainActivity.this, "Library Written by: MaazArfi", new AppsAdapter.OnItemClickListener() {
            @Override
            public void onItemClick(AllApps allApps, int i) {
                Toast.makeText(MainActivity.this, allApps.getName(), Toast.LENGTH_SHORT).show();
            }
        }).show(getSupportFragmentManager(), "MSF_SHEET_LIBRARY_TAG");
```

This "allApps" object holds all the data of apps like : Name , icon , size , installation date , etc.

### Full Sample code 

```java
public class MainActivity extends AppCompatActivity {

    //Declare Button instance object
    Button button;
    //Create library instance object
    MSFCustomIntentLibraryEngine msfCustomIntentLibraryEngine;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        //Initialise button and bind
        button = findViewById(R.id.load);

        //Initialise library with declared object and pass necessary parameters
        msfCustomIntentLibraryEngine = new MSFCustomIntentLibraryEngine(MainActivity.this, true);
        //Set the package names of the apps which you want to display in the intent
        msfCustomIntentLibraryEngine.setApplicationPackage("com.instagram.android");
        msfCustomIntentLibraryEngine.setApplicationPackage("com.klook");

        //Set onclick listener on the button
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                //Load the custom intent and pass necessary parameters
                new LoadMSFCustomIntentLib(MainActivity.this, "Library Written by: MaazArfi", new AppsAdapter.OnItemClickListener() {
                    @Override
                    public void onItemClick(AllApps allApps, int i) {
                        //When user will click app display name or do desired stuff
                        Toast.makeText(MainActivity.this, allApps.getName(), Toast.LENGTH_SHORT).show();
                    }
                }).show(getSupportFragmentManager(), "MSF_SHEET_LIBRARY_TAG");
            }
        });
    }
}
```

### Build the app with Android Studio

Build it with Android Studio normally.

## Contact Me

maaz.dev.x@msftechsolutions.co.in 
