# Ansible RC Playbooks

Ansible roles and playbooks to install different distros and configure `.rc`.

## Prerequisite

- [Ansible][ansible]
- [`sshpass`][sshpass] required for `--ask-pass`

[sshpass]: https://man.freebsd.org/cgi/man.cgi?query=sshpass
[ansible]: https://docs.ansible.com/ansible/latest/index.html

## Boot distro live image

- [Arch Linux](./archlinux.md)
- [Debian Ubuntu](./ubuntu.md)

## Playbook: distro-install

- Follow the pre-install guides for desired distro in "Boot distro live image"
- Install ansible required dependencies
- Run the `distro-install` playbook

```bash
ansible-galaxy install -r requirements.yml

ansible-playbook distro-install.yml --ask-pass
```

## Playbook: distro-configure

- Copy the example distro file configuration and update the desired host_vars file
- Install ansible required dependencies
- Run the `distro-configure` playbook

```bash
cp host_vars/*.example host_vars/

ansible-galaxy install -r requirements.yml

ansible-playbook distro-configure.yml --ask-become-pass
```
