RosettaBuild
============
#Android Build Environment:

####Install Oracle:
####Open terminal (CTRL + ALT + T)

```
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java6-installer oracle-java6-set-default
```
##done

####Installing Python from source
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ sudo apt install build-essential gcc python-software-properties libssl-dev
$ wget http://www.python.org/ftp/python/2.7.6/Python-2.7.6.tgz
$ tar -xvzf Python-2.7.6.tgz
$ cd Python-2.7.6
$ ./configure --prefix=/usr/local/python2.7
$ make
$ sudo make install
$ sudo ln -s /usr/local/python2.7/bin/python /usr/bin/python2.7
```

##done.

####install make from source
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ wget http://ftp.gnu.org/gnu/make/make-3.81.tar.gz
$ tar -xvzf make-3.81.tar.gz
$ cd make-3.81
$ ./configure
$ sudo make install
```

##done.

####Git:
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ sudo apt install git
```
####Configure Git:
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ git config --global user.email "<your email address here>"
$ git config --global user.name "<your user name here>"
```
##done.

####Android SDK:
####Download the SDK here: http://developer.android.com/sdk/index.html
####Extract the SDK and place it in your home directory.
####Mine is located in
```
 ~/android-sdks
```
####Go to your home folder, press Ctrl+H to show hidden files, and open up your ~/.bashrc file (or execute from sudo with your chosen text editor):
####Add these lines at the bottom of the file:
```
# Android tools
export PATH=${PATH}:~/android-sdks/tools
export PATH=${PATH}:~/android-sdks/platform-tools
export PATH=${PATH}:~/bin
```
####Find your ~/.profile file and add this at the bottom of the file (execute from sudo with your chosen text editor):
```
PATH="$HOME/android-sdk/tools:$HOME/android-sdk/platform-tools:$PATH"
```
##done.

####Installing required packages needed for Ubuntu 14.04:
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ sudo apt install bison python git-all gcc-arm-linux-androideabi gcc-i686-linux-android android-copyright abootimg android-headers android-src-vendor android-tools-fsutils android-tools-adbd bzip2 curl dpkg-dev flex g++-multilib git git-review gnupg gperf lib32bz2-1.0 lib32bz2-dev lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev libbz2-1.0 libbz2-dev libc6-dev libghc-bzlib-dev libgl1-mesa-dev libgl1-mesa-glx:i386 libncurses5-dev libreadline6-dev libreadline6-dev:i386 libx11-dev:i386 libxml2-utils lzop mingw32 pngcrush python-markdown schedtool squashfs-tools tofrodos x11proto-core-dev xsltproc zip zlib1g-dev zlib1g-dev:i386 phablet-tools
```
###**Optional packages if your the cautious type**
```
$ sudo aptitude install uuid uuid-dev zlib1g-dev liblz-dev liblzo2-2 liblzo2-dev libperl-dev libperl-apireference-perl libperl5.18 libperl6-caller-perl libperlio-gzip-perl libperl4-corelibs-perl libperl5i-perl perl perl-base libxml-perl libfile-find-rule-perl-perl libprobe-perl-perl libmodern-perl-perl perl-modules  
```
##done.

####Remove OpenJDK:
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ sudo apt purge openjdk-\* icedtea-\* icedtea6-\*
```
###Create a symbolic link of libGL.so.1:
```
$ sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
```
##done.

####Configure your USB:
####Create your 51 Android Rules
####Open terminal (CTRL + ALT + T)# 
####Then execute the following commands in terminal one by one:
```
$ sudo curl --create-dirs -L -o /etc/udev/rules.d/51-android.rules -O -L https://raw.githubusercontent.com/snowdream/51-android/master/51-android.rules
$ sudo chmod a+r /etc/udev/rules.d/51-android.rules
$ sudo service udev restart
```
##done.

####install repo:
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ mkdir ~/bin
$ PATH=~/bin:$PATH
$ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
```
####done.

###Recommended to reboot your computer now. 

####**(Optional)**

####**Installing and setting up ccache**
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ sudo apt install ccache
```
####cd to 
```
~/prebuilts/misc/linux-86/ccache
```
####set your ccache 
```
$ ccache -M 75G 
```
####you can set yours to whatever you want but it is recommended to use atleast 65 gigs
####Lastly add ccache to your export at the end of your ~/.bashrc file
```
export USE_CCACHE=1
```
####**To use Linaro Toolchains **(optional)**:
####Open terminal (CTRL + ALT + T)
####Then execute the following commands in terminal one by one:
```
$ sudo add-apt-repository ppa:linaro-maintainers/tools; 
$ sudo apt update
$ sudo apt install linaro-image-tools
```
####in your home folder cd to your prebuilts folder from the top of the work tree
```
~/prebuilts/gcc/linux-x86/arm
```
####Download the toolchains (as of 10-25-2014)
```
$ wget http://releases.linaro.org/latest/components/android/toolchain/4.9/android-toolchain-eabi-4.9-2014.09-x86.tar.bz2
$ bunzip2 *.tar.bz2; tar -xvf *.tar
```
####then inside your home folder, goto your build folder and open the envsetup.sh file 
####after the section that begins with 
####"**export ANDROID_EABI_TOOLCHAIN=:**" 
####on the "arm" line, 
#####Change 
```
arm) toolchaindir=arm/arm-linux-androideabi-$targetgccversion/bin
```
to 
```
arm) toolchaindir=arm/android-toolchain-eabi/bin
```
####done.
