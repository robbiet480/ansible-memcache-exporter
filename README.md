
robbiet480.memcache_exporter for Ansible Galaxy
============

[![Circle CI](https://circleci.com/gh/robbiet480/ansible-memcache-exporter.svg?style=shield)](https://circleci.com/gh/robbiet480/ansible-memcache-exporter)



## Summary

Role name in Ansible Galaxy: **[robbiet480.memcache_exporter](https://galaxy.ansible.com/list#/roles/4465)**

This Ansible role has the following features for [memcache_exporter](https://github.com/dcu/memcache_exporter) (a memcache metrics exporter for [Prometheus](http://prometheus.io/)):

 - Install a pre-compiled version of memcache_exporter (I hope the maintainer of memcache_exporter will provide official binary releases).
 - Handlers for restart/reload/stop events.




## Role Variables

### Mandatory variables

None.



### Optional variables


**memcache_exporter specific** user-configurable defaults:

```yaml
# memcache Connection String URI
# @see http://docs.memcache.org/manual/reference/connection-string/
memcache_exporter_memcache_uri:  "memcache://localhost:27017"
```


**Prometheus** user-configurable defaults (of course, a subset of optional variables in [robbiet480.prometheus](https://github.com/robbiet480/ansible-prometheus)):

```yaml
# user and group
prometheus_user:   prometheus
prometheus_group:  prometheus


# directory for executable files
prometheus_install_path:   /opt/prometheus

# directory for logs
prometheus_log_path:       /var/log/prometheus

# directory for PID files
prometheus_pid_path:       /var/run/prometheus


# version of helper utility "gosu"
gosu_version:  1.4
```


## Handlers

- `restart memcache_exporter`

- `reload memcache_exporter`

- `stop memcache_exporter`



## Usage


### Step 1: add role

Add role name `robbiet480.memcache_exporter` to your playbook file.


### Step 2: add variables

Set vars in your playbook file, if necessary.

Simple example:

```yaml
---
# file: simple-playbook.yml

- hosts: all
  sudo: True
  roles:
    - robbiet480.memcache_exporter

  vars:

    memcache_exporter_memcache_uri:  "memcache://adm:password@localhost:27017"


```




## Dependencies

None.


## License

MIT License. See the [LICENSE file](LICENSE) for details.
