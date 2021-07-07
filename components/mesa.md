---
label: Mesa
icon: pulse
order: -100
---

Gallium HUD
------------

"It’s a highly customizable Heads-Up Display (HUD) capable of displaying some extremely helpful information.

The hud is part of Mesa, so if you’re using the open-source drivers you’re ready to use it without any external package."

> Source : https://manerosss.wordpress.com/2017/07/13/howto-gallium-hud/

On Android-x86, Gallium HUD can be enabled on Mesa 18.1+ if you are using AMD GPUs or Nvidia GPUs (nouveau). On Intel GPUs, Gallium HUD can be enabled on Gen8+ using Mesa's new `iris` graphic driver. On older Intel GPUs, with the new `crocus` driver you can now be able to use it too.

For all Intel GPUs I recommend using the upcoming Mesa 21.2 if you want to try to experience this feature. 
If you wonder which Intel GPU you are using (different from CPU gen) then you can check this wikipedia page : https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units

To easily activate Gallium HUD on any Android-x86 build, go to `/system/etc/init/surfaceflinger.rc`

<image_placeholder> 

Add this line into the file : 
```
  setenv GALLIUM_HUD <value>
```
This is the main environment variable to activate the hud. 


There are other optional variables you can set as well
```
  setenv GALLIUM_HUD_PERIOD <value> //sets the HUD update rate in seconds. Use zero to update every frame.
  setenv GALLIUM_HUD_SCALE <value> //Scale HUD by an integer factor, for high DPI displays. Default is 1.
  setenv GALLIUM_HUD_DUMP_DIR <value> //specifies a directory for writing the displayed HUD values into files. (aka dump fps or some info into a file)
```
To know which value to set in each variables, you can read this post as a reference, it shows very detail about how you can customize the HUD.
https://manerosss.wordpress.com/2017/07/13/howto-gallium-hud/

***NOTE : There seems to be no document relate to `GALLIUM_HUD_SCALE` so please report to us if you know how to use it***

For example, these are the variables I use
```
    setenv GALLIUM_HUD cpu+fps
    setenv GALLIUM_HUD_PERIOD 0.1
```

After decide which one to use and customize your own HUD, save the edit and then reboot.

You will see the HUD on the position you set (default is on the left side)

<image_placeholder>

