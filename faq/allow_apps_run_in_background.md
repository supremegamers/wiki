---
label: Allow Apps Run in the Background
icon: question
---

By default android battery saving patterns reduce the background activities of running apps unless they are explicitly excluded in framework level or via android-settings battery-optimization panel if in favor.

Here I will show some **possible** methods to keep background apps alive. Please note that this is specific to the android-x86 platform.

## On Android-x86

- Open `Settings` app from your **app menu**.
- Find the option which says `Battery`.
- Look for a button called `Battery Optimization`. This can be found in different forms, such as:
	- Clicking on the top right toggle with three-dots.
	- Checking the `Advanced Settings` (Mostly in Android-Pie{9}+)
- Once you are in the `Battery Optimization` page, select `Not Optimized` from the top-menu.
- Later you can select any app to disable battery-optimization for it and it should stay alive in the background afterwords.

## On BlissOS-x86

Same instructions as [Android-x86](#on-android-x86)

## On PhoenixOS-x86

- Open `Security` app from your **app-menu**.
- Select `Autostart` menu.
- Toggle on any app you wish to keep alive in the background.
