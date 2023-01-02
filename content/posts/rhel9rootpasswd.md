---
title: "Reset Root Password RHEL9"
date: 2023-01-02T19:11:57Z
draft: false
categories: ["Linux", "RHCA"]
showcomments: false
featured_image: redhatlogo.png
---

Tip of the day for all you Red Hat 9 administrators out there. Need to reset the root password? Either for the RHCSA exam or in the field?

Things have changed a bit in RHEL 9. **"rd.break"** does not work anymore. These are the steps that need to be taken.


1. Find the line that loads the Linux kernel and add "init=/bin/bash" to the end of the line.
2. ``mount -o remount,rw /`` This is necessary because it's mounted as read-only.
3. ``passwd root``
4. ``touch /.autorelabel``
5. ``exec /usr/lib/systemd/systemd/``

This command will reboot the machine and now you have a new root password! 😎 

