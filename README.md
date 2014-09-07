Zabbix Client
=============

This play will install the zabbix Agent on your clients
The Client will also be added into the Zabbix server with the correct template and group

Requirements
------------

Centos 6.5 or Rhel 6.5

Version
-------
7/9/2014

Role Variables
--------------

All variables are set in default\main.yml

```yaml
---
# Please adjust these parameters to your own needs
zbx_repo_enabled: 1                                     # Put 0 to use your own
local repo
zbx_agent_Version: "2.2.5"                              # Desired version of the
client
zbx_agent_HostName:                                     # If not set hostname
from machine will be taken.
zbx_server_Passive: "192.168.10.102"                    # Passive Server Checks
zbx_agent_ServerActive: "192.168.10.102"                # Active Server Checks
zbx_agent_Group: "Discovered hosts"                     # Zabbix hostgroup where
host has to be added
zbx_agent_Template: "Template OS Linux"                 # Zabbix template to
link with the host

# API
api_admin: "Admin"
api_password: "zabbix"

# Zabbix Repository & Epel repos
zbx_repo:
"http://repo.zabbix.com/zabbix/2.2/rhel/6/x86_64/zabbix-release-2.2-1.el6.noarch.rpm"
epel_repo: "http://epel.mirror.nucleus.be/6/i386/epel-release-6-8.noarch.rpm"



# General Zabbix Agent Parameters

zbx_agent_Pid: "/var/run/zabbix/zabbix_agentd.pid"      # Location of Agent PID
File
zbx_agent_Log: "/var/log/zabbix/zabbix_agentd.log"      # Location of Agent Log
File
zbx_agent_LogSize: 0                                    # Log File Size In MB (
0 = disabled Log Rotation )
zbx_agent_Debug: 1                                      # Debug Level (0 = no
debug, 1=critical, 2=error info, 3=warnings, 4=debug )
zbx_agent_SourceIp:                                     # Source IP address for
outgoing connections.
zbx_agent_Remote: 0                                     # Enable remote commands
( 0=disabled, 1=enabled)
zbx_agent_LogRemote: 0                                  # Log Remote Commands (
Enable logging of executed commands )
zbx_agent_Port: 10050                                   # Zabbix Agent Listen
Port (if changed also alter tasks/iptables.yml
zbx_agent_ListenIp:                                     # Agent Listen Ip
zbx_agent_StartAgents: 3                                # Number of Pre-Forked
Instances of zabbix_agentd
zbx_agent_HostName:                                     # Put the hostname if
not filled in name of the machine is used
zbx_agent_HostMeta:                                     # Optional parameter
that defines host metadata.
zbx_agent_HostMetaItem:                                 # Optional parameter
that defines an item used for getting host metadata
zbx_agent_RefreshActiveChecks: 120                      # How often list of
active checks is refreshed, in seconds.
zbx_agent_Buffer: 5                                     # Do not keep data
longer then N seconds in buffer.
zbx_agent_BufferSize: 100                               # Maximum number of
values in a memory buffer
zbx_agent_MaxLinesSecond: 100                           # Maximum number of new
lines the agent will send per second to Zabbix Server

# Advanced Zabbix Agent Parameters

zbx_agent_Timeout: 3                                    # Spend no more than
Timeout seconds on processing
zbx_agent_AllowRoot: 0                                  # Allow the agent to run
as 'root'
zbx_agent_Include:                                      # Possible to add
multiple lines start always with - like next line.
                  - "/etc/zabbix/zabbix_agentd.d/"      # You may include
                    individual files or all files in a directory in the cfg
                    file.


# USER-DEFINED Zabbix Agent Monitored Parameters

zbx_agent_UnsafeUserParam: 0
zbx_agent_UserParameter: []                             # Add one or more lines
with user parameters same as with zbx_agent_Include
zbx_agent_LoadModulePath:                               # Add path of the
loadable modules
zbx_agent_Modules: []                                   # Add one or more lines
with modules module.so

Dependencies
------------

Centos 6.5 or Rhel 6.5 are needed only if Selinux is an issue as in the latest update of SeLinux a new Zabbix policy is added.

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

