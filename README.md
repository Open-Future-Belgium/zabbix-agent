Zabbix Client
=============

This play will install the zabbix Agent on your clients

Requirements
------------

Centos 6x or Rhel 6x

Role Variables
--------------

All variables are set in default\main.yml

```yaml

# Zabbix Repository
zbx_repo_enabled: 1
zbx_repo: "http://repo.zabbix.com/zabbix/2.2/rhel/6/x86_64/zabbix-release-2.2-1.el6.noarch.rpm"

# defaults file for Zabbix-Agent

# Zabbix Client Version
zbx_agent_Version: "2.2.2"

# General Zabbix Agent Parameters

zbx_agent_Pid: "/var/run/zabbix/zabbix_agentd.pid"
zbx_agent_Log: "/var/log/zabbix/zabbix_agentd.log"
zbx_agent_LogSize: 0
zbx_agent_Debug: 1
zbx_agent_SourceIp:
zbx_agent_Remote: 0
zbx_agent_LogRemote: 0
zbx_server_Passive: "192.168.1.1"
zbx_agent_ServerActive: "192.168.1.1"
zbx_agent_Port: 10050
zbx_agent_ListenIp:
zbx_agent_StartAgents: 3
zbx_agent_HostName:
zbx_agent_HostMeta:
zbx_agent_HostMetaItem:
zbx_agent_RefreshActiveChecks: 120
zbx_agent_Buffer: 5
zbx_agent_BufferSize: 100
zbx_agent_MaxLinesSecond: 100 

# Advanced Zabbix Agent Parameters

zbx_agent_Timeout: 3
zbx_agent_AllowRoot: 0
zbx_agent_Include: 
                  - "/etc/zabbix/zabbix_agentd.d/"


# USER-DEFINED Zabbix Agent Monitored Parameters

zbx_agent_UnsafeUserParam: 0
zbx_agent_UserParameter: []
zbx_agent_LoadModulePath:
zbx_agent_Modules: []
```

Dependencies
------------

No other roles are needed.

Todo
----

* Make the module also workable for Debian 
* Let is automatic register on the zabbix server


License
-------

GPLv2

Author Information
------------------
* Patrik Uytterhoeven
* patrik( at )open-future.be
* [www.open-future.be](http://www.open-future.be)

