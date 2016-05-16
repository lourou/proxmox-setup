# Proxmox VE Setup from a mac running MacOS X

Cloning a Debian 7 Linux physical machine and running it on Proxmox VE 4.2.

## Create a USB bootable disk containing Clonezilla from MacOS X

 - Download a Clonezilla Live .iso from here: <http://clonezilla.org/downloads/download.php?branch=stable> 
 - Insert USB key and run `diskutil list` from the terminal to ifentify the device name
 - Identify the USB disk device name, for example `/dev/disk4`
 - Unmount / eject the USB disk using umount or Disk Utility
 - Copy the .iso disk image to the USB key. Warning, make sure you point to the right disk and make sure not to erase your own hard drive with this command.

```
sudo dd if=/tmp/clonezilla-live.iso of=/dev/diskXXXX
```

Press ctrl+t to check progress.

## Create USB bootable disk containing Proxmox from MacOS X

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
