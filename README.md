Ansible Hadoop Collection
==============================

- Hadoop Config: Install necessary software eg: Hadoop, JDK
- master-setup: Configure conf file in master node and start services
- slave-setup: Configure conf file in all data node and start service

Tested on:
----------

- RHEL 8
- Amazon Linux 2

Prerequisite:
-------------

- Make sure you have two groups in inventory file: master and slave

Example
-------

### Install the role:

```bash
ansible-galaxy collection install gaurav-gupta-gtm.ansible_hadoop
```


### playbook.yml example

```yaml
- name: Install Necessary Software
  hosts: all
  roles:
  -  role: hadoop_config

- name: Setup Master Node
  hosts: master
  roles:
  - role: master_setup

- name: Setup Slave  Node
  hosts: slave
  become: true
  roles:
  - role: slave_setup
```

### Running role:

```
ansible all -m include_role -a 'name=hadoop_config'
```

More Details:
-------------

[Click here for know more how to use it](https://techq.medium.com/setup-a-multi-node-hadoop-cluster-using-ansible-by-gaurav-gupta-7dc88d53f26f)
[Ansible-Galaxy URL](https://galaxy.ansible.com/gaurav_gupta_gtm/ansible_hadoop)

