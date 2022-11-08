OPNsense: Gateway
=================

An Ansible role to configure gateways on an opnSense firewall. 

Requirements
------------

This role requires the `lxml` python package to be installed on the host system.

Role Variables
--------------

|             Variable             |  Type  |                             Description                             |
| :------------------------------: | :----: | :-----------------------------------------------------------------: |
|    opnsense_gateway_interface    | string |             The interface this gateway is connected to              |
|      opnsense_gateway_name       | string |                    Unique name for this gateway                     |
|   opnsense_gateway_description   | string |                 Optional description for this item                  |
|     opnsense_gateway_default     |  bool  |              Whether or not this is a default gateway               |
|   opnsense_gateway_ip_protocol   | string |                        IP family (v4 or v6)                         |
|     opnsense_gateway_ip_addr     | string |  Address of our gateway, empty/dynamic when dynamically generated.  |
| opnsense_gateway_monitor_disable |  bool  |                Disable monitoring (consider online)                 |
|    opnsense_gateway_interval     |  int   | For multi WAN. How often that an ICMP probe will be sent in seconds |
|     opnsense_gateway_weight      |  int   |  For multi WAN, to assign more/less traffic to a specific gateway   |

- Resources:
  - https://docs.opnsense.org/manual/gateways.html
  - https://docs.opnsense.org/manual/how-tos/multiwan.html

Dependencies
------------

N/A.

Example Playbook
----------------

```yaml
- name: Configure the default gateway on all firewalls
  hosts: opnsense

  roles:
    - role: mirceanton.opnsense_gateway
      vars:
        opnsense_gateway_interface: wan
        opnsense_gateway_name: WAN_GW
        opnsense_gateway_description: Interface WAN Gateway
        opnsense_gateway_default: true
        opnsense_gateway_ip_protocol: inet
        opnsense_gateway_ip_addr: "192.168.10.1"
        opnsense_gateway_monitor_disable: true
        opnsense_gateway_interval: 1
        opnsense_gateway_weight: 1
```

License
-------

MIT

Author Information
------------------

A role developed by [Mircea-Pavel ANTON](https://www.mirceanton.com).
