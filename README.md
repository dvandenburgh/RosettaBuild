RosettaBuild
============
####Android Build Environment:
####This guide will help you set up an Ubuntu 14.10 build Android 
####First I recommend purging your current Java set up if you have one
```
sudo apt purge openjdk-\* icedtea-\* icedtea6-\* oracle*
```
### Install Python
```
$ sudo apt-get install build-essential gcc
$ wget https://www.python.org/ftp/python/2.7.9/Python-2.7.9.tgz
$ tar -xvzf Python-2.7.9.tgz
$ cd Python-2.7.9
$ ./configure --prefix=/usr/local/python2.7
$ make
$ sudo make install
```
####Setup Java (OpenJDK 7 for Lollipop. If building for versions prior to Lollipop install Oracle JDK 6)
```
$ sudo apt install openjdk-7-jdk 
```
####Build Tools
```
$ sudo apt install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev android-tools-adb android-tools-fastboot
```
####If you have issues running apt, try aptitude;
```
$ sudo apt install aptitude
```
####and then try 
```
$ sudo aptitude install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzoppngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev android-tools-adb android-tools-fastboot
```
#### 51-android rules for usb
```
$ sudo curl --create-dirs -L -o /etc/udev/rules.d/51-android.rules -O -L https://raw.githubusercontent.com/snowdream/51-android/master/51-android.rules; 
$ sudo chmod a+r /etc/udev/rules.d/51-android.rules; 
$ sudo service udev restart
```
####When that's done installing enter 
```
$ sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
```
####To set up your Android SDK easily and also download Android Studio
```
$ sudo apt-add-repository ppa:paolorotolo/android-studio; 
$ sudo apt update
$ sudo apt install android-studio
```
##### After the install process you with have to execute Android Studio to install the latest SDK sources and also the proper build tools. If you are building for Kitkat, you will need to open your SDK and download the proper files.

######Google's repo tool 
```
$ mkdir ~/bin; PATH=~/bin:$PATH; curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo; chmod a+x ~/bin/repo; export PATH=~/bin:$PATH

```
### Add the $PATH to your ~/.bashrc file with your chosen text editor
```
# Android tools
$ export PATH=${PATH}:~/android-sdk/tools
$ export PATH=${PATH}:~/android-sdk/platform-tools
$ export PATH=~/bin:$PATH
$ source ~/.bashrc
```
### Save and Exit

### And this to your ~/.profile
```
$ PATH="$HOME/android-sdk/tools:$HOME/android-sdk/platform-tools:$PATH"
```
### *OPTIONAL* set up ccache 
```
$ sudo apt-get install ccache
$ cd ~/prebuilts/misc/linux-86/ccache;
$ ccache -M 50G (sets ccache to 50G you can use however much you wish
$ export USE_CCACHE=1
```
### Then in your ~/.bashrc file again at the end
```
# export USE_CCACHE=1
```
### OPTIONAL install Android Studio
```
$ sudo add-apt-repository ppa:paolorotolo/android-studio
$ sudo apt-get update
$ sudo apt-get install android-studio
```
### Reboot cause you're good to go
