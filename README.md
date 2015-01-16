RosettaBuild
============
####Android Build Environment:

####This guide will help you set up an Ubuntu 14.04 machine to build Android

####Install OpenSSL, for Python:
```

$ sudo apt-get install libssl1.0.0=1.0.1-4ubuntu5.3
$ sudo apt-get install libssl-dev
```

####Build Tools
```

$ sudo apt-get install git-core gnupg flex bison gperf build-essential \
  zip curl zlib1g-dev zlib1g-dev:i386 libc6-dev lib32ncurses5-dev \
  ia32-libs x11proto-core-dev libx11-dev:i386 libreadline6-dev:i386 \
  lib32z-dev libgl1-mesa-dev g++-multilib mingw32 \
  tofrodos python-markdown libxml2-utils xsltproc readline-common \
  libreadline6-dev libreadline6 lib32readline-gplv2-dev libncurses5-dev \
  lib32readline5 lib32readline6 libreadline-dev libreadline6-dev:i386 \
  libreadline6:i386 bzip2 libbz2-dev libbz2-1.0 libghc-bzlib-dev lib32bz2-dev \
  libsdl1.2-dev libesd0-dev squashfs-tools pngcrush schedtool libwxgtk2.6-dev
```
####If you have issues running apt, try aptitude;
```
$ sudo apt install aptitude
```
####and then try 
```
$ sudo aptitude install git-core gnupg flex bison gperf build-essential \
  zip curl zlib1g-dev zlib1g-dev:i386 libc6-dev lib32ncurses5-dev \
  ia32-libs x11proto-core-dev libx11-dev:i386 libreadline6-dev:i386 \
  lib32z-dev libgl1-mesa-dev g++-multilib mingw32 \
  tofrodos python-markdown libxml2-utils xsltproc readline-common \
  libreadline6-dev libreadline6 lib32readline-gplv2-dev libncurses5-dev \
  lib32readline5 lib32readline6 libreadline-dev libreadline6-dev:i386 \
  libreadline6:i386 bzip2 libbz2-dev libbz2-1.0 libghc-bzlib-dev lib32bz2-dev \
  libsdl1.2-dev libesd0-dev squashfs-tools pngcrush schedtool libwxgtk2.6-dev
```

####When that's done installing enter 
```
$ sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
```
####Configure USB (Android 51 Rules)
```
sudo curl --create-dirs -L -o /etc/udev/rules.d/51-android.rules -O -L https://raw.githubusercontent.com/snowdream/51-android/master/51-android.rules; sudo chmod a+r /etc/udev/rules.d/51-android.rules; sudo service udev restart
```
####Setup Java
```
$ sudo apt install openjdk-7-jdk 
```
####Java PATHs open .bashrc in text editor
```
#Java
export JAVA_HOME=/usr/bin/java
export PATH=$PATH:$JAVA_HOME/bin
```
####Install python

-> For 2.7 you need to explicitly enable SSL after running the ./configure script and before running make: 
```
$ sudo apt-get install build-essential gcc
$ wget http://www.python.org/ftp/python/2.7.6/Python-2.7.6.tgz
$ tar -xvzf Python-2.7.6.tgz
$ cd Python-2.7.6
$ ./configure --prefix=/usr/local/python2.7
$ make
$ sudo make install
$ sudo ln -s /usr/local/python2.7/bin/python /usr/bin/python2.7
```
####OPTIONAL to set up your Android SDK easily and also download Android Studio
```
$ sudo apt-add-repository ppa:paolorotolo/android-studio; 
$ sudo apt update
$ sudo apt install android-studio
```

####Add to .bashrc
```
# Python
export PATH=/usr/bin:$PATH
```

####Add SDK to .bashrc
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
####Install the Repo:
```
$ mkdir ~/bin
$ PATH=~/bin:$PATH
$ curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
```
#Reboot.
