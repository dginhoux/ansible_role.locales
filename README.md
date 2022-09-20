Ansible Role : dginhoux.locales
=========

This ansible role configure locales


Requirements
------------

This role require a supported platform defined in `meta/main.yml`.
It will skip node with unsupported platform ; this behaviour can be bypassed by settings this variable `asserts_bypass=True`.


Role Variables
--------------

Necessary variables are defined on `defaults/main.yml`.

```yaml
locales_locales_list:
  - name: en_US.UTF-8
    state: present
  - name: fr_FR.UTF-8
    state: present
  - name: de_DE.UTF-8
    state: absent

locales_default_locales_list:
  LANG: en_US.UTF-8
  LC_ALL: en_US.UTF-8

locales_keymap: fr
locales_keymap_toggle:

locales_variables_list:
  - LANG
  - LANGUAGE
  - LC_ADDRESS
  - LC_COLLATE
  - LC_CTYPE
  - LC_IDENTIFICATION
  - LC_MONETARY
  - LC_MESSAGES
  - LC_MEASUREMENT
  - LC_NAME
  - LC_NUMERIC
  - LC_PAPER
  - LC_TELEPHONE
  - LC_TIME
  - LC_ALL
```


Specifics variables are in `vars/` yml files ; example for RedHat 8 : 

```yaml
locales_required_packages:
  - tzdata
  - locales
  - console-data

locales_conf_file: /etc/default/locale

locales_language_packages:
  - name: glibc-langpack-en
    state: present
  - name: glibc-langpack-fr
    state: present
  - name: glibc-langpack-de
    state: absent
```

Dependencies
------------

none


Example Playbook
----------------



License
-------

BSD ; This role is inspired from https://github.com/aisbergg/ansible-role-localization


Author Information
------------------

https://github.com/dginhoux/
