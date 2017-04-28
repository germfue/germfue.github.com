/etc/default/grub:
GRUB_CMDLINE_LINUX="... rhgb quiet acpi_backlight=vendor acpi_osi=linux"

$ sudo grub2-mkconfig -o /boot/grub2/grub.cfg

restart
