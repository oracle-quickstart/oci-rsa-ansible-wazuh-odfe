
## OCI-RSA-ANSIBLE-ODFE
This stack contains the [Wazuh](https://documentation.wazuh.com/current/index.html) cluster elastic search playbook, 
which automates the deployment and configuration of [Open Distro for Elasticsearch](https://opendistro.github.io/for-elasticsearch/) 
(ODFE) in a 3 node cluster.

## Ansible Role: wazuh-odfe
Detailed information on the wazuh-odfe role and role variables can be found [here](/wazuh-odfe/README.md). 

## Ansible Role: wazuh-ansible
We are using **Galaxy** which provides pre-packaged units of work known to Ansible as roles and collections. Content 
from roles and collections of the **wazuh-ansible** are referenced in oci-rsa-ansible-wazuh-odfe. This playbook installs and 
configures Wazuh agent and manager.

## Ansible Role: oci-rsa-ansible-base
Detailed information on the oci-rsa-ansible-base can be found [here](https://github.com/oracle-quickstart/oci-rsa-ansible-base)).

## Requirements
- [Ansible core](https://docs.ansible.com/ansible-core/devel/index.html) >= 2.9.x
- [Oracle Autonomous Linux](https://www.oracle.com/linux/autonomous-linux/) >= 7.9

## Dependencies

A list of other roles hosted on Galaxy:

* [wazuh-ansible](https://github.com/wazuh/wazuh-ansible): These playbooks install and configure Wazuh agent, manager and 
  Elastic Stack
    - [wazuh-opendistro-elasticsearch](https://github.com/wazuh/wazuh-ansible/tree/master/roles/opendistro/opendistro-elasticsearch) 
      An Ansible Role that installs Open Distro for Elasticsearch.

A list of other roles hosted on Github:
* [oci-rsa-ansible-base](https://github.com/oracle-quickstart/oci-rsa-ansible-base): Installs base packages and sets configuration for general security, montoring, 
  and auditing purposes.

## Branches

* `main` branch contains the latest code.

## Usage
There are multiple ways to run Ansible playbook, but for our project we choose to pull down the bundled playbook from 
the OCI Object Storage bucket and then run the following command to configure each of the hosts locally.

```
ansible-playbook -i localhost, $OCI_RSA_BASE/${playbook_name}/main.yml --connection=local
```

An `extra_variables.yml` file is required to set the variables below. Here the Wazuh password, Open Distro Kibana 
username and password can be set by the user.
```
opendistro_admin_password: "${}"
opendistro_kibana_password: "${}"
```

This is a wrapper which configures the Wazuh cluster. To deploy the infrastructure and configure the cluster on instance nodes,
our team recommends a specific workflow. Detailed explanation of the recommended workflow can be found [here](WORKFLOW.md). 

## Documentation

* [Wazuh Ansible documentation](https://documentation.wazuh.com/current/deploying-with-ansible/index.html)
* [Full documentation](http://documentation.wazuh.com)

## The Team
This repository was developed by the Oracle OCI Regulatory Solutions and Automation (RSA) team.

## How to Contribute
Interested in contributing?  See our contribution [guidelines](CONTRIBUTE.md) for details.

## License
This repository and its contents are licensed under [UPL 1.0](LICENSE).    
