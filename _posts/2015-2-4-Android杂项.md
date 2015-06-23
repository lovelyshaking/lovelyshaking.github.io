---
layout: post
title: Android 杂项
---

1. android 关机命令  reboot -p
2. 关于android分区
        物理分区表查看在  /proc/parstition 下 
        逻辑分区与物理分区映射关系在  /dev/block/platform/XX/by-name 下  ls -l就可查看
        misc 分区 保存设备配置信息:CID (Carrier or Region ID),USB和其它硬件设备配置信息
 

Let’s start with a list of standard internal memory partitions on Android phones and tablets. These are:

    /boot
    /system
    /recovery
    /data
    /cache
    /misc

In addition, there are the SD card partitions.

    /sdcard
    /sd-ext

Note that only /sdcard is found in all Android devices and the rest are present only in select devices. Let’s now take a look at the purpose and contents of each of these partitions.

/boot

This is the partition that enables the phone to boot, as the name suggests. It includes the kernel and the ramdisk. Without this partition, the device will simply not be able to boot. Wiping this partition from recovery should only be done if absolutely required and once done, the device must NOT be rebooted before installing a new one, which can be done by installing a ROM that includes a /boot partition.

/system

This partition basically contains the entire operating system, other than the kernel and the ramdisk. This includes the Android user interface as well as all the system applications that come pre-installed on the device. Wiping this partition will remove Android from the device without rendering it unbootable, and you will still be able to put the phone into recovery or bootloader mode to install a new ROM.

/recovery

The recovery partition can be considered as an alternative boot partition that lets you boot the device into a recovery console for performing advanced recovery and maintenance operations on it. To learn more about this partition and its contents, see the ‘About Android Recovery’ section of our guide to ClockworkMod recovery.

/data

Also called userdata, the data partition contains the user’s data – this is where your contacts, messages, settings and apps that you have installed go. Wiping this partition essentially performs a factory reset on your device, restoring it to the way it was when you first booted it, or the way it was after the last official or custom ROM installation. When you perform a wipe data/factory reset from recovery, it is this partition that you are wiping.

/cache

This is the partition where Android stores frequently accessed data and app components. Wiping the cache doesn’t effect your personal data but simply gets rid of the existing data there, which gets automatically rebuilt as you continue using the device.

/misc

This partition contains miscellaneous system settings in form of on/off switches. These settings may include CID (Carrier or Region ID), USB configuration and certain hardware settings etc. This is an important partition and if it is corrupt or missing, several of the device’s features will will not function normally.

/sdcard

This is not a partition on the internal memory of the device but rather the SD card. In terms of usage, this is your storage space to use as you see fit, to store your media, documents, ROMs etc. on it. Wiping it is perfectly safe as long as you backup all the data you require from it, to your computer first. Though several user-installed apps save their data and settings on the SD card and wiping this partition will make you lose all that data.

On devices with both an internal and an external SD card – devices like the Samsung Galaxy S and several tablets – the /sdcard partition is always used to refer to the internal SD card. For the external SD card – if present – an alternative partition is used, which differs from device to device. In case of Samsung Galaxy S series devices, it is /sdcard/sd while in many other devices, it is /sdcard2. Unlike /sdcard, no system or app data whatsoever is stored automatically on this external SD card and everything present on it has been added there by the user. You can safely wipe it after backing up any data from it that you need to save.

/sd-ext

This is not a standard Android partition, but has become popular in the custom ROM scene. It is basically an additional partition on your SD card that acts as the /data partition when used with certain ROMs that have special features called APP2SD+ or data2ext enabled. It is especially useful on devices with little internal memory allotted to the /data partition. Thus, users who want to install more programs than the internal memory allows can make this partition and use it with a custom ROM that supports this feature, to get additional storage for installing their apps. Wiping this partition is essentially the same as wiping the /data partition – you lose your contacts, SMS, market apps and settings.

With this, we conclude our tour of Android partitions. Now whenever you install a ROM or mod that requires you to wipe certain partitions before the installation, you should be in a better position to know what you’re losing and what not and thus, you’ll know what to backup and what not.
