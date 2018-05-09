OpenWRT attitude_adjustment_2018
================================

This branch includes fixes and instructions to build this 
old Openwrt release in modern environments (after 2018 at last) and specially 
considering old feeds that is currently deprecated and 
moved to different URLs.

# Change notes

## hotplug2 hash

For some reason this feed package has a different hash in current 
URLs than expected in feed Makefile.
Be aware to unexpected behaviours from this feed since we're
using a different version from the one used in 2014.

# Compiling Environment

## Basic Recipe

To build any OpenWRT image you need to install C/C++ compilers,
some libs and tools.
A basic recipe example is this one that can be used in an
Ubuntu/Debian Linux distribution:

```
sudo apt-get update
sudo apt-get install -y git-core subversion mercurial build-essential libssl-dev libncurses5-dev unzip gawk binutils bzip2 flex gcc util-linux tar zlib1g-dev make genisoimage gettext quilt gcc-multilib
```

## GCC 5

Current Linux distributions comes with gcc-5.x or later, 
that has many differences from previous versions, specially 
concerning reserved words and macros, that works in previous
gcc versions but not in gcc-5 anymore.
To workaround this you it's necessary to use a previous gcc
version. 
We know that any gcc-4.x works. 

In Linux systems you can install gcc alternatives and select
the one you want to use when compiling OpenWRT.
Refer https://askubuntu.com/questions/26498/choose-gcc-and-g-version?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa
to check out how to do it.

# Image Build

After compiling environment configurations you can build
your OpenWRT image as usual, referenced in original README.

```
git clone git@github.com:INTV-Brasil/archive.git -b attitude_adjustment_2018
cd archive
./scripts/feeds update -a
./scripts/feeds install -a
make menuconfig
make
```



    