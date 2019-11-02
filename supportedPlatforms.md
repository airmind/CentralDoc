# Latest Central Builds

#### Stable Release

MindCentral public release v3.0.0, Sharp A.

# Download Central binary

#### Select version for different operating systems

[Mac OS Version](https://github.com/airmind/MindCentral_Public_Releases/releases/download/MindCentral_v3_0_0_A/MindSkin.dmg)

[Linux Version](https://github.com/airmind/MindCentral_Public_Releases/releases/download/MindCentral_v3_0_1_A/MindCentral.tar.bz2)

# Installation

#### Mac OS

###### Pre-requisite

* MacOS 10.12 and above, with minimum 4GB memory and 10GB hard drive free space.

###### Installation

* Double click downloaded .dmg binary package.
* Drag the MindCentral icon into 'Launchpad' on task bar.
* Tap the MindCentral icon in Launchpad to run the application.

#### Linux

###### Pre-requisite

* Ubuntu 18.04, with Intel i5 processor \(or equivalent\) recommended, minimum 4GB memory and 10GB hard drive free space.

* Install SDL library. Open a terminal and input following commands:

```
sudo apt-get install libsdl2-2.0
```

* Remove modem manager:

```
sudo apt-get remove modemmanager -y
```

* Authorize yourself access to USB serial port, where '$USER' is your user name to login into Linux:

```
sudo usermod -a -G dialout $USER
```

* Reboot your computer to make sure commands take effect.

###### Installation

* Create folder 'MindCentral' under your home folder and copy downloaded MindCentral binary file into it.
* Change working directory into this folder and unzip the binary package using following command:

```
tar -xvf MindCentral.tar.bz2
```

* Launch MindCentral application by typing:

```
./mindcentral-start.sh &
```



# Un-installation

Un-installation is needed if you want to remove MindCentral from your computer, or upon an upgrade to new version.

#### Mac OS

Simply find the MindCentral app in 'Application' and delete it. 

To also remove application data \(logs, plans, etc.\), go too 'Documents' directory, and remove the 'MindCentral' directory there.

You can keep the application data directory if you only want to do an upgrade.

#### Linux

Go to installation directory, and remove all contents under.

Go to Document directory and remove the 'MindCentral' directory.

You can keep the application data directory if you only want to do an upgrade.



