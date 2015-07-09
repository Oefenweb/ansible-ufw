## ufw

[![Build Status](https://travis-ci.org/Oefenweb/ansible-ufw.svg?branch=master)](https://travis-ci.org/Oefenweb/ansible-ufw) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-ufw-blue.svg)](https://galaxy.ansible.com/list#/roles/1613)

Set up ufw in Debian-like systems.

#### Requirements

None

#### Variables

* `ufw_default_policy` [default: `deny`]: Default policy
* `ufw_logging` [default: `off`]: Log level
* `ufw_rules` [default: see `defaults/main.yml`]: Rules to apply

## Dependencies

None

#### Example

```yaml
---
- hosts: all
  roles:
  - ufw
```

##### Allow ssh
```yaml
ufw_rules:
  - rule: allow
    to_port: 22
    protocol: tcp
```

##### Allow all traffic on eth1
```yaml
ufw_rules:
  - rule: allow
    interface: eth1
    to_port: ''
```

##### Allow snmp traffic from 1.2.3.4 on eth0
```yaml
ufw_rules:
  - rule: allow
    interface: eth0
    from_ip: 1.2.3.4
    to_port: 161
    protocol: udp
```

#### TODO

Make use of `omit`, available in **ansible 1.8**

#### License

MIT

#### Author Information

Mischa ter Smitten (based on work of weareinteractive)

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-ufw/issues)!
