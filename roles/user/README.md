# Ansible Role: User

This role creates the user and configures the `sudo` functionality for the user

## Role Variables

- `username` **Required** name of the user to be created.
- `user_password` created user default password (default: `changeme`).
- `user_public_keys` the list of ssh public keys to be added to user authorized_keys

## Internals

- ensure `sudo` installed.
- configure `sudoers` file to grant `%sudo ALL=(ALL:ALL) ALL` for `sudo_group_name`.
- create user and add to the `username` and `sudo` groups.
- require user password change on first use of `sudo` command.
- configure the user authorized keys to allow public key authentication (if configured).

### Caveats

If no public key authentication is configured by this role,
the user won't be able to login (since the hardened ssh role disable root and password authentication).

For this reason, if you want to enable the insecure password authentication,
please update the ssh role `"Configure authentication policy"` manually to
allow for password/root authentication, These features are disabled by default.
