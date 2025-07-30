# Install Ubuntu

- Download [ubuntu](https://ubuntu.com/download/alternative-downloads)
- Format the usb
- Unmount disk (on MacOS ex. `diskutil unmountDisk /dev/diskX`)
- Create bootable image from iso `sudo dd if=/path/to/image.iso of=/dev/diskX bs=4M status=progress`
- Boot the `ubuntu` live image from a bootable USB
- Connect to wireless network (if not connected via LAN)
- Set root password (which will be asked to run the install playbook)
- Set the hostname to `ubuntuiso.local`
- Install and configure ssh
- Install `debootstrap`

**Example:**

```bash
sudo su
passwd
nmcli dev wifi connect <SSID> password <PASSPHRASE>

hostnamectl set-hostname ubuntuiso.local
systemctl restart avahi-daemon

apt update
DEBIAN_FRONTEND=noninteractive apt-get install -o Dpkg::Options::="--force-confold" -y openssh-server

cat > /etc/ssh/sshd_config<< EOF
PasswordAuthentication yes
Port 22
PermitRootLogin yes
EOF

systemctl restart ssh
```

On the ansible controller:

- `cp host_vars/ubuntuiso.local.example host_vars/ubuntuiso.local`
- Update the `host_vars/ubuntuiso.local` file
- Run the `distro-install` playbook on the ansible controller
