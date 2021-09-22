OCI-RSA-ANSIBLE-ODFE
=========

Installs [Open Distro for Elasticsearch](https://opendistro.github.io/for-elasticsearch/). 
Used to deploy Elasticsearch nodes in a Wazuh cluster.

Requirements
------------
- [Ansible core](https://docs.ansible.com/ansible-core/devel/index.html) >= 2.9.x
- [Oracle Autonomous Linux](https://www.oracle.com/linux/autonomous-linux/) >= 7.9

Role Variables
--------------
Open Distro for Elasticsearch version.
```
opendistro_version: 1.13.2
```

Configure elastic cluster node network settings. The domain_name variable refers to the subnet domain name.
```
single_node: false
elasticsearch_node_name: '{{ ansible_fqdn }}'
domain_name: 'wazuhsubnet.primaryvcn.oraclevcn.com'
opendistro_cluster_name: wazuh
elasticsearch_network_host: '0.0.0.0'
elasticsearch_node_master: true
elasticsearch_node_data: true
elasticsearch_node_ingest: true
elasticsearch_lower_disk_requirements: false
```
Certificate generation is set to false becuase it is done locally whithin the wazuh-odfe role.
```
generate_certs: false
local_certs_path: "/etc/ssl/local"
```

Instance file config. Sets ip mapping and node domain names.
```
instances:
  node1:
    name: 'elasticnode0'
    ip: "{{ lookup('dig', 'elasticnode0.{{ domain_name }}')}}"
  node2:
    name: 'elasticnode1'
    ip: "{{ lookup('dig', 'elasticnode1.{{ domain_name }}')}}"
  node3:
    name: 'elasticnode2'
    ip: "{{ lookup('dig', 'elasticnode2.{{ domain_name }}')}}"

elasticsearch_cluster_nodes:
  - "{{ instances.node1.name }}.{{ domain_name }}"
  - "{{ instances.node2.name }}.{{ domain_name }}"
  - "{{ instances.node3.name }}.{{ domain_name }}"
elasticsearch_discovery_nodes:
  - "{{ instances.node1.name }}.{{ domain_name }}"
  - "{{ instances.node2.name }}.{{ domain_name }}"
  - "{{ instances.node3.name }}.{{ domain_name }}"
```

Dependencies
---------------

None

Example Playbook
----------------
Use the oci-rsa-ansible-base role before to install required software. An `extra-variables.yml` file can also be used to pass in other variables.

```
- hosts: all
  vars_files:
    - ../extra-variables.yml
  roles: 
    - role: oci-rsa-ansible-base
    - role: wazuh-odfe
      become: true
```

License
-------

This repository and its contents are licensed under UPL 1.0.