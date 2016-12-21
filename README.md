Role Name
=========

Role that install Shipyard on a Swarm Cluster configured with gchiesa.swarm role

Role Variables
--------------

The Shipyard interface is setup based on the hosts in the hostgroups used by
gchiesa.swarm:

__swarm_managers__ : should contain the manager nodes

__swarm_agents__ : should contain all the node that should be part of the swarm cluster

Dependencies
------------

```gchiesa.swarm``` and its dependencies


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
---
- hosts: servers
  roles:
     - { role: gchiesa.swarm, x: 42 }
```

inventory looks like:

```
[targets:vars]
ansible_host=localhost
ansible_become=true
ansible_ssh_user=vagrant
ansible_ssh_private_key_file=~/.vagrant.d/insecure_private_key
proxy=

[consul_cluster:vars]
consul_bootstrap_hostname=test01.local

[targets]
test01.local ansible_port=2200
test02.local ansible_port=2201
test03.local ansible_port=2202
test04.local ansible_port=2203

[consul_cluster]
test01.local
test02.local
test03.local

[swarm_agents]
test01.local
test02.local
test03.local
test04.local

[swarm_managers]
test01.local
test02.local
```

License
-------

BSD
