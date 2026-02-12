# [Ansible role sudo](#ansible-role-sudo)

Install sudo on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-sudo/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-sudo/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-sudo/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-sudo)|[![downloads](https://img.shields.io/ansible/role/d/buluma/sudo)](https://galaxy.ansible.com/buluma/sudo)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-sudo.svg)](https://github.com/buluma/ansible-role-sudo/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-sudo/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  # This role installs packages using the `raw` module and needs to connect as
  # `root`. (`sudo` is not available before sudo-ing.) All tasks in the
  # role have `become` set to `false`, so you can use either `false` or `true` for
  # `become`, the role will not use become (so `sudo`) for any task.
  become: false  # `false` will also work.
  # This role installs sudo, gathering facts can't be done before `sudo` is
  # installed. This role runs the `setup` module, so facts will be available
  # after running the role.
  gather_facts: false

  roles:
    - role: buluma.sudo
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-sudo/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: prepare
  hosts: all
  become: true
  gather_facts: false

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-sudo/blob/master/defaults/main.yml):

```yaml
---
# defaults file for sudo

# Do you want to wait for the host to be available?
sudo_wait_for_host: false

# The number of seconds you want to wait during connection test before failing.
sudo_timeout: 3
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-sudo/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-sudo/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Amazon](https://hub.docker.com/r/buluma/amazonlinux)|all|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|all|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[opensuse](https://hub.docker.com/r/buluma/opensuse)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|
|[Kali](https://hub.docker.com/r/buluma/kalilinux)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-sudo/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-sudo/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

