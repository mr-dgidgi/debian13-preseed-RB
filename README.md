# Fully automatic installation of Debian 13 through ISO remastering

This is a fork from ["istepaniuk's debian13-preseed"](https://github.com/istepaniuk/debian13-preseed) modified for the RecoveryBox

This tool need the followings packages (for debian):
* libarchive-tools
* xorriso


Usage:

1. Download a [debian "netinst"](https://www.debian.org/CD/netinst/) image.
   (Tested with 13.4)
2. Adapt the preseed.cfg file to your needs. (This one installs just SSH and
   sudo)
3. Run:

```
./make-preseed-iso.sh debian-13.4.0-amd64-netinst.iso
```

This will create a new ISO image named `preseed-debian-13.4.0-amd64-netinst.iso`
which installs Debian on the first available disk without intervention, not even
a boot menu prompt.

### WARNING: This deletes stuff!!!

The preseed.cfg that in this repository ***completely erases the first 
disk\*\****

> ** as returned by `list-devices disk`, so excluding usb

The location of the initrd is hardcoded to 'install.amd', this needs to be
changed if you are using an iso for other than amd64.

In the case of a UEFI system, the configuration for the boot menu options is
specific to this Debian version. This is because grub uses the position of the
entry to specify the default option.

### More on how to preseed

* https://wiki.debian.org/DebianInstaller/Preseed
* https://wiki.debian.org/DebianInstaller/Preseed/EditIso
* https://wiki.debian.org/RepackBootableISO
