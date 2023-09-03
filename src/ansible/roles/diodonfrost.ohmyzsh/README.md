# ansible-role-ohmyzsh

[![molecule](https://github.com/diodonfrost/ansible-role-ohmyzsh/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-ohmyzsh/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.ohmyzsh-660198.svg)](https://galaxy.ansible.com/diodonfrost/ohmyzsh)

This role provide a compliance for install ohmyzsh on your target host.

## Requirements

This role was developed using Ansible 2.8 Backwards compatibility is not guaranteed.
Use `ansible-galaxy install diodonfrost.ohmyzsh` to install the role on your system.

Supported platforms:

```yaml
- name: EL
  versions:
    - 8
    - 7
    - 6
- name: Fedora
  versions:
    - any
- name: Debian
  versions:
    - buster
    - stretch
    - jessie
    - wheezy
    - squeeze
- name: Ubuntu
  versions:
    - bionic
    - xenial
    - trusty
    - precise
- name: Amazon
  versions:
    - any
- name: opensuse
  versions:
    - any
- name: ArchLinux
  versions:
    - any
- name: Alpine
  versions:
    - any
- name: Gentoo
  versions:
    - any
- name: ClearLinux
  versions:
    - any
- name: FreeBSD
  versions:
    - any
- name: OpenBSD
  versions:
    - any
- name: MacOSX
  versions:
    - any
```

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# defaults file for ansible-role-ohmyzsh

# Install ohmyzsh for the defined users.
# Default: current ansible connection user
ohmyzsh_users: "{{ ansible_user_id }}"

# Setup the ohmyzsh theme to used
ohmyzsh_theme: robbyrussell

# Setup the ohmyzsh plugins to used
ohmyzsh_plugins:
  - git
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy ohmyzsh role in a localhost and installing the latest version of ohmyzsh.

```yaml
---
- hosts: localhost
  roles:
    - role: diodonfrost.ohmyzsh
```

This role can also configure ohmyzsh theme and plugins.

```yaml
---
- hosts: localhost
  roles:
    - role: diodonfrost.ohmyzsh
      vars:
        ohmyzsh_theme: intheloop
        ohmyzsh_plugins: "git,docker,systemd"
```

## Local Testing

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](hhttps://libvirt.org/) (bsd test only)
* [Vagrant](https://www.vagrantup.com/downloads.html) (bsd test only)

### Testing with Docker

```shell
# Test ansible role with centos-8
image=centos:8 molecule test

# Test ansible role with ubuntu-20.04
image=ubuntu:20.04 molecule test

# Test ansible role with alpine-latest
image=alpine:latest molecule test

# Create centos-7 instance
image=centos:7 molecule create

# Apply role on centos-7 instance
image=centos:7 molecule converge

# Launch tests on centos-7 instance
image=centos:7 molecule verify
```

### Testing with Vagrant and Libvirt

```shell
# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with OpenBSD
molecule test -s openbsd
```

## License

Apache 2

## Author Information

This role was created in 2020 by diodonfrost.
