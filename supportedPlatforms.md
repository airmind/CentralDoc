# Latest Central Builds

#### Stable Release

MindCentral public release v3.0.0, Sharp A.

# Download Central binary

#### Currently supported platform

[Mac OS Version](https://github.com/airmind/MindCentral_Public_Releases/releases/download/MindCentral_v3_0_0_A/MindSkin.dmg)

Linux

# Installation

#### Mac OS

###### Pre-requisite

* MacOS 10.12 and above, with minimum 4GB memory and 10GB hard drive free space.

###### Installation

* Double click downloaded .dmg binary packet.
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
tar -xvf MindCentral.zip
```

* Launch MindCentral application by typing:

```
./mindcentral-start.sh &
```



