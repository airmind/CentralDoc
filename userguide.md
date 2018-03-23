# Dev Guides

## Obtaining source code

Source code for Central is kept on GitHub: [https://github.com/airmind/Central](https://github.com/airmind/Central).

```
git clone --recursive https://github.com/airmind/Central.git
```

Each time you pull new source to your repository you should run `git submodule update` to get the latest submodules as well. Since Central uses submodules, using the zip file for source download will not work. You must use git.

### Supported Builds

#### Native Builds

Central builds are supported for OSX, Linux, Windows, iOS and Android. Central uses [Qt](http://www.qt.io) as its cross-platform support library.

* OSX: OSX 10.7 or higher, 64 bit, clang compiler
* Ubuntu: 64 bit, gcc compiler
* Windows: Vista or higher, 32 bit, [Visual Studio 2013 compiler](http://www.visualstudio.com/downloads/download-visual-studio-vs#d-express-windows-desktop)
* iOS: 8.0 and higher
* Android: Jelly Bean \(4.1\) and higher
* Qt version: 5.9.3+ ONLY

###### Install QT

You need to install Qt as described below instead of using pre-built packages from say, a Linux distribution because Central needs access to private Qt headers.

* Download the [Qt installer](http://www.qt.io/download-open-source)
  * Make sure to install Qt version **5.9.3+** NOT 5.4.x, 5.6.x, 5.7.x, etc.  
  * Ubuntu: Set the downloaded file to executable using:`chmod +x`. Install to default location for use with ./Central-start.sh. If you install Qt to a non-default location you will need to modify Central-start.sh in order to run downloaded builds.
  * Windows: Default installer not quite correct, use [this](http://download.qt.io/official_releases/qt/5.5/5.5.1/qt-opensource-windows-x86-msvc2013-5.5.1.exe) instead

###### Install additional packages:

* Ubuntu: sudo apt-get install espeak libespeak-dev libudev-dev libsdl1.2-dev
* Fedora: sudo dnf install espeak espeak-devel SDL-devel SDL-static systemd-devel
* Arch Linux: pacman -Sy espeak
* Windows: [USB Driver](http://www.pixhawk.org/firmware/downloads) to connect to Pixhawk/PX4Flow/3DR Radio
* Android: [Qt Android Setup](http://doc.qt.io/qt-5/androidgs.html)

#### Supported IDE

Developers can use [XCode](https://developer.apple.com/xcode/), [Android Studio](https://developer.android.com/studio/index.html), or [Qt Creator](http://doc.qt.io/qtcreator/index.html) to develop and build Central application.

###### Building using XCode

For iOS/MAC builds, XCode is recommended for developing native Obj-C/C++, Swift application, or Qt space application as well.

* Use qmake to generate XCode project. qmake uses shadow build. Make a build directory outside the Central source directory and cd to that directory. Type in following command:
  * iOS build: qmake ../Central/mindskin.pro -r -spec macx-ios-clang CONFIG+=iphoneos
  * MAC build: qmake ../Central/mindskin.pro -spec macx-xcode
* After generation completed, open `mindskin.xcodeproj` in XCode. You can edit source in XCode.
* Tap the 'Run' button to build and run.

#### ![](/assets/Screen Shot 2018-03-24 at 12.38.41 AM.png)

###### 

###### Building using Android Studio

For Java native developer, [Android Studio](https://developer.android.com/studio/index.html) is recommended to build Central application.

* Compile using qmake, i.e. build in Qt-Creator
* Enter the build directory and add gradle.properties with the following content:

```
androidCompileSdkVersion=23
androidBuildToolsVersion=24.0.0
qt5AndroidDir=/Users/<uid>/Qt5.9.3/5.9/android_armv7/src/android/
```

these properties in gradle.properties will be referenced by main build.gradle like below:

```
android {
/*******************************************************
* The following variables:
* - androidBuildToolsVersion,
* - androidCompileSdkVersion
* - qt5AndroidDir - holds the path to qt android files
*                   needed to build any Qt application
*                   on Android.
*
* are defined in gradle.properties file. This file is
* updated by QtCreator and androiddeployqt tools.
* Changing them manually might break the compilation!
*******************************************************/

compileSdkVersion androidCompileSdkVersion.toInteger()

buildToolsVersion androidBuildToolsVersion

sourceSets {
    main {
        manifest.srcFile 'AndroidManifest.xml'
        java.srcDirs = [qt5AndroidDir + '/src', 'src', 'java']
        aidl.srcDirs = [qt5AndroidDir + '/src', 'src', 'aidl']
        res.srcDirs = [qt5AndroidDir + '/res', 'res']
        resources.srcDirs = ['src']
        renderscript.srcDirs = ['src']
        assets.srcDirs = ['assets']
        jniLibs.srcDirs = ['libs']
   }
}

lintOptions {
    abortOnError false
}

}
```

* Copy back to qt project directory after android java/ui is finished.



###### Building using QtCreator

For other builds and platforms, developers can use QtCreator to build Central application.

* Launch [Qt Creator](http://doc.qt.io/qtcreator/index.html) and open the `mindskin.pro` project.
* Select the appropriate kit for your needs:
  * OSX: Desktop Qt 5.9.3 clang 64 bit
  * Ubuntu: Desktop Qt 5.9.3 GCC bit
  * Windows: Desktop Qt 5.9.3 MSVC2015 32bit
  * Android: Android for armeabi-v7a \(GCC 4.9, Qt 5.9.3\)

#### Vagrant

A Vagrantfile is provided to build Central using the [Vagrant](https://www.vagrantup.com/) system. This will produce a native Linux build which can be run in the Vagrant Virtual Machine or on the host machine if it is compatible.

* [Download](https://www.vagrantup.com/downloads.html) Vagrant
* [Install](https://www.vagrantup.com/docs/getting-started/) Vagrant
* From the root directory of the Central repository run "vagrant up"

#### Additional build notes for all supported OS

* Warnings as Errors: Specifying `CONFIG+=WarningsAsErrorsOn` will turn all warnings into errors which breaks the build. If you are working on a pull request you plan to submit to github for consideration, you should always run with this setting turned on, since it is required for all pull requests. NOTE: Putting this line into a file called "user\_config.pri" in the top-level directory \(same directory as `Central.pro`\) will set this flag on all builds without interfering with the GIT history.
* Parallel builds: For non Windows builds, you can use the '-j\#' option to run parellel builds.
* Location of built files: Individual build file results can be found in the `build_debug` or `build_release` directories. The built executable can be found in the `debug` or `release` directory.
* If you get this error when running Central: /usr/lib/x86\_64-linux-gnu/libstdc++.so.6: version 'GLIBCXX\_3.4.20' not found. You need to either update to the latest gcc, or install the latest libstdc++.6 using: sudo apt-get install libstdc++6.

## Additional functionality

Central has functionality that is dependent on the operating system and libraries installed by the user. The following sections describe these features, their dependencies, and how to disable/alter them during the build process. These features can be forcibly enabled/disabled by specifying additional values to qmake.

### Opal-RT's RT-LAB simulator

Integration with Opal-RT's RT-LAB simulator can be enabled on Windows by installing RT-LAB 7.2.4. This allows vehicles to be simulated in RT-LAB and communicate directly with QGC on the same computer as if the UAS was actually deployed. This support is enabled by default once the requisite RT-LAB software is installed. Disabling this can be done by adding `DEFINES+=DISABLE_RTLAB` to qmake.

### XBee support

Central can talk to XBee wireless devices using their proprietary protocol directly on Windows and Linux platforms. This support is not necessary if you're not using XBee devices or aren't using their proprietary protocol. On Windows, the necessary dependencies are included in this repository and no additional steps are required. For Linux, change to the `libs/thirdParty/libxbee` folder and run `make;sudo make install` to install libxbee on your system \(uninstalling can be done with a `sudo make uninstall`\). `qmake` will automatically detect the library on Linux, so no other work is necessary.

To disable XBee support you may add `DEFINES+=DISABLE_XBEE` to qmake.

### Video Streaming

Check the [Video Streaming](https://github.com/mavlink/Central/tree/master/src/VideoStreaming) directory for further instructions.

