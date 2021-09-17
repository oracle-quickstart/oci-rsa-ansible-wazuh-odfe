
## OCI-RSA-Ansible-ODFE
This stack contains the [Wazuh](https://wazuh.com/) cluster elastic search playbook, which automates the deployment and configuration of Open Distro for Elasticsearch in a 3 node cluster.

## Requirements
- [Ansible core](https://docs.ansible.com/ansible-core/devel/index.html) >= 2.11.0
- Oracle Linux >= 7.9

## Dependencies

A list of other roles hosted on Galaxy:

* [geerlingguy.clamav](https://github.com/geerlingguy/ansible-role-clamav): Installs ClamAV on RedHat Linux server.
* [wazuh-ansible](https://github.com/wazuh/wazuh-ansible): These playbooks install and configure Wazuh agent, manager and Elastic Stack
    - [wazuh-opendistro-elasticsearch](https://github.com/wazuh/wazuh-ansible/tree/master/roles/opendistro/opendistro-elasticsearch) An Ansible Role that installs Elasticsearch.

A list of other roles hosted on Github:
* [oci-rsa-ansible-base](pending...): Installs base packages and sets configuration for general security, montoring, and auditing purposes.

## Code style

[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://github.com/oracle-quickstart) 

## Branches

* `main` branch contains the latest code.

## Usage
Launching the playbook

```
ansible-playbook -i localhost, $OCI_RSA_BASE/${playbook_name}/main.yml --connection=local
```

## Documentation

* [Wazuh Ansible documentation](https://documentation.wazuh.com/current/deploying-with-ansible/index.html)
* [Full documentation](http://documentation.wazuh.com)

## How to Contribute
Interested in contributing?  See our contribution [guidelines](CONTRIBUTE.md) for details.

## License
This repository and its contents are licensed under [UPL 1.0](LICENSE).    

