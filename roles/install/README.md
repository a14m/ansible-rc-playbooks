# Ansible Role: install

This role installs and configure the basic networking functionality of a linux distro

## Role Variables

- `hostname` the distro linux network hostname to be used.
- `rc_playbooks_dir` the root directory of the rc playbooks defaults the ansible playbook_dir variable
- `partition_boot` the boot partition definition for role `partition`, to install bootloader
- `partition_root` the root partition definition for role `partition`, to install distro root

### Debian variables

- `install_debian_distro` the distro code name to install, default: `noble` (Ubuntu 24.04 LTS)
- `install_distro_variant` the distro variant to install, default: `ubuntu-desktop`
- `install_kernel_version` the kernel version to install, default: `6.14.0-24`
- `install_apt_ignored_preferences` the default content of ignored packages in `etc/apt/preferences.d/ignored-package`
- `install_apt_sources` the default content of the source list in `etc/apt/sources.list`

## Internals

`rc_playbooks_dir` variable is required for testing, since molecule will override the default special
ansible `playbook_dir` variable with the molecule playbook directory, this variable is needed to allow
the testing to pass, without conflicting with the original behaviour of the playbook directory

### Archlinux

- run the `pacstrap -K` script to install arch linux
- generate the `/etc/fstab` configs
- initialize `systemd-boot`
- configure `systemd-boot`
- install the required dependencies to run ansible
- copy the ansible playbook to the installed arch directory
- run the configure playbook to bootstrap the arch installation

### Debian

- include debian distro variable (distro name, variant, kernel pkg, etc)
- install required dependencies in live environment (ex. `debootstrap` and `arch-install-scripts`)
- run `debootstrap` to install desired debian distro
- generate the `/etc/fstab` configs
- configure `apt` in chroot
- configure kernel install/postinstall
- install HWE kernel package
- initialize `systemd-boot`
- configure `systemd-boot`
- install debian distro variant (ex. `ubuntu-desktop`, `ubuntu-server`, etc)
- install the required dependencies to run ansible
- copy the ansible playbook to the installed arch directory
- run the configure playbook to bootstrap the arch installation
