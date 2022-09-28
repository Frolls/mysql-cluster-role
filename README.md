Mysql-cluster-role
====================

Отказоустойчивый кластер баз данных MySQL.

MySQL работает в режиме репликации Master/Slave.

В кластере автоматически создаётся база данных c именем `wordpress`.

В кластере автоматически создаётся пользователь `wordpress` с полными правами на базу `wordpress` и паролем `wordpress`.

Requirements
------------

Какие-то специальные рекомендации отсутствуют


Role Variables
--------------

Смотри `defaults/mai.yml`

Может пригодиться пример inventory:

```yml
    dbservers:
      hosts:
        db01:
          db_role: master
        db02:
          db_role: slave

    db_cluster:
      vars:
        mysql_replication_master: <address>
      children:
        dbservers:

```

Dependencies
------------

None

Example Playbook
----------------

```yml
- name: Create MySQL-cluster
  hosts: dbservers
  roles:
    - role: mysql-cluster-role
```

License
-------

BSD

Author Information
------------------

Frolls
