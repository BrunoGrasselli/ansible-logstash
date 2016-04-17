## ansible-logstash

This repository contains an ansible playbook (`logstash.yml`) for provisioning servers with logstash (elasticsearch, kibana and nginx). It also contains a role for installing filebeat to your app servers in order to forward the logs to logstash (`roles/filebeat`).

## Usage

Running the playbook:

```
ansible-playbook -i logstash -u vagrant logstash.yml
```

Adding the filebeat role to your app playbook (example):

```
- hosts: app-vagrant
  remote_user: vagrant
  become: yes
  vars:
    logs_path: "/home/vagrant/fakeapp/log/*.log"
  vars_files:
     - variables/logstash/vagrant
  roles:
     - filebeat
```
