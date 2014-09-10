## ufw [![Build Status](https://travis-ci.org/Oefenweb/ansible-ufw.svg?branch=master)](https://travis-ci.org/Oefenweb/ansible-ufw)

Set up ufw in Debian-like systems.

#### Requirements

None

#### Variables

* `uwf_default_policy` [default: `deny`]: Default policy
* `uwf_logging` [default: `off`]: Log level
* `uwf_rules` [default: see `defaults/main.yml`]: Rules to apply

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
uwf_rules:
  - rule: allow
    to_port: 22
    protocol: tcp
```

##### Allow all traffic on eth1
```yaml
uwf_rules:
  - rule: allow
    interface: eth1
    to_port: ''
```

##### Allow snmp traffic from 1.2.3.4 on eth0
```yaml
uwf_rules:
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
