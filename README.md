RosettaBuild
============
####Android Build Environment:

####This guide will help you set up an Ubuntu 14.10 build Android 

```
####Build Tools
```

$ sudo apt install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop openjdk-6-jdk openjdk-6-jre pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev
```
####If you have issues running apt, try aptitude;
```
$ sudo apt install aptitude
```
####and then try 
```
$ sudo aptitude install  sudo apt install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop openjdk-6-jdk openjdk-6-jre pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev
```

####When that's done installing enter 
```
$ sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
```
####Setup Java (OpenJDK 7 for Lollipop. If building for versions prior to Lollipop install Oracle JDK 6)
```
$ sudo apt install openjdk-7-jdk 
```
####Add to .bashrc
```
# Python
export PATH=/usr/bin:$PATH
```

####OPTIONAL to set up your Android SDK easily and also download Android Studio
```
$ sudo apt-add-repository ppa:paolorotolo/android-studio; 
$ sudo apt update
$ sudo apt install android-studio
```

####Or install through Eclipse
#####Open Eclipse goto Help/Install new Software
#####Click add:
```
https://dl-ssl.google.com/android/eclipse/
```

####Add SDK to .bashrc (from Android Studio it will be installed as I have it. If you did it through Eclipse the defaultis ~/android-sdks)
```
#Android SDK 
export PATH=${PATH}:~/Android/Sdk/tools
export PATH=${PATH}:~/Android/Sdk/platform-tools
export PATH=${PATH}:~/bin
```
Add PATH to .profile:
```
$ PATH="$HOME/Android/Sdk/tools:$HOME/Android/Sdk/platform-tools:$PATH"
```
####Configure USB (Android 51 Rules)
```
$ sudo curl --create-dirs -L -o /etc/udev/rules.d/51-android.rules -O -L https://raw.githubusercontent.com/snowdream/51-android/master/51-android.rules; sudo chmod a+r /etc/udev/rules.d/51-android.rules; sudo service udev restart
```
####Install the Repo:
```
$ mkdir ~/bin; PATH=~/bin:$PATH; curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo; chmod a+x ~/bin/repo
```
#Reboot.
