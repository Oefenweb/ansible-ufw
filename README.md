## ufw

[![CI](https://github.com/Oefenweb/ansible-ufw/workflows/CI/badge.svg)](https://github.com/Oefenweb/ansible-ufw/actions?query=workflow%3ACI)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-ufw-blue.svg)](https://galaxy.ansible.com/Oefenweb/ufw)

Set up ufw in Debian-like systems.

#### Requirements

None

#### Variables

* `ufw_default_incoming_policy` [default: `deny`]: Default (incoming) policy
* `ufw_default_outgoing_policy` [default: `allow`]: Default (outgoing) policy

* `ufw_logging` [default: `off`]: Log level

* `ufw_rules` [default: see `defaults/main.yml`]: Rules to apply

* `ufw_etc_default_ipv6` [default: `true`]: Set to yes to apply rules to support IPv6
* `ufw_etc_default_default_input_policy` [default: `DROP`]: Set the default input policy to `ACCEPT`, `DROP`, or `REJECT`. Please note that if you change this you will most likely want to adjust your rules
* `ufw_etc_default_default_output_policy` [default: `ACCEPT`]: Set the default output policy to `ACCEPT`, `DROP`, or `REJECT`. Please note that if you change this you will most likely want to adjust your rules
* `ufw_etc_default_default_forward_policy` [default: `DROP`]: Set the default forward policy to `ACCEPT`, `DROP` or `REJECT`.  Please note that if you change this you will most likely want to adjust your rules
* `ufw_etc_default_default_application_policy` [default: `SKIP`]: Set the default application policy to `ACCEPT`, `DROP`, `REJECT` or `SKIP`. Please note that setting this to `ACCEPT` may be a security risk
* `ufw_etc_default_manage_builtins` [default: `false`]: By default, ufw only touches its own chains. Set this to 'yes' to have ufw manage the built-in chains too. Warning: setting this to 'yes' will break non-ufw managed firewall rules
* `ufw_etc_default_ipt_sysctl` [default: `/etc/ufw/sysctl.conf`]: IPT backend, only enable if using iptables backend
* `ufw_etc_default_ipt_modules` [default: `[nf_conntrack_ftp, nf_nat_ftp, nf_conntrack_netbios_ns]`]: Extra connection tracking modules to load. Complete list can be found in `net/netfilter/Kconfig` of your kernel source

## Dependencies

None

#### Example

```yaml
---
- hosts: all
  roles:
    - oefenweb.ufw
```

##### Allow ssh
```yaml
- hosts: all
  roles:
    - oefenweb.ufw
  vars:
    ufw_rules:
      - rule: allow
        to_port: 22
        protocol: tcp
        comment: 'allow incoming connection on standard ssh port'
```

##### Allow all traffic on eth1
```yaml
- hosts: all
  roles:
    - oefenweb.ufw
  vars:
    ufw_rules:
      - rule: allow
        interface: eth1
        to_port: ''
        comment: 'allow all traffic on interface eth1'
```

##### Allow snmp traffic from 1.2.3.4 on eth0
```yaml
- hosts: all
  roles:
    - oefenweb.ufw
  vars:
    ufw_rules:
      - rule: allow
        interface: eth0
        from_ip: 1.2.3.4
        to_port: 161
        protocol: udp
```

#### License

MIT

#### Author Information

Mischa ter Smitten (based on work of weareinteractive)

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-ufw/issues)!
