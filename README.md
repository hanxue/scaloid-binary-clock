# Scaloid Binary Clock
See instructions on how to build the clock from: http://dontbelievethebyte.github.io/article/2015/02/11/binary-clock-android-app-in-scala-part-1/

Original author: [Jean-Francois Berube](https://github.com/dontbelievethebyte)

## Getting Started
Clone this repository. I have a created a tag based on the sbt scaloid template. Check it out to another branch, and you can follow the steps above. 

```
$ git clone https://github.com/hanxue/scaloid-binary-clock.git
$ cd scaloid-binary-clock
$ git checkout -b my-branch start
```

Build
-----
You can build this project using sbt:

    $ sbt android:package

This will compile the project and generate an APK.

For more command, refer to [android-sdk-plugin for sbt](https://github.com/pfn/android-sdk-plugin).

Tips for faster development iteration
-------------------------------------
In sbt, `~` is a prefix that repeatedly runs the command when the source code is modified.

    ~run
    
This sbt command schedules to execute compile-package-deploy-run process after you save the edited source code.
Compiling and packaging runs incrementally, so this iteration takes about only few seconds.

If you use default AVD, try genymotion or other faster virtual device. Deploying apk to the device becomes much faster!

Using Eclipse
-------------

    $ sbt eclipse

Using IntelliJ IDEA
-------------------

### Generate the local.properties file

     $ android update project -p . # in the root of the project

### Plugins

Make sure the Scala & SBT plugins are installed in IntelliJ IDEA

### Import the SBT project

 File -> Import Project... -> select project root folder -> OK -> Import project from external model -> SBT Project
-> Check "Use auto-import" & for Project SDK, select an Android API platform -> Finish. Choose to configure the
android project when IDEA asks.

Edit the generated run configuration. Remove the 'Before launch: Make' then add a new SBT command `android:package-debug` then tab out or it
will not save, then click OK then OK.

You now should be able to run and debug from the run configuration like normal.

### Troubleshooting IntelliJ

`Local path doesn't exist.` when Intellij tries to deploy the apk.
 
File -> Project Structure -> Modules -> hello-scaloid-sbt -> Android -> Packaging -> Then choose the APK Path for
the apk. For this project it should be in .../bin/hello-scaloid-sbt-debug.apk

Troubleshooting
---------------

### Build error `Android SDK build-tools not available`
[The most likely cause of this error is that your SDK build-tools are old.](https://github.com/pfn/android-sdk-plugin/issues/13) Update the Android SDK and retry.

