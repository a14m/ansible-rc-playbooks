# Install ArchLinux

- create bootable image from iso.

```bash
sudo dd if=/path/to/image.iso of=/dev/diskX bs=1M
```

- boot the `archiso` live image from a bootable USB.
- connect to wireless network (if not connected via LAN).
- set root password (which will be asked to run the install playbook).

```bash
iwctl --passphrase <PASSPHRASE> station wlan0 connect <SSID>
passwd
```
