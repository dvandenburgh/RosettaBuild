RosettaBuild
============
####Android Build Environment:
####This guide will help you set up Ubuntu 16.04/10 to build Android
##### Open a terminal 

####First I recommend purging your current Java set up if you have one
```
$ sudo apt purge openjdk-\* icedtea-\* icedtea6-\* oracle*
```
Installing the JDK
Ubuntu 16.04
```
(Marshmallow and below)
$ sudo add-apt-repository ppa:openjdk-r/ppa  
$ sudo apt-get update  
$ sudo apt-get install openjdk-7-jdk
```
Ubuntu 16.10
No need for PPA, openjdk-7 is not availible on 16.10 so just roll with
```
(Nougat)
$ sudo apt-get install openjdk-8-jdk
```
####Google's packagaes since Ubuntu 14.04
```
$ sudo apt-get install git-core gnupg flex bison gperf build-essential \
  zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 \
  lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache \
  libgl1-mesa-dev libxml2-utils xsltproc unzip
```
#####and some more since then
```
$ sudo apt-get install build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev androidsdk-uiautomatorviewer android-copyright android-src-vendor android-emulator android-tools-adb android-headers android-tools-adbd androidsdk-ddms  android-tools-fastboot androidsdk-hierarchyviewer android-tools-fsutils androidsdk-traceview gcc-arm-linux-androideabi gcc-i686-linux-android android-copyright abootimg android-headers android-src-vendor android-tools-fsutils android-tools-adbd aapt gradle maven apktool; 
```
####If you have issues running apt-get, try aptitude;
```
$ sudo apt install aptitude
```
####and then try 
```
$ sudo aptitude install build-essential curl flex git gnupg gperf liblz4-tool libncurses5-dev libsdl1.2-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib lib32ncurses5-dev lib32z1-dev android-src-vendor android-tools-adb android-headers android-tools-adbd android-tools-fastboot android-tools-fsutils abootimg android-headers android-src-vendor android-tools-fsutils android-tools-adbd aapt gradle maven apktool;
```
#### 51-android rules for usb
```
$ sudo curl --create-dirs -L -o /etc/udev/rules.d/51-android.rules -O -L https://raw.githubusercontent.com/snowdream/51-android/master/51-android.rules; 
$ sudo chmod a+r /etc/udev/rules.d/51-android.rules; 
$ sudo service udev restart
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
$ echo "export CCACHE_EXEC=/usr/bin/ccache" >> ~/.bashrc
```

####Set up your Android SDK 
```
$ wget http://dl.google.com/android/android-sdk_r24.3.4-linux.tgz
*** or current https://developer.android.com/sdk/index.html ***
$ tar -xvzf android-sdk_r24.1.2-linux.tgz
$ cd ~/android-sdk-linux/tools
$ ./andoid sdk
```

### *OPTIONAL* set up ccache 
```
$ sudo apt-get install ccache
$ echo "export USE_CCACHE=1" >> ~/.bashrc
```

### *OPTIONAL* Toolchain dependencies 
```
$ sudo aptitude install flex bison ncurses-dev texinfo gcc gperf patch libtool automake g++ libncurses5-dev gawk subversion expat libexpat1-dev python-all-dev libgcc1:i386 bc libcloog-isl-dev libcap-dev autoconf libgmp-dev build-essential gcc-multilib g++-multilib pkg-config libmpc-dev libmpfr-dev linaro-image-tools linaro-boot-utils
```
