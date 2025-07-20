# Ansible Role: configure

This role is a wrapper around the `roles` section in a playbook,
to allow running different set of roles for each host

Ex. For archlinux, one might need to configure a desktop environment, while
not needing the same for a raspberryPi install

## Role Variables

- `hostname` the inventory hostname machine to be configured (default: "{{ inventory_hostname }}")
- `configure_roles` the list of roles to run, these will load their variables from ansible (host_vars or group_vars).
