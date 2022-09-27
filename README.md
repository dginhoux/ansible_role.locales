# ROLE dginhoux.locales



## DESCRIPTION

This ansible role configure locales.<br />
It 



## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform.<br />
It will skip node with unsupported platform to avoid any compatibility problem.<br />
This behaviour can be bypassed by settings the following variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36 |
| EL | 7, 8 |

#### ANSIBLE VERSION

Ansible >= 2.12

#### DEPENDENCIES

None.



## INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.locales
```
#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.locales dginhoux.locales
```


## USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.locales
      ansible.builtin.include_role:
        name: dginhoux.locales
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml` : 

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

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

* Debian Family

```yaml
locales_required_packages:
  - tzdata
  - locales
  - console-data

locales_conf_file: /etc/default/locale
```

* Fedora Family

```yaml
locales_required_packages:
  - tzdata

locales_conf_file: /etc/locale.conf

locales_language_packages:
  - name: glibc-langpack-en
    state: present
  - name: glibc-langpack-fr
    state: present
  - name: glibc-langpack-de
    state: absent
```

* RedHat 8 Family

```yaml
locales_required_packages:
  - tzdata

locales_conf_file: /etc/locale.conf

locales_language_packages:
  - name: glibc-langpack-en
    state: present
  - name: glibc-langpack-fr
    state: present
  - name: glibc-langpack-de
    state: absent
```

* RedHat Family

```yaml
locales_required_packages:
  - tzdata

locales_conf_file: /etc/locale.conf
```


## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
