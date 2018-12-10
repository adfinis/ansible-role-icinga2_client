===================
ROLE ICINGA2_CLIENT
===================

.. image:: https://img.shields.io/github/license/adfinis-sygroup/ansible-role-icinga2_client.svg?style=flat-square
  :target: https://github.com/adfinis-sygroup/ansible-role-icinga2_client/blob/master/LICENSE

.. image:: https://img.shields.io/travis/adfinis-sygroup/ansible-role-icinga2_client.svg?style=flat-square
  :target: https://travis-ci.org/adfinis-sygroup/ansible-role-icinga2_client

.. image:: https://img.shields.io/badge/galaxy-adfinis--sygroup.icinga2_client-660198.svg?style=flat-square
  :target: https://galaxy.ansible.com/adfinis-sygroup/icinga2_client

This role is used to configure the icinga2 client and request certificates from
the icinga2 master.

Role Variables
===============

A description of the settable variables for this role should go here, including
any variables that are in defaults/main.yml, vars/main.yml, and any variables
that can/should be set via parameters to the role. Any variables that are read
from other roles and/or the global scope (ie. hostvars, group vars, etc.)
should be mentioned here as well.


Dependencies
=============

This role depends on the role `adfinis-sygroup.icinga2_agent <https://galaxy.ansible.com/adfinis-sygroup/icinga2_agent>`_, which installs
the icinga2 binary.



Example Playbook
=================


.. code-block:: yaml

  - hosts: servers
    roles:
     - { role: adfinis-sygroup.icinga2_agent }
     - { role: adfinis-sygroup.icinga2_client }


License
========

`GPL-3.0 <https://github.com/adfinis-sygroup/ansible-role-icinga2_client/blob/master/LICENSE>`_


Author Information
===================

icinga2_client role was written by:

* Adfinis SyGroup AG | `Website <https://www.adfinis-sygroup.ch/>`_ | `Twitter <https://twitter.com/adfinissygroup>`_ | `GitHub <https://github.com/adfinis-sygroup>`_
