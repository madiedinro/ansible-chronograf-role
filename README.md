# Asible role for base docker setup

Created for Ubuntu

## Usage

Add to ansible playbook following:

    - import_role:
        name: dr.chronograf
      vars:
        # listen port
        chronograf_port: 8888
        # listen ip addr or 0.0.0.0 for all
        chronograf_listen: 0.0.0.0
        # url for influxdb http
        chronograf_influxdb_url: http://127.0.0.1:8086
        # system service name
        chronograf_service_name: chronograf
        # Set service in state. Valid values: started (will be started if stopped), restarted (will be restarted any way)
        chronograf_service_state: 'started'
        # Value 'no': in systemd disable service in upstart remove config
        chronograf_service_enabled: 'yes'
      tags: ['chronograf']
      become: yes

if you need more flexibility use next params:

        chronograf_apt_repo_url: "deb https://repos.influxdata.com/{{ ansible_distribution | lower }} {{ ansible_distribution_release }} stable"

## Default parameters

Discover in `defaults/main.yml`

## Requirements

installed python `netaddr` lib

    pip install -U netaddr

or

    sudo apt-get install python-netaddr