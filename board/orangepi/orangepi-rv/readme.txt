OrangePi RV
====================

The OrangePi RV is a low-cost RISC-V 64-bit based platform, powered by a
Starfive JH7110 processor.

http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-RV.html

How to build
============

$ make orangepi_rv_defconfig
$ make

Once the build process is finished you will have two images
in the output/images/ directory:
- sdcard.img
- spi-nor.img

How to write the SPI NOR flash
=============================

If you have a booting device use u-boot and tftp:

  # tftpboot 0x82000000 spi-nor.img
  # sf probe
  # sf update 0x82000000 0x0 {filesize}

Otherwise, follow the recovery instruction:

https://doc-en.rvspace.org/VisionFive2/Quick_Start_Guide/VisionFive2_SDK_QSG/recovering_bootloader%20-%20vf2.html

How to write the SD card
========================

Copy the bootable "sdcard.img" onto an SD card with "dd":

  $ sudo dd if=output/images/sdcard.img of=/dev/sdX
