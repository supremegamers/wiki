---
title: 'Grub Installation'
---

Here we are gonna learn how to install grub from both Windows and Linux. Please note that it is recommended to know how to use terminal or CMD and basic knowledge of partition in order to install grub. If you don't know how, consider switching to Grub2Win.

## Getting grub
If your in Linux theres a high chance that grub-install is already there. If your in windows, well you can tell the Linux users "Lazy". Goto to  [this](https://ftp.gnu.org/gnu/grub) and download the packages that end with `windows.zip`.

## Preparation
Before we proceed to install grub we need to prepare a location for grub to be installed. The partition where grub is going to be installed is needed to be mounted. For windows it needs to be mounted with letter and for Linux it's a directory

### Windows
For windows the partition is usually mounted unless its a special partition like EFI Partition. To mount the partition if its not mounted press `Winkey + R`  to start run. There type `diskmgmt.msc` and hit OK.

Now a window will pop up and show all the disks and partition after loading. Right click the desired partition and select assign letter. Here we will assign the epic letter Z

### Linux
For Linux if its not EFI partition or root partition, in most cases it needs to be mounted. Suppose we want to mount the partition `sda1` on `/mnt/grub`. Now open up terminal and type these command.
```bash
sudo su
mkdir /mnt/grub
mount /dev/sda1 /mnt/grub
```
And thats it!

## Installation
Now the installation process for both windows and Linux is almost the same. You just need to specify installation target differently and also specify your firmware is legacy or UEFI. Suppose we want to install grub under boot folder on the target partition and. Now start terminal or CMD as administrator and type one of the commands according to your system.

Note: Index of drives can be found in `diskmgmt.msc` for windows

### Windows
To install grub on our first disk which is disk 0 according to `diskmgmt.msc` we need to specify disk as   `\\?\PhysicalDrive0`
```bash
#For installing as Legacy system on disk0
grub-install.exe  \\?\PhysicalDrive0 --target=i386-pc --boot-directory=Z:\boot

#For installing as UEFI 32bit system on disk0
grub-install.exe  \\?\PhysicalDrive0 --target=i386-efi --boot-directory=Z:\boot --efi-directory=A:\

#For installing as UEFI 32bit system on disk0
grub-install.exe  \\?\PhysicalDrive0 --target=x86_64-efi --boot-directory=Z:\boot --efi-directory=A:\

#For installing as Legacy system on disk0 which is USB 
grub-install.exe  \\?\PhysicalDrive0 --target=i386-pc --boot-directory=Z:\boot --removable

#For installing as UEFI 32bit system on disk0 which is USB 
grub-install.exe  \\?\PhysicalDrive0 --target=i386-efi --boot-directory=Z:\boot --efi-directory=A:\ --removable

#For installing as UEFI 64bit system on disk0 which is USB 
grub-install.exe  \\?\PhysicalDrive0 --target=x86_64-efi --boot-directory=Z:\boot --efi-directory=A:\ --removable
```
Note: Here `A:\` is the EFI partition of the disk
### Linux
To install grub on our first disk which is disk 0 we need to specify disk as   `/dev/sda`
```bash
#For installing as Legacy system on disk0
grub-install  /dev/sda --target=i386-pc --boot-directory=/mnt/grub/boot

#For installing as UEFI 32bit system on disk0
grub-install  /dev/sda --target=i386-efi --boot-directory=/mnt/grub/boot -efi-directory=/boot/efi

#For installing as UEFI 64bit system on disk0
grub-install  /dev/sda --target=x86_64-efi --boot-directory=/mnt/grub/boott -efi-directory=/boot/efi

#For installing as Legacy system on disk0 which is USB 
grub-install  /dev/sda --target=i386-pc --boot-directory=/mnt/grub/boot --removable

#For installing as UEFI 32bit system on disk0 which is USB 
grub-install  /dev/sda --target=i386-efi --boot-directory=/mnt/grub/boott -efi-directory=/mnt/grub --removable

#For installing as UEFI 64bit system on disk0 which is USB 
grub-install /dev/sda --target=x86_64-efi --boot-directory=/mnt/grub/boott -efi-directory=/mnt/grub --removable
```
Note: 
1 Here `/mnt/grub` is the EFI partition of the disk. In case if its installed on same disk as where Linux is, it is usually mounted on `/boot/efi`

2 `i386-pc` for legacy system, `i386-efi` for 32bit EFI system, `x86_64-efi` for 64bit EFI system. If the target partition is removable drive like USB, add  --removable.

3 Index of drives can be found in `diskmgmt.msc` in start menu for windows

And thats it! We have successfully installed grub. But by default grub doesn't generate any configuration file. This file is easy to generate in Linux but not so in windows(Lazy). On next page, we will learn how to configure grub configuration file. Now if you try to boot grub, it will stop at grub shell if installation was successful. Else it will stop at grub-rescue shell which has only some basic functionality to fix and reach the shell.
