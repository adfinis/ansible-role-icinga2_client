ROLE ICINGA2\_CLIENT
====================

[![image](https://img.shields.io/github/license/adfinis-sygroup/ansible-role-icinga2_client.svg?style=flat-square)](https://github.com/adfinis-sygroup/ansible-role-icinga2_client/blob/master/LICENSE)

[![image](https://img.shields.io/travis/adfinis-sygroup/ansible-role-icinga2_client.svg?style=flat-square)](https://travis-ci.org/adfinis-sygroup/ansible-role-icinga2_client)

[![image](https://img.shields.io/badge/galaxy-adfinis--sygroup.icinga2_client-660198.svg?style=flat-square)](https://galaxy.ansible.com/adfinis-sygroup/icinga2_client)

This role is used to configure the icinga2 client and request
certificates from the icinga2 master.

Role Variables
--------------

``` {.sourceCode .yaml}
# The icinga2 parent hosts. Only 2 allowed.
# https://github.com/Icinga/icinga2/issues/3533
icinga2_client_monitoring_parents:
  - monitoring-master1.example.com
  - monitoring-master2.example.com

# The default icinga2 parent zone
icinga2_client_parent_zone: "monitoring-master"
```

Dependencies
------------

This role depends on the role
[adfinis-sygroup.icinga2\_agent](https://galaxy.ansible.com/adfinis-sygroup/icinga2_agent),
which installs the icinga2 binary.

Example Playbook
----------------

``` {.sourceCode .yaml}
- hosts: servers
  roles:
   - { role: adfinis-sygroup.icinga2_agent }
   - { role: adfinis-sygroup.icinga2_client }
```

License
-------

[GPL-3.0](https://github.com/adfinis-sygroup/ansible-role-icinga2_client/blob/master/LICENSE)

Author Information
------------------

icinga2\_client role was written by:

-   Adfinis SyGroup AG \| [Website](https://www.adfinis-sygroup.ch/) \|
    [Twitter](https://twitter.com/adfinissygroup) \|
    [GitHub](https://github.com/adfinis-sygroup)
