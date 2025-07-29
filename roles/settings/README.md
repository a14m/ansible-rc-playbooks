# Ansible Role: settings

This role configure the machine settings (locales/timezone/password policy/etc.)

## Role Variables

- `settings_timezone` the timezone default `UTC`
- `settings_locales_list` the locales to be generated.
- `settings_locales_conf` the dictionary of different locales environment variable
  - `lang`: `LANG=` default `en_US.UTF-8`
  - `language`: `LANGUAGE=` default `en_US.UTF-8`
  - `lc_time`: `LC_TIME=` default `en_KD.UTF-8`
  - `time_style`: `TIME_STYLE=` default `iso` (23:59:59)
  - `lc_collate`: `LC_COLLATE=` default `c.UTF-8`
- `settings_pw_policy` the dictionary of password policy configurations
  - `enabled` boolean to enable or disable the enforcement of password policy
  - `difok` the number of differences between new and old password (default 0 - disabled)
  - `minlen` min password length (default 8)
  - `dcredit` required digits in password (default 0)
  - `ucredit` required uppercase chars in password (default 0)
  - `ocredit` required other chars in password (default 0)
  - `lcredit` required lowercase chars in password (default 0)
  - `minclass` required minimum classes in password upper/lower/digit/other (default 0 - disabled)
  - `maxrepeat` allowed maximum repeats in password (default 0 - disabled)
  - `maxclassrepeat` maximum allowed consecutive class repeats (default 0 -disabled)
  - `gecoscheck` (default 0 - disabled)

## Docs

- https://manpages.debian.org/buster/manpages/locale.1.en.html
- https://manpages.debian.org/buster/locales/locale-gen.8.en.html
- https://manpages.debian.org/buster/manpages/localedef.1.en.html
- https://linux.die.net/man/8/pam_pwquality
