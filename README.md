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
locales_language_packages:
  ## REDHAT
  - name: glibc-langpack-en
    state: present
  - name: glibc-langpack-fr
    state: present
  - name: glibc-langpack-de
    state: absent
  ## UBUNTU
  # - name: language-pack-en
  #   state: present
  # - name: language-pack-fr
  #   state: present
  # - name: language-pack-de
  #   state: absent

locales_locales_present:
  - en_US.UTF-8
  - fr_FR.UTF-8

locales_locales_absent:
  - de_DE.UTF-8

locales_default_locales_list:
  LANG: en_US.UTF-8
  LC_ALL: en_US.UTF-8

locales_keymap: fr
locales_keymap_toggle:
```


Specifics variables are in `vars/{{ ansible_os_family }}`  ; example for Debian OS family : 

```yaml
locales_required_packages:
  - tzdata
  - locales
  - console-data

locales_conf_file: /etc/default/locale
```

Dependencies
------------

none


Example Playbook
----------------



License
-------

BSD ; This role is forked from : https://github.com/aisbergg/ansible-role-localization


Author Information
------------------

https://github.com/dginhoux/
