Ansible Sematext SPM Monitor Configure Role
===========================================

Configure Sematext SPM Monitor.

Dependencies
------------
None

Example Playbooks
-------------------------
MySQL:
```
- hosts: all
  become: yes
  vars:
    monitoring_token: MONTIORING_TOKEN
    infra_token: INFRA_TOKEN
    agent_type: standalone
    app_type: mysql
    args:
      SPM_MONITOR_MYSQL_DB_USER: mysql-user
      SPM_MONITOR_MYSQL_DB_PASSWORD: mysql-password
  roles:
    - { role: sematext.spm-monitor-config }
```

Elasticsearch:
```
- hosts: all
  become: yes
  vars:
    monitoring_token: MONTIORING_TOKEN
    infra_token: INFRA_TOKEN
    agent_type: standalone
    app_type: elasticsearch
    args:
      SPM_MONITOR_ES_NODE_HOSTPORT: 'localhost:9200'
  roles:
    - { role: sematext.spm-monitor-config }

```

ZooKeeper:
```
- hosts: all
  become: yes
  vars:
    monitoring_token: MONTIORING_TOKEN
    infra_token: INFRA_TOKEN
    agent_type: standalone
    app_type: zookeeper
    args:
      jmx_host: localhost
      jmx_port: 3000
  roles:
    - { role: sematext.spm-monitor-config }

```

Kafka:
```
- hosts: all
  become: yes
  vars:
    monitoring_token: MONTIORING_TOKEN
    infra_token: INFRA_TOKEN
    agent_type: standalone
    app_type: kafka
  roles:
    - { role: sematext.spm-monitor-config, app_subtype: kafka-broker, args: [jmx_host: 'localhost', jmx_port: 3000]}
    - { role: sematext.spm-monitor-config, app_subtype: kafka-producer, args: [jmx_host: 'localhost', jmx_port: 3001]}
    - { role: sematext.spm-monitor-config, app_subtype: kafka-consumer, args: [jmx_host: 'localhost', jmx_port: 3002]}
```

License
-------

Apache2

Author Information
------------------

Ciprian Hacman <ciprian.hacman@sematext.com>
