# Airtrik Java

Airtrik is an IoT Cloud platform for managing communication between IoT devices and software platforms.
This is java library that can be used for communicating IoT device. This library is primarly built for the use in android app.

## Summary

  - [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installing](#installing)
    - [Example Code](#example-code)
  - [Versioning](#versioning)
  - [Authors](#authors)
  - [License](#license)

## Getting Started

Follow the below instructions to get your device and application up and running within minutes. It is very easy to integrate airtrik into your project.

### Prerequisites

- Before proceeding further you install Android Studio on your system and connect a mobile or emulator to in.
- Create an account at [airtrik.com](https://airtrik.com/panel/) and create an app and devices to get your `__APP_KEY__` and `__DEVICE_ID__`


### Installing

Add the following dependencies to your gradle file and sync.

```gradle

allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' } // Add this
        ...
    }
}

dependencies {
    ...
    implementation 'com.github.airtrik:java:0.1.01'
    ...
}
```

### Example code

```java

import com.airtrik.iot.Airtrik;


// Connect to the app, put this code inside your Activity class
Airtrik.connect(this, "__APP_KEY__", new Airtrik.Options() {
    @Override
    public void onConnect(String appName, String[] devices) {

      // Print app name
        System.out.println(appName);

        for (int i = 0; i < devices.length; i++){
            // List all devices
            System.out.println(devices[i]);
        }
    }

    @Override
    public void onMessageReceive(String deviceId, String msg) {
        // Print all incomming message
        System.out.println(msg+" from "+deviceId);
    }
    @Override
    public void onAppKeyError(){
        System.out.println("APP KEY NOT CORRECT")
    }
});

// Sending message to device
Airtrik.send("__DEVICE_ID__","__MESSAGE__");



```


## Versioning



## Authors

  - **Vishal Pandey** - *Written Python Library* -
    [vishal-pandey](https://github.com/vishal-pandey)

See also the list of
[contributors](https://github.com/airtrik/python/contributors)
who participated in this project.

## License

This project is licensed under the [MIT](LICENSE)
Creative Commons License - see the [LICENSE](LICENSE) file for
details



