---
title: Installation
media_order: download_gearlock_step.png
taxonomy:
    category:
        - docs
---

So here we gonna learn ways of installing GearLock in your desired android-x86 system. There are several ways of doing so, you just need to pay some attention and read everything properly to avoid errors.

# Method 1: Directly from installer-binary

##### Get the latest GearLock installer binary

Simply head over to [this](https://supreme-gamers.com/r/gearlock-custom-recovery-replacement-for-android-x86.40) link and click on **Download** button.
![](download_gearlock_step.png)

##### Place the binary anywhere inside android filesystem

In this guide we will put `gearlock` installer-binary at either **Main Storage** or **Internal Storage** or **/sdcard** from a file manager.

I'm using [FX File Explorer](https://fx-file-explorer.en.uptodown.com/android) for moving `gearlock` installer-binary to **Main Storage** (aka the **Internal Storage**) from my **Downloads** folder.

##### Switch to command terminal / console

Now press either `Alt + F1` or `fn + Alt + F1` for switching to a command terminal. (If the buttons are not working then move to #Method 2)

Once you're in a black terminal prompt, type in the following and press **Enter** key after each line.

```bash
cp /sdcard/gearlock /data
cd /data
chmod 777 gearlock
./gearlock
```

# Todo ....