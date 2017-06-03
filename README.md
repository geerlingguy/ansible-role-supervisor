# Ansible Role: Supervisor

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-supervisor.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-supervisor)

An Ansible Role that installs [Supervisor](http://supervisord.org/) on Linux.

## Requirements

Python `pip` should be installed. If it is not already installed, you can use the `geerlingguy.pip` Ansible role to install Pip prior to running this role.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    supervisor_version: ''

Install a specific version of Supervisor by setting it here. See [available Supervisor versions](https://pypi.python.org/pypi/supervisor) on Pypi.

    supervisor_started: true
    supervisor_enabled: true

Choose whether to use an init script or systemd unit configuration to start Supervisor when it's installed and/or after a system boot.

    supervisor_config_path: /etc/supervisor

The path where Supervisor configuration should be stored.

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - geerlingguy.pip
        - geerlingguy.supervisor

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
