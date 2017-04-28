---
layout: post
title:  "Aspire S3 Series: Configure backlight in Fedora 25"
published: true
tags: 
 - fedora
priority: 0.8
---
I installed recently Fedora 25 and found out that the backlight wasn't working properly when adjusting it with the keyboard. This small recipe solved the issue.

# Configure Grub
Go to `/etc/default/grub` and append `acpi_backlight=vendor acpi_osi=linux` to the variable `GRUB_CMDLINE_LINUX`. See example:

    GRUB_CMDLINE_LINUX="... rhgb quiet acpi_backlight=vendor acpi_osi=linux"

# Update Grub
Run the following command:

    $ sudo grub2-mkconfig -o /boot/grub2/grub.cfg

Restart and enjoy :)
