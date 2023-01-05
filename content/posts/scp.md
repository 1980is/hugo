---
title: "SCP Cheatsheet"
date: 2023-01-05T15:06:03Z
draft: false
categories: ["Linux"]
tags: ["SSH", "Cheatsheet"]
featured_image: scpfeatured.png
showcomments: false
description: All you need to know about SCP
images:
- images/featuredscp_hufdaa388111e5cf949af96851bf432d3f_46599_600x0_resize_box_3.png
---

## Copy local file to a remote host ###
``scp request.csv armann@192.168.122.164:/home/armann/Documents/`` \
reqquest.csv needs to be in your current directory.

## Copy a file from a remote host ###
``scp armann@192.168.122.164:/tmp/codepipeline-user.pdf .`` \
The dot at the end represents your current local directory.

## Copy local folder to a remote server
``scp -r /home/armann/Music/ armann@192.168.122.164:/tmp/``

## Copy a remote folder
``scp -r armann@192.168.122.164:/var/log/ /home/armann/``

## Copy a file from a remote server to a remote server
``scp armann@64.227.47.13:~/random.sh devarmann@1980.is:/tmp/``

## SCP Flags/Options

**–r** Recursively copy entire directories. Note that this follows symbolic links encountered in the tree traversal.

**-C** Compression enable. Passes the -C flag to ssh to enable compression.

**-l** Limits the used bandwidth, specified in Kbit/s.

**-o** Can be used to pass options to ssh in the format used in ssh_config.

**-P** Specifies the port to connect to on the remote host. Note that this option is written with a capital ‘P.’

**-p** Preserves modification times, access times, and modes from the original file.

**-q** Disables the progress meter as well as warning and diagnostic messages from ssh.

**-v** Verbose mode. Print debugging messages about progress. This is helpful in debugging connection, authentication, and configuration problems.

## Debug
Received disconnect from 18.130.233.91 port 22:2: **Too many authentication failures**

Most likely you have five or more ssh keys loaded. Check how many keys you have with ``ssh-add -l``

If you see five keys or more you are out of luck for now. Remove one of the keys you are not going to be needing soon.

``ssh-add -L ~/.ssh/id_ed25519yourprivatekey``

If that doesn't work you can remove keys with ``ssh-add -D``

Your ssh client will attempt to use all the keys from `ssh-agent` one by one before it gets to use the key you specified with `-i`. Each attempt counts as an _authentication failure_ and **by default only 5 attempts are allowed** by the SSH server you are getting the error you see. **Too many authentication failures**.

{{<img src="images/featurescp.png" alt="How to SCP data" class="center">}}
