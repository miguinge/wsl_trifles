---
Windows version: W10 22H2
wsl version: 2.4.11.0
Linux distribution version: Ubuntu 24.04.2 LTS
Linux kernel version: 5.15.167.4-microsoft-standard-WSL2
---

# Mounting Google Drive for Desktop File System

Some user as in this [stackoverflow entry](https://stackoverflow.com/questions/69207755/google-drive-virtual-drive-mount-in-wsl2), gave this workaround.

```bash
sudo mount -t drvfs G: /mnt/g
```

<a name="Create_mount_point"></a>
The directory `/mnt/g` must exist firt.

`sudo mkdir /mnt/g`

## Context
When _Google Drive for Desktop_ are installed in your Windows machine you can notice it is  unreachable from your **WSL** linux distribution.

### [What is DrvFs?](https://devblogs.microsoft.com/commandline/chmod-chown-wsl-improvements/#what-is-drvfs)

***DrvFs*** is a filesystem plugin to **WSL** that was designed to support interop between **WSL** and the **Windows filesystem**. ***DrvFs*** enables WSL to mount drives with supported file systems under `/mnt`, such as `/mnt/c`, `/mnt/d`, etc.

## The command

Let's break down the command `sudo mount -t drvfs G: /mnt/g` for better understanding.

- `sudo mount`: Run the `mount` command with the security privileges of another user, by default the **root** user. (Originally `sudo` stood for _SuperUser Do_).
- `-t`: This is the `mount` option for _File System_ **type**.
- `drvfs`: `drvfs` is the file system pluging. [Read this.](https://github.com/miguinge/wsl_trifles/new/main#what-is-drvfs)
  - You can remember it as ***drv*** -->Drive; ***fs*** --> File System.
- `G:`: This is the _Google Drive for Desktop_ drive letter. By default the assigned drive letter is `G:`.
- `/mnt/g`: The [previously created](#Create_mount_point) mount point.
