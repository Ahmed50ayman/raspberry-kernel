## Linux kernel for Raspberry Pi
This is linux kernel v4.4.35 for rasberry pi devices. in this version we added 
android config files and you can build this kernel for android os.

<img src="https://www.tech2max.com/wp-content/uploads/image.jpg" />

## Pending Features
1 . working on quick boot for (Android , Yocto , Buildroot) systems </br>
2 . adding special system call for direct device controlling </br>
3 . adding a new schuduler subsystem for better performance in Arm </br>


## How to build for Raspberry PI 3
With this commands , you will be able to build this kernel and 
Generate zImage and Kernel Modules. before running this commands , please make sure , 
you installed an Arm toolchain (arm-linux-gnueabihf). you can install toolchain by these commands :

* Ubuntu/debain/mint
````
 $ sudo apt install gcc-arm-linux-gnueabihf
````
* Fedora 
````
 $ sudo yum install gcc-arm-linux-gnueabihf
````
After Installing toolchain , use this commands to build
````
 $ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2709_defconfig 
 $ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs
````
for Installing Kernel Modules
````
  $ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- INSTALL_MOD_PATH=path/to/rootfs modules_install </br>
````
for cleanning the source and remove all built files
````
  $ make clean all 
````

## How to build Android kerenl for Raspberry PI 3
This Command is for bulding Linux kernel for Android OS.
for better performance in Building , use j [ your host computer cpu core count * 2] , 
for example for a 2-core pc we use -j 4 Argument in make.

````
$ ARCH=arm scripts/kconfig/merge_config.sh arch/arm/configs/bcm2709_defconfig android/configs/android-base.cfg android/configs/android-recommended.cfg </br>
$ ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- make zImage dtbs </br>
````
## Author 
Nima Mohammadi
