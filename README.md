cloud3rsio.zabbix40_agent
=========

Install zabbix-agent.

Installation
------------

```bash
$ ansible-galaxy install cloud3rsio.zabbix40_agent
```

Requirements
------------

Nothing.

Role Variables
--------------

| Key | Default Value | Type |
| ------------- | ------------- | ------------- |
| `zabbix40_agent_packages` | Reference to [defaults/main.yml](defaults/main.yml) | Array |
| `zabbix40_agent_Server` | `127.0.0.1/32` | String |
| `zabbix40_agent_ListenPort` | `10050` | Int |
| `zabbix40_agent_ServerActive` |  | String |
| `zabbix40_agent_HostMetadata` |  | String |
| `zabbix40_agent_AllowRoot` | `0` | Int |
| `zabbix40_agent_UserParameters` | `[]` | Array |
| `zabbix40_agent_mysql` | Reference to [defaults/main.yml](defaults/main.yml) | Hash |
| `zabbix40_agent_mysql.user` | `root` | String |
| `zabbix40_agent_mysql.password` | `password` | String |
| `zabbix40_agent_mysql.host` | `localhost` | String |

Dependencies
------------

- `cloud3rsio.yumrepo_zabbix40`

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - role: cloud3rsio.zabbix40_agent
      zabbix40_agent_UserParameters:
        - >-
          redis.status[*],redis-cli info |
          grep -w "$1" |
          awk -F':' '{print $$2}'
      zabbix40_agent_mysql:
        user: root
        password: Passw0rd
        host: 127.0.0.1
```

License
-------

[MIT](LICENSE)

Author Information
------------------

- youyo
