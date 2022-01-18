---
title: 'rEFInd Installation'
taxonomy:
    category:
        - docs
---

Here we are gonna learn how to install rEFInd from both Windows and Linux. Please note that it is recommended to know how to use terminal and have basic knowledge of partition in order to install rEFInd. If you don't know how, just follow evey step exactly like we do.

## Getting grub
If you'r in Linux you can either use terminal(recommended) or even install it manually from [here](https://sourceforge.net/projects/refind/). If you'r in windows, you have to install refind packages and some other softwares manually. Install rEFInd from [here](https://sourceforge.net/projects/refind/) and EasyUEFI from [here](https://getintopc.com.pk/softwares/utilities/easyuefi-technician-free-download/).

## Preparation
Before moving forward we first need to do some minor preparation for both Windows and Linux users. After downlading rEFInd package, Extract it to your Desktop and rename it to "refind", open it, edit `refind.conf` file and paste the following text at the end of the file.
```
menuentry "Darkmatter" {
    icon /EFI/refind/darkmatter.png
    volume /
    loader /kernel
    initrd /initrd.img
    options "root=/dev/ram0 androidboot.hardware=android_x86_64 androidboot.selinux=permissive SRC=/"
}
```
Edit the location of required files if you have installed your OS in any other custom location.

## Windows Installation
If you done downloading all required packages for windows, we're good-to-go for further steps.
1) First extract EasyUEFI to your desktop and copy refind folder to `c:` drive.
2) Setup EasyUEFI on your system and run it as `administrator`.
3) Now open `Manage EFI System Partition` > `EFI System Partition Explorer` in EasyUFI and select your fat32 <b>EFI</b> partition, which is most likely <b>500 MB</b> in size. open it! 
4) Right click on `\` directory and select upload. Now select the `refind` file you copied in `c:` drive and click ok. This will add refind file to `\` directory.
5) Click on <b>Exit</b> > <b>Home</b> to go back to main screen, select `Manage EFI Boot Options` and click on <b>Create new entry</b>(Button with small '+' sign).
6) After new popup appears, setlect the <b>Type</b> as `Unix or Other OS`, Type "refind" in <b>Description</b> and navigate to fat32 <b>EFI</b> partition, select `\refind\refind_x64.efi` for 64 bit or `\refind\refind_ia32.efi` for 32 bit CPUs and click ok to save changes.
7) Now a new boot entry with name "refind" will be created, select it and click on move up(button with small up arrow), click it untill "refind" boot menu reach at the top of all other boot menus. This will set rEFInd as our default bootloader.
8) Lastly click on <b>Home</b> button and then close the EasyUEFI programm.
9) Now reboot to bios and select `boot Sequence`, click on <b>Add New Entry</b> button and name it "refind" and select location of the boot file `/EFI/refind/refind_x64.efi` for 64 bit or `\refind\refind_ia32.efi` for 32 bit GPUs.
10) Now click on save, select refind and click up arrow untill refind reaches the top of all other boot options.
11) Now reboot. This will just install refind, To setup Darkmatter boot entry in rEFInd follow the following steps

## Linux Installation
If you done editing `refind.conf` then start following further steps.
### Install With terminal
If you want to install rEFInd with terminal-
1) Press ``CTRL + T`` to open terminal and type these commands-
``` 
### for Ubuntu users

sudo apt install refind    

### for Arch linux users you can check the official post from ArchWiki (https://wiki.archlinux.org/title/REFInd) 
```
This will just install refind, To setup Darkmatter boot entry in rEFInd follow `## Setup Darkmatter BootEntry`

### Install manually
If you done Download required rEFInd packages, follow these steps-
1) Extract refind file into desktop and rename it to "refind"
2) Open any filemanger as root and copy "refind" file to `/boot/efi/EFI/refind`.
3) now reboot to bios and select `boot Sequence`, click on <b>New Entry</b> button and name it "refind" and select location of the boot file `/EFI/refind/refind_x64.efi` for 64 bit or `\refind\refind_ia32.efi` for 32 bit GPUs.
4) Now click on save, select refind and click up arrow untill refind reaches the top of all other boot options.
5) Now reboot. This will just install refind, To setup Darkmatter boot entry in rEFInd follow `## Setup Darkmatter BootEntry`

## Setup Darkmatter BootEntry
1) now after your rEFInd is installed on your distro, open any filemanager as root and navigate to `/boot/efi/EFI/refind`.
2) Edit `refind.conf` and add these text at the end of the file-
``` 
menuentry "Darkmatter" {
    icon /EFI/refind/darkmatter.png
    volume /
    loader /kernel
    initrd /initrd.img
    options "root=/dev/ram0 androidboot.hardware=android_x86_64 androidboot.selinux=permissive SRC=/"
}
```
Edit the location of required files if you have installed your OS in any other custom location.

3) Now save the file and reboot your system.



## Finally!!
And thats it! We have successfully installed rEFInd.
