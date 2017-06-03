# Ansible Role: Supervisor

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-supervisor.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-supervisor)

An Ansible Role that installs [Supervisor](http://supervisord.org/) on Linux.

## Requirements

Python `pip` should be installed. If it is not already installed, you can use the `geerlingguy.pip` Ansible role to install Pip prior to running this role.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    supervisor_version: latest

Install a specific version of Supervisor by setting it here. See [available Supervisor versions](https://pypi.python.org/pypi/supervisor) on Pypi. `latest` installs the latest stable release.

    supervisor_started: true
    supervisor_enabled: true

Choose whether to use an init script or systemd unit configuration to start Supervisor when it's installed and/or after a system boot.

    supervisor_config_path: /etc/supervisor

The path where Supervisor configuration should be stored.

    supervisor_programs:
      - name: 'true'
        command: /bin/true
        state: present

A list of `program`s to be managed by Supervisor. If you set `state` to `present`, then a configuration file for the program (named `[program-name-here].conf`) will be added to the `conf.d` path included by the global Supervisor configuration.

    supervisor_nodaemon: false

Set to `true` if you need to run Supervisor in the foreground.

    supervisor_log_dir: /var/log/supervisor

The location where Supervisor logs will be stored.

    supervisor_user: root
    supervisor_password: 'my_secret_password'

The user under which `supervisord` will be run, and the password to be used when connecting to Supervisor's HTTP server (either for `supervisorctl` access, or when viewing the administrative UI).

    unix_http_server_enable: false
    unix_http_server_socket_path: /var/run/supervisor.sock

Whether to enable the UNIX socket-based HTTP server, and the socket file to use if enabled.

    inet_http_server_enable: false
    inet_http_server_port: '*:9001'

Whether to enable the TCP-based HTTP server, and the interface and port on which the server should listen if enabled.

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
