Zabbix Client
=============

This play will install the zabbix Agent on your clients
The Client will also be added into the Zabbix server with the correct template and group

Requirements
------------

Centos-RHEL 6.5/7

Version
-------
v2 19/6/2015

Role Variables
--------------

All variables are set in default\main.yml

```yaml

# Please adjust these parameters to your own needs
zbx_repo_enabled: 1                                     # Put 0 to use your own local repo
zbx_agent_Version: "2.4.4"                              # Desired version of the client
zbx_agent_HostName:                                     # If not set hostname from machine will be taken.
zbx_server_Passive: "192.168.1.1"                       # Passive Server Checks
zbx_agent_ServerActive: "192.168.1.1"                   # Active Server Checks
zbx_agent_Group: "Discovered hosts"                     # Zabbix hostgroup where host has to be added
zbx_agent_Template: "Template OS Linux"                 # Zabbix template to link with the host


# API
server_url: "http://192.168.1.1/api_jsonrpc.php"        # Add the url to the API
login_user: "Administrator"                             # Login for the user with API rights
login_password: "zabbix"                                # Password for the API user
host_groups:                                            # List of host groups the host should belong to start each group with -
          - "Linux servers"
link_templates:                                         # A list of templates that need to be linked to the host
          - "Template OS Linux"
status: "enabled"                                       # Status of the host enabled or disabled
state: "present"

# Zabbix Repository & Epel repos
zbx_repo6: "http://repo.zabbix.com/zabbix/2.4/rhel/6/x86_64/zabbix-release-2.4-1.el6.noarch.rpm"
zbx_repo7: "http://repo.zabbix.com/zabbix/2.4/rhel/7/x86_64/zabbix-release-2.4-1.el7.noarch.rpm"
epel_repo6: "http://fedora.cu.be/epel/6/i386/epel-release-6-8.noarch.rpm"
epel_repo7: "http://epel.mirror.nucleus.be/7/x86_64/e/epel-release-7-5.noarch.rpm"



# General Zabbix Agent Parameters

zbx_agent_Pid: "/var/run/zabbix/zabbix_agentd.pid"      # Location of Agent PID File
zbx_agent_Log: "/var/log/zabbix/zabbix_agentd.log"      # Location of Agent Log File
zbx_agent_LogSize: 0                                    # Log File Size In MB ( 0 = disabled Log Rotation )
zbx_agent_Debug: 1                                      # Debug Level (0 = no debug, 1=critical, 2=error info, 3=warnings, 4=debug )
zbx_agent_SourceIp:                                     # Source IP address for outgoing connections.
zbx_agent_Remote: 0                                     # Enable remote commands ( 0=disabled, 1=enabled)
zbx_agent_LogRemote: 0                                  # Log Remote Commands ( Enable logging of executed commands )
zbx_agent_Port: 10050                                   # Zabbix Agent Listen Port (if changed also alter tasks/iptables.yml
zbx_agent_ListenIp:                                     # Agent Listen Ip
zbx_agent_StartAgents: 3                                # Number of Pre-Forked Instances of zabbix_agentd
zbx_agent_HostName:                                     # Put the hostname if not filled in name of the machine is used
zbx_agent_HostMeta:                                     # Optional parameter that defines host metadata.
zbx_agent_HostMetaItem:                                 # Optional parameter that defines an item used for getting host metadata
zbx_agent_RefreshActiveChecks: 120                      # How often list of active checks is refreshed, in seconds.
zbx_agent_Buffer: 5                                     # Do not keep data longer then N seconds in buffer.
zbx_agent_BufferSize: 100                               # Maximum number of values in a memory buffer
zbx_agent_MaxLinesSecond: 100                           # Maximum number of new lines the agent will send per second to Zabbix Server

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

Centos/RHEL 6.5 or 7 is needed

Todo
----

* Make the module also workable for Debian


License
-------

GPLv2

Author Information
------------------
* Patrik Uytterhoeven
* patrik( at )open-future.be
* [www.open-future.be](http://www.open-future.be)

