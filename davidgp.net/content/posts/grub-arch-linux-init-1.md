---
title: "Start Arch Linux in Single User Mode"
date: 2021-01-02T20:08:00+01:00
draft: true
---

The other day, after performing several updates to my system, I restarted it to load the new Linux kernel. After the restart, [LightDM][1] was not able to start. It was crashing, [SystemD][2] automatically restarting it and I was not able to even login into the system via a console terminal due to the restart loop of [LightDM][1].

The solution was to start my Linux in single user mode, disable [LightDM][1] and start it again in multiuser mode to fix the problem (an old [PRIME][3] script that [LightDM][1] was trying to load and it was not longer working). Here you have the steps that I performed to start an Arch Linux system using Grub as boot manager in single user mode:

1. **Reboot Linux** - Reboot Linux to reach the Grub screen.

2. **Edit the Kernel parameters** - Selecting the option `Arch Linux` or the default option you normally boot, press the key 'e' to enter in the edit mode of Grub. Look for the line that starts with `linux` and append at the end the following: `init=/bin/bash`.

3. **Start in single user mode** - Press `Control + x` or `F10` to boot Linux in single user mode.

In my case the `/root` disks was already mounted and I just deleted the link in [SystemD][2] that was starting [LightDM][1] and restarted the system normally in multiuser mode.

[1]: https://github.com/canonical/lightdm
[2]: https://www.freedesktop.org/wiki/Software/systemd/
[3]: https://wiki.archlinux.org/index.php/PRIME
