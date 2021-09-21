---
label: Building a Bigdroid Project
icon: download
order: -100
---

## Prerequisites

- Host utilities:

+++ ArchLinux

```bash
sudo pacman -Sy git curl rsync cpio coreutils e2fsprogs findutils grep wget file squashfs-tools cdrtools p7zip
```

+++ Debian/Ubuntu

```bash
sudo apt install -y git curl rsync cpio coreutils e2fsprogs findutils grep wget file squashfs-tools genisoimage p7zip
```

+++

- [Bashbox](https://github.com/bashbox/bashbox):
```bash
curl --proto '=https' --tlsv1.2 -sSfL "https://git.io/Jc9bH" | bash -s selfinstall
```

- Bigdroid:
```bash
bashbox install bigdroid
```

## Building/Compiling

In this example we will build PhoenixOS DarkMatter.

At first we clone the project repository:

```bash
git clone https://github.com/supremegamers/darkmatter
```

Now there are ~~three~~ two ways you can invoke the build command:

- You can cd into the repository dir and then run it:
```
cd darkmatter
bigdroid build --release
```
- Or you can directly pass the dir path in bigdroid without changing your PWD:
```
bigdroid build --release darkmatter
```

Then you should find the output iso in `target/release`.

## Advanced build command options

- If you do not want to compress `system.img` with squashfs:
```bash
bigdroid build --no-squashfs --release
```

- If you want to stop the build process after injecting the hooks:
```bash
bigdroid build --hooks-only --release
```

- If you do not want to build ISO and stop at `system.img` creation:
```bash
bigdroid build --image-only --release
```

> Protip: Try `bigdroid build --help`
