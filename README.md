
## OCI-RSA-Ansible-ODFE
This stack contains the [Wazuh](https://wazuh.com/) cluster elastic search playbook, which automates the deployment and configuration of Open Distro for Elasticsearch in a 3 node cluster.

## Requirements


## Dependencies
This playbook uses the following roles:
- [oci-rsa-ansible-base]()
- [role: wazuh-odfe]()
- [role: geerlingguy.clamav]()
- [role: wazuh-ansible/wazuh-ansible/roles/opendistro/opendistro-elasticsearch]()


## Branches
* `main` branch contains the latest code.

## Documentation

* [Wazuh Ansible documentation](https://documentation.wazuh.com/current/deploying-with-ansible/index.html)
* [Full documentation](http://documentation.wazuh.com)

## Code style

[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://github.com/oracle-quickstart) 

## Usage
Launching the playbook

```
ansible-playbook -i localhost, $OCI_RSA_BASE/${playbook_name}/main.yml --connection=local
```

## Tech/framework used

<b>Built with</b>
- [Ansible](https://documentation.wazuh.com/current/deploying-with-ansible/index.html) core 2.11.0 


## How to Contribute
Interested in contributing?  See our contribution [guidelines](CONTRIBUTE.md) for details.

## License
This repository and its contents are licensed under [UPL 1.0](https://opensource.org/licenses/UPL).    

