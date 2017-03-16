---
layout: post
title:  "Globaleaks: development on Fedora"
published: true
tags: 
 - globaleaks
 - fedora
priority: 0.8
---

sudo dnf groupinstall "C Development Tools and Libraries"
sudo dnf install gcc-c++ openssl-devel libffi-devel python2-devel
curl --silent --location https://rpm.nodesource.com/setup_6.x | sudo bash -
sudo dnf install nodejs
=> accept new pgp key
[user@darkplanet Downloads]$ sudo dnf install nodejs
Node.js Packages for Fedora Linux 25 - x86_64                                                                                                                                       18 kB/s | 103 kB     00:05    
Dependencies resolved.
===================================================================================================================================================================================================================
 Package                                      Arch                                         Version                                                          Repository                                        Size
===================================================================================================================================================================================================================
Installing:
 nodejs                                       x86_64                                       2:6.10.0-1nodesource.fc25                                        nodesource                                       9.8 M

Transaction Summary
===================================================================================================================================================================================================================
Install  1 Package

Total download size: 9.8 M
Installed size: 34 M
Is this ok [y/N]: y
Downloading Packages:
nodejs-6.10.0-1nodesource.fc25.x86_64.rpm                                                                                                                                          1.7 MB/s | 9.8 MB     00:05    
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                              1.7 MB/s | 9.8 MB     00:05     
warning: /var/cache/dnf/nodesource-97b44be9747b6db5/packages/nodejs-6.10.0-1nodesource.fc25.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 34fa74dd: NOKEY
Importing GPG key 0x34FA74DD:
 Userid     : "NodeSource <gpg-rpm@nodesource.com>"
 Fingerprint: 2E55 207A 95D9 944B 0CC9 3261 5DDB E8D4 34FA 74DD
 From       : /etc/pki/rpm-gpg/NODESOURCE-GPG-SIGNING-KEY-EL
Is this ok [y/N]: y
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Installing  : nodejs-2:6.10.0-1nodesource.fc25.x86_64                                                                                                                                                        1/1 
  Verifying   : nodejs-2:6.10.0-1nodesource.fc25.x86_64                                                                                                                                                        1/1 

Installed:
  nodejs.x86_64 2:6.10.0-1nodesource.fc25                                                                                                                                                                          

Complete!






cd GlobaLeaks/client
npm install grunt-cli --save-dev
