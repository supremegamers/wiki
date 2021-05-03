---
title: 'From windows'
taxonomy:
    category:
        - docs
---

Due to how Android-x86 is structured it can be installed in any system. It mainly depends if the boot-loader can boot the system from that File-System. 
Here we are gonna learn how to Install Android-x86 on NTFS. But the process is similar in any File-System.

# Installing on any file-system

## Preparation

To install Android-x86 we are gonna need 3 things.

1. The boot-loader or Grub or Grub2win

2. The ISO of course

3. A tool to create the data.img (For example [makeData](https://mega.nz/file/VxggALRD#_q4_JkkpTe-2s9-1nbI9v_bkwMeDyMmG2DYHLd4G5FY)).


## Step-1 The Android-x86 Folder

Android-x86 can be booted from root of partition or from any folder or sub-folder. We are gonna install it in a sub-folder Android_x86 in App folder in our D drive. After creating the folder copy the kernel,ramdisk.img.system.img/system.sfs,initrd.img,gearlock(if exists) from the ISO to the folder. And thats step-1



## Step-2 The Data Partition

Use any tool or the makeData tool to create data.img file. This will serve as the SD-card for the system. makeData will ask for SD-card size in GB. Provide at least 8 GB for efficient gaming. Now move that created data file to the folder where we copied files from ISO to.



Warning: Pleas don't use data.img of one installation on another. Create a fresh data on every install. Or the system might not boot.



## Step-3 The Bootloader

Now the last part. Install Grub2win from [here](https://sourceforge.net/projects/grub2win/). Pleas don't use any external links as there are reports of malware injected inside them. After installation open Grub2win. Goto "Manage boot menu" and select add entry. Select type as Android, Give a name and at last click the "Select A new Android Kernel File" button. This will open a explorer. Now browse to the folder where we copied the files from ISO and open the kernel file. The texts in box 3 and 4 should change according to your folder. Hit apply and your done.

![image](entry.png)


# Installing on ext file-systems (Advanced)