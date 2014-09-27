Role Name
=========

Configure the underlying network for Eucalyptus clodu

Requirements
------------

The use must know his network capacities :

- VLANs allowance
 
- Backend-network subnet addressing allowance

Role Variables
--------------

The vars folder contains different example, one for each of supported topologies by Eucalyptus for its deployment. To use it, the user can simply create a symlink from the file he wants to use and name the target "main.yml"
Otherwise, the user will have to specify the variables file in his playbook (see below).

| Name | Defaults | Values | Description | Notes
|--- |--- |--- |--- |---
| networking_mode| None| EDGE/MANAGED/MANAGED-NOVLAN| Defines the networking mode used by Eucalyptus | None
| use_vlans | true | true/false|  defines wether or not to use vlans in the backend network|  If set to true, VLAN interfaces will be created by the playbook. Not applicable to MANAGED
| edge_using_private | true | true/false | Defines if EDGE mode should use instances' private address|Applies to EDGE Only
| instance_dns_domain| eucalyptus.internal | yourdomain.any | Sets the domain search for instances  | None
| instance_dns_servers | 8.8.8.8 | list of IP addresses | Sets the nameserver(s) for the instances | Must be a list
| pub_ips | None | list of IP addresses of ranges | Sets the Public IP addresses that will be used by your instances for public traffic | None
| clusters | Object (Dict) | See below | Defines your clusters specific network settings | None
| vlan_routes | "[]" (empty list) | List of the subnets to add on the NC to communicate over multi-subnets via a specific gateway | Advanced users only

Dependencies
------------

None

Example Playbook
----------------

```
- hosts: all
  roles:
  - eucalyptus-network
  vars:
  - networking_mode: EDGE
  - use_vlans: true

```

License
-------

None

Author Information
------------------

John Mille
