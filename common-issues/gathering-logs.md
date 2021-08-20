---
label: Gathering Logs
icon: database
order: -400
---

## GearDump automated log gathering

GearDump is an automated log collection tool to help boost the debugging process on user-reported issues. It was originally made for GearLock but now it can be helpful for the whole operating-system log collection as well.

- Press ALT+F1 or use any terminal [emulator](https://play.google.com/store/apps/details?id=com.termoneplus)/tty.
- If you can't boot into the android-GUI then get into recovery mode from your grub menu and open `Virtual Command Terminal` there.
- Run `geardump` command.
- Then you can find the **zipball** at both `/data` and at the root of your `operating-system-Partition`. You may grab it from one of these suitable locations in your favor.

## Manual log gathering

=== Getting into a terminal

Manual log gathering is useful when you can not run `geardump`.

First of all you will need to get into a terminal where you can execute commands.

+++ On Booted System (GUI)
Press `Alt + F1` or `fn + Alt + F1`(laptop)

If that is not working then install [TermOneplus](https://play.google.com/store/apps/details?id=com.termoneplus) app and open it.

Then run `su` in **TermOneplus** app.

+++ On Recovery Mode (When you can't boot into android-interface)
- Boot into recovery mode from grub
- Select option `3. Open Virtual Command Terminal`

+++

===

=== Create a working directtory

We will create a directory and save all the logs there.

```bash
mkdir -p /data/mylogs
cd /data/mylogs
```

Now you can proceed with grabing logs from the components stated below.

===

### dmesg

```bash
dmesg > dmesg.log
```

### lsmod

```bash
lsmod > lsmod.log
```

### lsusb

```bash
lsusb > lsusb.log
```

### logcat

!!!warning Warning
Logcat does not work in recovery-mode.
**Normally** you can only run it after the `android` bootanimation. (Aka android-interface)
!!!

```bash
logcat > logcat.log
```

=== Making an archive of the logs

Assuming that you are in `/data/mylogs` directory [as instructed above](#create-a-working-directtory).

Run the following command while being in `/data/mylogs`:

```bash
tar -cf logs.tar *
```

===

Now lets find the archived `logs.tar` file for uploading to a dev

+++ From Booted Android System

Run the following command in your terminal:

```bash
cp /data/mylogs/logs.tar /sdcard
```

Then you can find it on your `Internal Storage` from a file-manager.

+++ From Linux

- Mount your Android-x86 partition
- If you have a directory called `data` inside it then you should find `logs.tar` at `data/mylogs`
- Or if you have `data.img` then mount it with the following command and look at `dmount/mylogs` for `logs.tar`:

```bash
mkdir dmount
sudo mount -oloop,ro data.img dmount
```

+++ From Windows

- Open the folder where you have Android-x86 installed.
- If you have `data.img` then use [7-zip](https://www.7-zip.org/download.html) to open it.
- If you have `data` folder then open it normally.
- Look for a folder called `mylogs` and you should find `logs.tar` there.

!!!info Ext4 on Windows
If you had installed Android-x86 inside an **Ext4** partition from Windows then use the appropriate program to mount it.
E.g **Paragon LinuxFS**, **Ext2fsd**
!!!

+++
