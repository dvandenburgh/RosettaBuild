RosettaBuild
============
####Android Build Environment:
####This guide will help you set up an Ubuntu 14.10 build Android 
####First I recommend purging your current Java set up if you have one
```
sudo apt purge openjdk-\* icedtea-\* icedtea6-\* oracle*
```
####Build Tools
```
$ sudo apt install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev
```
####If you have issues running apt, try aptitude;
```
$ sudo apt install aptitude
```
####and then try 
```
$ sudo aptitude install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzoppngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev
```
####Android debian packages
```
$ sudo add-apt-repository ppa:phablet-team/tools 
$ sudo apt-get update
$ sudo apt install phablet-tools android androidsdk-uiautomatorviewer android-copyright android-src-vendor android-emulator android-tools-adb android-headers android-tools-adbd androidsdk-ddms  android-tools-fastboot androidsdk-hierarchyviewer android-tools-fsutils androidsdk-traceview
```
####When that's done installing enter 
```
$ sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
```
####Setup Java (OpenJDK 7 for Lollipop. If building for versions prior to Lollipop install Oracle JDK 6)
```
$ sudo apt install openjdk-7-jdk 
```
##### **For building Android prior to Lollipop you will need the Oracle JDK**
```
$ sudo add-apt-repository ppa:webupd8team/java 
$ sudo apt-get update
$ sudo apt install oracle-java6-installer oracle-java6-set-default
```
####To set up your Android SDK easily and also download Android Studio
```
$ sudo apt-add-repository ppa:paolorotolo/android-studio; 
$ sudo apt update
$ sudo apt install android-studio
```
##### After the install process you with have to execute Android Studio to install the latest SDK sources and also the proper build tools. If you are building for Kitkat, you will need to open your SDK and download the proper files.

######Google's repo tool isn't necessary to install with the phablet-tools meta package it is already included. 

####Or install your SDK through Eclipse (personally I don't recommend this)
#####Open Eclipse goto Help/Install new Software
#####Click add:
```
https://dl-ssl.google.com/android/eclipse/
```
#Reboot.
