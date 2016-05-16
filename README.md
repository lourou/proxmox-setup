# Proxmox Setup

Proxmox 4.2 setup for running Debian virtual machines

## Create USB disk image from MaxOS X

Instructions for OS X : OS X can use dd as the unix systems, but first requires the ISO image to be converted
before it can be copied over to the USB stick. First you will need to download the ISO image, then plug in the USB Stick.
To get the device name by running 'diskutil list'.

This command will output all the disk attached to the system, you should be able to match up the USB stick
to the specs and name of one listed. To get the raw device, you can add an 'r' in front of the name,
ex. /dev/disk4 would become /dev/rdisk4. Next you will an to open Disk Utility and eject each partition only
(If you eject from Finder or the Desktop it will eject the entire disk, removing it completely from the system).

Now we can convert the ISO and copy the new image over with. Note hdiutil will commonly add the .dmg
extension to the output file, so you will end up pve-cd.img.dmg

```
hdiutil convert -format UDRW -o pve-cd.img pve-cd.iso
sudo dd if=pve-cd.img.dmg of=/dev/rXYZ
```

Source: <https://pve.proxmox.com/wiki/Install_from_USB_Stick>

## Migrate a Physical running Debian to Proxmox VE



## Migrate a Physical (running) Windows server to Proxmox VE

Source: <https://pve.proxmox.com/wiki/Migration_of_servers_to_Proxmox_VE#Physical_.28running.29_server_to_Proxmox_VE_.28KVM.29_using_Windows_backup>
