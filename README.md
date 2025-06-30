# Ansible RC Playbooks

Ansible roles and playbooks to install different distros and configure `.rc`.

## Prerequisite

- [Ansible][ansible]
- [`sshpass`][sshpass] required for `--ask-pass`

[sshpass]: https://man.freebsd.org/cgi/man.cgi?query=sshpass
[ansible]: https://docs.ansible.com/ansible/latest/index.html

## Playbook: distro-configure

```bash
cp distro-configure.yml.example distro-configure.yml

ansible-galaxy install -r requirements.yml

ansible-playbook site.yml \
  --limit wlan \
  --extra-vars '{"network_wifi_ssid":"<WIFI_SSID>", "network_wifi_pass":"<WIFI_PASS>"}'
```
