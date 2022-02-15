---
title: 'rEFInd'
taxonomy:
    category:
        - docs
---
### What is rEFInd?
rEFInd is a GUI based boot manager for UEFI and EFI-based machines. It can be used to boot multiple operating systems that are installed on a single device. It also provide some basic theme Customisation options.


# Installation
Now we are gonna learn how to install rEFInd from both Windows and Linux. Please note that it is recommended to know how to use terminal and have basic knowledge of partition in order to install rEFInd.

## Getting rEFInd
If you'r in Linux you can use [terminal-installation](#goto2)(recommended) or even install it manually from [here](https://sourceforge.net/projects/refind/files/)(downlaod latest zip file). If you'r in windows, you have to install refind packages and some other softwares manually. Install rEFInd from [here](https://sourceforge.net/projects/refind/files/)(downlaod latest zip file) and EasyUEFI from [here](https://getintopc.com.pk/softwares/utilities/easyuefi-technician-free-download/).

## <a name="goto1">Preparation</a>
Before moving forward we first need to do some minor preparation for both Windows and Linux users who want to install rEFInd manually. After downlading rEFInd package, Extract it to your Desktop and rename it to "refind", open it, edit `refind.conf` and add the following text at the end of the file.
```
menuentry "Darkmatter" {
    volume 
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
8) Lastly click on <b>Home</b> button and then close the EasyUEFI program.

#### If rEFInd does't bootup
Reboot to bios and select `boot Sequence`.If refind is already on the top of every other boot entry then click on save else select refind, click up arrow untill refind reaches the top of all other boot entries and then Save it.

## Linux Installation
You can install rEFInd on linux via terminal or even manually.
### <a name="goto2">Install through terminal</a>
1) Press ``CTRL + ALT + T`` to open terminal and then type these commands-
``` 
# for Ubuntu and Debain users

sudo apt install refind    

# for Arch linux users

sudo pacman -S refind

```
> If you're fedora, Mageia or other linux user then follow these steps-
> 1) Go to this [link](https://sourceforge.net/projects/refind/files) and download latest `rpm` or `deb` file according to your system.
> 2) If you install `rpm` file then cd to file and type ```sudo rpm -i refind*.rpm``` 
> 3) If you install `dbm` file then cd to file and type ```sudo dpkg -i refind*.deb```

rEFInd instllation start automatically if not then type-
```
sudo refind-install
```
2) Now after your rEFInd is installed on your distro, open any filemanager as root and navigate to `/boot/efi/EFI/refind`.
3) Edit `refind.conf` and add following text at the end of the file-
``` 
menuentry "Darkmatter" {
    volume 
    loader /kernel
    initrd /initrd.img
    options "root=/dev/ram0 androidboot.hardware=android_x86_64 androidboot.selinux=permissive SRC=/"
}
```
Edit the location of required files if you have installed your OS in any other custom location.

4) Save the file and reboot.

### Install manually
If you done all [Preparation](#goto1), follow these steps-
1) Copy "refind" folder we extracted in Desktop.
2) Open any filemanger as root and copy "refind" file to `/boot/efi/EFI/refind`.
4) now reboot to bios and select `boot Sequence`, click on <b>New Entry</b> button and name it "refind" and select location of the boot file `/EFI/refind/refind_x64.efi` for 64 bit or `\refind\refind_ia32.efi` for 32 bit CPUs.
5) Now click on save, select refind and click up arrow untill refind reaches the top of all other boot options.
6) Now reboot!


## Finally!!
And thats it! We have successfully installed rEFInd.
