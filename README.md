RosettaBuild
============
####Android Build Environment:
####This guide will help you set up an Ubuntu 15.04/15.10 to build Android
##### Open a terminal 

####First I recommend purging your current Java set up if you have one
```
$ sudo apt purge openjdk-\* icedtea-\* icedtea6-\* oracle*
```
Installing the JDK
```
$ sudo apt install openjdk-7-jdk 
```
####Google's packagaes since Ubuntu 14.04
```
$ sudo apt-get install bison g++-multilib git gperf libxml2-utils make python-networkx zlib1g-dev:i386 zip
```
#####and some more since then
```
$ sudo apt-get install build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev androidsdk-uiautomatorviewer android-copyright android-src-vendor android-emulator android-tools-adb android-headers android-tools-adbd androidsdk-ddms  android-tools-fastboot androidsdk-hierarchyviewer android-tools-fsutils androidsdk-traceview gcc-arm-linux-androideabi gcc-i686-linux-android android-copyright abootimg android-headers android-src-vendor android-tools-fsutils android-tools-adbd aapt gradle; 
```
####If you have issues running apt-get, try aptitude;
```
$ sudo apt install aptitude
```
####and then try 
```
$ sudo aptitude install build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev androidsdk-uiautomatorviewer android-copyright android-src-vendor android-emulator android-tools-adb android-headers android-tools-adbd androidsdk-ddms  android-tools-fastboot androidsdk-hierarchyviewer android-tools-fsutils androidsdk-traceview gcc-arm-linux-androideabi gcc-i686-linux-android android-copyright abootimg android-headers android-src-vendor android-tools-fsutils android-tools-adbd aapt gradle;
```
#### 51-android rules for usb
```
$ sudo curl --create-dirs -L -o /etc/udev/rules.d/51-android.rules -O -L https://raw.githubusercontent.com/snowdream/51-android/master/51-android.rules; 
$ sudo chmod a+r /etc/udev/rules.d/51-android.rules; 
$ sudo service udev restart
```
####Set up your Android SDK 
```
$ wget http://dl.google.com/android/android-sdk_r24.3.4-linux.tgz 
*** or current https://developer.android.com/sdk/index.html ***
$ tar -xvzf android-sdk_r24.1.2-linux.tgz
$ cd ~/android-sdk-linux/tools
$ ./andoid sdk
```
### Now install any packages you still need from SDK
###Google's repo tool 
```
$ mkdir ~/bin
$ PATH=~/bin:$PATH
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
$ source ~/.bashrc
$ echo "export PATH=~/bin:$PATH" >> ~/.bashrc

```
### *OPTIONAL* set up ccache 
```
$ sudo apt-get install ccache
$ echo "export USE_CCACHE=1" >> ~/.bashrc
```
### OPTIONAL install Android Studio 
(Link is good as of 9/16 if not goto https://developer.android.com/sdk/index.html#Other download Android Studio for Linux)
```
$ wget https://dl.google.com/dl/android/studio/ide-zips/1.3.2.0/android-studio-ide-141.2178183-linux.zip
$ unzip android-studio-ide-141.2178183-linux.zip
$ cd android-studio/bin
$ ./studio.sh
```
### Reboot cause you're good to go repo will work after it to start syncing 
