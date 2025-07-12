# Ansible Role: install

This role installs and configure the basic networking functionality of a linux distro

## Role Variables

- `hostname` the distro linux network hostname to be used.
- `rc_playbooks_dir` the root directory of the rc playbooks defaults the ansible playbook_dir variable
- `partition_boot` the boot partition definition for role `partition`, to install bootloader
- `partition_root` the root partition definition for role `partition`, to install distro root

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
