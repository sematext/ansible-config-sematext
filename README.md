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
    spm_token: SPM_TOKEN
    spm_type: mysql
    mysql_db_user: mysql-user
    mysql_db_pass: mysql-password
  roles:
    - { role: sematext.spm-monitor-config }
```

Elasticsearch:
```
- hosts: all
  become: yes
  vars:
    spm_token: SPM_TOKEN
    spm_type: standalone
    java_app_type: es
  roles:
    - { role: sematext.spm-monitor-config }

```

ZooKeeper:
```
- hosts: all
  become: yes
  vars:
    spm_token: SPM_TOKEN
    spm_type: standalone
    java_app_type: zk
    jmx_params: -Dspm.remote.jmx.url=localhost:3000
  roles:
    - { role: sematext.spm-monitor-config }

```

Kafka:
```
- hosts: all
  become: yes
  vars:
    spm_token: SPM_TOKEN
    spm_type: standalone
    java_app_type: kafka
  roles:
    - { role: sematext.spm-monitor-config, java_app_subtype: kafka-broker, jmx_params: "-Dspm.remote.jmx.url=localhost:3000" }
    - { role: sematext.spm-monitor-config, java_app_subtype: kafka-producer, jmx_params: "-Dspm.remote.jmx.url=localhost:3001" }
    - { role: sematext.spm-monitor-config, java_app_subtype: kafka-consumer, jmx_params: "-Dspm.remote.jmx.url=localhost:3002" }
```

License
-------

Apache2

Author Information
------------------

Ciprian Hacman <ciprian.hacman@sematext.com>
