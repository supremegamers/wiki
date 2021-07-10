---
label: Booting
icon: issue-reopened
order: -100
---

In this page we will try to cover the most common booting issues people face.

## Grub2Win Boot Entry Missing

If your `PhoenixOS DarkMatter` grub2win entry is missing from the boot-menu then you can follow this.

- Open `C:/grub2/grub.cfg` with a text editor (Notepad++)

- Copy and paste this code at the bottom of that file.

```bash
#  Sub Menu Entry       DarkMatter-Exo4.7
#
submenu   'DarkMatter-Exo4.7'  --class submenu --class icon-asg {
     #
     source $prefix/windata/customconfigs/DarkMatter-Exo4.7.cfg
     #
}
```

- Download the file below and copy in `C:/grub2/windata/customconfigs`

[!file](../DarkMatter-Exo4.7.cfg)
