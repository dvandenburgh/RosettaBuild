RosettaBuild
============
####Android Build Environment:
####This guide will help you set up an Ubuntu 15.04 build Android 
####First I recommend purging your current Java set up if you have one
```
sudo apt purge openjdk-\* icedtea-\* icedtea6-\* oracle*
```
####Setup Java (OpenJDK 7 for Lollipop. If building for versions prior to Lollipop install Oracle JDK 6)
```
sudo apt install openjdk-7-jdk 
```
####Build Tools
```
sudo apt install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev android-tools-adb android-tools-fastboot
```
####If you have issues running apt, try aptitude;
```
sudo apt install aptitude
```
####and then try 
```
sudo aptitude install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzoppngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev android-tools-adb android-tools-fastboot
```
#### Few more dependencies
```
sudo apt-get build-dep android -y; 
```
#### 51-android rules for usb
```
sudo curl --create-dirs -L -o /etc/udev/rules.d/51-android.rules -O -L https://raw.githubusercontent.com/snowdream/51-android/master/51-android.rules; 
sudo chmod a+r /etc/udev/rules.d/51-android.rules; 
sudo service udev restart
```
####When that's done installing enter 
```
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
```
####Set up your Android SDK 
```
wget http://dl.google.com/android/android-sdk_r24.1.2-linux.tgz 
*** or current https://developer.android.com/sdk/index.html ***
tar -xvzf android-sdk_r24.1.2-linux.tgz
cd ~/android-sdk/tools
./andoid sdk
```
### Now install any packages you still need from SDK
######Google's repo tool 
```
mkdir ~/bin; 
PATH=~/bin:$PATH; 
curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo
chmod a+x ~/bin/repo
echo "export PATH=~/bin:$PATH" >> ~/.bashrc

```
### *OPTIONAL* set up ccache 
```
sudo apt-get install ccache
cd ~/prebuilts/misc/linux-86/ccache;
ccache -M 50G *** (sets ccache to 50G you can use however much you wish)
echo "export USE_CCACHE=1" >> ~/.bashrc
```
### OPTIONAL install Android Studio
```
sudo add-apt-repository ppa:paolorotolo/android-studio
sudo apt-get update
sudo apt-get install android-studio
```
### Reboot cause you're good to go
