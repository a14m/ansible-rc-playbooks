# Install ArchLinux

- Download [archlinux](https://archlinux.org/releng/releases/)
- Format the usb
- Unmount disk (on MacOS ex. `diskutil unmountDisk /dev/diskX`)
- create bootable image from iso `sudo dd if=/path/to/image.iso of=/dev/diskX bs=4M status=progress`
- boot the `archiso` live image from a bootable USB.
- connect to wireless network (if not connected via LAN).
- set root password (which will be asked to run the install playbook).
- set the hostname to `archlinuxiso.local`
- run the `distro-install` playbook on the ansible controller

**Example:**

```bash
passwd
iwctl --passphrase <PASSPHRASE> station wlan0 connect <SSID>
hostnamectl set-hostname archlinuxiso.local
systemctl restart systemd-resolved
```
