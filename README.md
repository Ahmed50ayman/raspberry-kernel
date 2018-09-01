# raspberry-kernel

Linux kernel for Raspberry Pi 
<p> This is linux kernel v4.4.35 for rasberry pi devices. in this version we added 
android config files and you can build this kernel for android os. </p>

<h3> Pending Features : </h3>

1 . working on quick boot for (Android , Yocto , Buildroot) systems </br>
2 . adding special system call for direct device controlling </br>
3 . adding a new schuduler subsystem for better performance in Arm </br>


<h3> How to build for Raspberry PI 3 : </h3>
<p> With this commands , you will be able to build this kernel and 
Generate zImage and Kernel Modules. before running this commands , please make sure , 
you installed an Arm toolchain (arm-linux-gnueabihf). you can install toolchain by these commands :

Ubuntu/debain/mint : sudo apt install gcc-arm-linux-gnueabihf </br>
Fedora  : sudo yum install gcc-arm-linux-gnueabihf

</p>

$ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2709_defconfig </br>
$ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs </br>

<h4> for Installing Kernel Modules </h4>
$ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- INSTALL_MOD_PATH=path/to/rootfs modules_install </br>

<h4>  for cleanning the source </h4>
$ make clean all </br>


<h3> How to build Android kerenl for Raspberry PI 3 : </h3>
This Command is for bulding Linux kernel for Android OS. </br>
for better performance in Building , use j [ your host computer cpu core count * 2] , 
for example for a 2-core pc we use -j 4 Argument in make.
</br>

$ ARCH=arm scripts/kconfig/merge_config.sh arch/arm/configs/bcm2709_defconfig android/configs/android-base.cfg android/configs/android-recommended.cfg </br>
$ ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- make zImage dtbs </br>

<h4> Contact us </h4>
nima.mx00@gmail.com
