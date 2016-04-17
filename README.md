## ansible-logstash

This repository contains an ansible playbook (`logstash.yml`) that installs Logstash to your server (together with Elasticsearch, Kibana and Nginx). It also contains a role that installs Filebeat to your app servers in order to forward the logs to logstash (`roles/filebeat`).

## Usage

Running the playbook:

```
ansible-playbook -i logstash -u vagrant logstash.yml
```

Example of how to add the filebeat role to your app server's playbooks:

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
