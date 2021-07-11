---
label: Gathering Logs
icon: database
order: -400
---

## GearDump automated log gathering

GearDump is an automated log collection tool to help boost the debugging process on user-reported issues. It was originally made for GearLock but now it can be helpful for the whole operating-system log collection as well.

* Press ALT+F1 or use any terminal [emulator](https://play.google.com/store/apps/details?id=com.termoneplus)/tty.
* Run `geardump` command.
* Then you can find the **zipball** at both `/data` and at the root of your `operating-system-Partition`. You may grab it from one of these suitable locations in your favor.

## Manual log gathering

=== Getting into a terminal

Manual log gathering is useful when you can not run `geardump`.

First of all you will need to get into a terminal where you can execute commands.

+++ On Booted System (GUI)
Press `Alt + F1` or `fn + Alt + F1`(laptop)

If that is not working then install [TermOneplus](https://play.google.com/store/apps/details?id=com.termoneplus) app and open it.

Then run `su` in **TermOneplus** app.

+++ On Recovery Mode
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
Logcat does not run in recovery-mode

You can only run it after the `android` bootanimation. (Aka android-interface)
!!!

```bash
logcat > logcat.log
```

=== Making an archive of the logs

Assuming that you are in `/data/mylogs` directory as instructed above.

Run the following command while being in `/data/mylogs`:

```bash
tar -cf logs.tar *
```

===
