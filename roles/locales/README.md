# Ansible Role: locales

This role configure the machine locales

## Role Variables

- `locales_list` the locales to be generated.
- `locales_conf` the dictionary of different locales environment variable
  - `lang`: `LANG=` default `en_US.UTF-8`
  - `language`: `LANGUAGE=` default `en_US.UTF-8`
  - `lc_time`: `LC_TIME=` default `en_KD.UTF-8`
  - `time_style`: `TIME_STYLE=` default `iso` (23:59:59)
  - `lc_collate`: `LC_COLLATE=` default `c.UTF-8`
- `locales_timezone` the timezone default `UTC`

## Docs

- https://manpages.debian.org/buster/manpages/locale.1.en.html
- https://manpages.debian.org/buster/locales/locale-gen.8.en.html
- https://manpages.debian.org/buster/manpages/localedef.1.en.html
