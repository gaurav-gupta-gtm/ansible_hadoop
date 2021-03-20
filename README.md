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
  become: true
  roles:
  -  role: hadoop-config

- name: Setup Master Node
  hosts: master
  become: true
  roles:
  - role: master-setup

- name: Setup Slave  Node
  hosts: slave
  become: true
  roles:
  - role: slave-setup
```

### Running role:

```
ansible all -m include_role -a 'name=hodoop-config'
```
