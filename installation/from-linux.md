---
label: Linux
icon: ":penguin:"
order: 100
---

Android-x86 is just a highly modified Linux. As a result, it has lot of similarities with Linux. So installing Android-x86  from Linux is easier than installing from Windows where only limited number of File-System is supported. Here We will learn `How to install Androidx86 from Linux`. As a Linux user, basic command line knowledge is expected. This guide is mainly focused on `Ext4` and `NTFS` File-System. Both can be done on any.

## Preparation

To install Android-x86 we are gonna need 4 things.

1. The boot-loader or Grub
2. The ISO of course
3. Basic terminal knowledge

## Step-1 The Android-x86 Folder

Android-x86 can be booted from root of partition or from any folder or sub-folder. We are gonna install it in a sub-folder `Android_x86` in `App` folder in our target drive. After creating the folder copy the `kernel`,`ramdisk.img`,`system.img/system.sfs`,`initrd.img`,`gearlock`(if exists) from the ISO to the folder. 

And that's step-1.

## Step-2 The Data Partition

Since Android-x86 is Linux inside, it natively supports `Ext4`. So we can just make a folder named `data` in our `Android-x86` folder.

### Note for OtherFS

You need to create `data.img` as Android-x86 being a striped down Linux, natively supports only `ext4` File-System. So just a folder named `data` will not do. To create `data.img`

```
# Use dd to create data.img
dd if=/dev/zero of=./data.img bs=8G count=0 skip=1
# Replace 8G with whatever size you want

# Format the file with ext4 filesystem
mkfs.ext4 ./data/img
```

!!!warning Warning
Please don't use `data.img` of one installation on another. Create a fresh data on every install. Or the system might not boot.
!!!

## Step-3 The Bootloader

Now the last part. Install Grub2 and open `nano` or some text-editor as root. Edit the file `/boot/grub/grub.cfg` and add these line to the end.

```
menuentry 'Android-x86' {
set android=/FOLDER_NAME
insmod all_video 
search --set=root --file $android/kernel 
linux $android/kernel quiet root=/dev/ram0 androidboot.selinux=permissive acpi_sleep=s3_bios,s3_mode SRC=$android
initrd $android/initrd.img
}
```

At first line, replace `Android-x86` with what ever you want to show at Grub menu. And replace FOLDER_NAME with the folder path to your Android-x86 system. For this case it is `/App/Android_x86`. Add any kernel configuration you have after `SRC=$android`in same line. 

!!!warning Warning
Pleas be extra careful as failing to write properly might make grub menu not accessible. This will lead to grub shell.
!!!

## Step-4 Another Step?

No this is just some warnings and tips for your better experience.

1. There is no such thing as best Android-x86. If the system runs slow, try changing the kernel/mesa or apply some tweaks from `gearlock` or `lspeed`,`FDE`.
2. There is no such thing as best kernel/mesa. Each device works with specific kernel. Some devices works on all. And there's no magic word to tell which will work for your device. Just pick 4.19 series of kernel and mesa 18 and try to go up and down.
3. If you got NVidia GPU, pray to God that it works or just use emulator if GPU is good enough.
4. Install kernel/mesa from `gearlock recovery`.



Happy Gaming ;)

