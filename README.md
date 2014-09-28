Role Name
=========

Configure the underlying network for Eucalyptus cloud

** *WARNING !!!* **
*This role has to be used in the deployment of Eucalyptus cloud. This is not meant to be an angnostic network configuration role !*

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
| networking_mode| MANAGED-NOVLAN | EDGE/MANAGED/MANAGED-NOVLAN| Defines the networking mode used by Eucalyptus | None
| use_vlans | false | true/false|  defines wether or not to use vlans in the backend network|  If set to true, VLAN interfaces will be created by the playbook. Not applicable to MANAGED
| edge_using_private | true | true/false | Defines if EDGE mode should use instances' private address|Applies to EDGE Only

Dependencies
------------

None

Example Playbook
----------------

```
- hosts: all
  roles:
  - eucalyptus-network

```


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

Apache

Author Information
------------------

John Preston [John Mille]
