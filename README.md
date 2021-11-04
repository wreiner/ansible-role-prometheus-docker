# Ansible Role: prometheus-docker

Ansible role to create prometheus docker container.

## Mandatory Role Variables

This role requires you to set the address on which prometheus should listen.

```
prometheus_docker__listen_address: "{{ ansible_host }}"
```

The container will be exposed to the _prometheus_docker__listen_address_ on port 39090.

## Optional Role Variables

To add node-exporter targets the variable _prometheus_docker__node_exporter_targets_ can be set in the following format:

```
prometheus_docker__node_exporter_targets:
  - X.Y.Z.A:9100@cleartext-hostname
```

To include notification through alertmanager define the alertmanager instances which should receive alerts:

```
prometheus_docker__alertmanager_targets:
  - 192.168.122.87:9093
```

Specify the prometheus version you want to deploy:

```
prometheus_docker__prometheus_version: "v2.30.3"
```

Optionally it is possible to add rule files for prometheus through the inventory:

```
prometheus_docker__inventory_alert_rules:
- "{{ inventory_dir }}/prometheus_alert_rules/rule-backup.yml"
```

Those files are treated a Ansible template files. To escape ansible variables use:

```
{% raw %}{{ $prometheus.variable-to-escape }}{% endraw %}
```