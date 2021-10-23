# Ansible Role: prometheus-docker

Ansible role to create prometheus docker container.

## Mandatory Role Variables

This role requires you to set the address on which prometheus should listen.

```
prometheus_docker__listen_address: "{{ ansible_host }}"
```

The container will be exposed to the _prometheus_docker__listen_address_ on port 39090.

## Optional Role Variables

To include notification through alertmanager define the alertmanager instances which should receive alerts:

```
prometheus_docker__alertmanager_targets:
  - 192.168.122.87:9093
```

Specify the prometheus version you want to deploy:

```
prometheus_docker__prometheus_version: "v2.30.3"
```
