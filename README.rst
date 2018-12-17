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

.. code-block:: yaml

  # The icinga2 parent hosts. Only 2 allowed.
  # https://github.com/Icinga/icinga2/issues/3533
  icinga2_client_monitoring_parents:
    - monitoring-master1.example.com
    - monitoring-master2.example.com

  # The default icinga2 parent zone
  icinga2_client_parent_zone: "monitoring-master"

  # The API url of the icinga2 master. Defaults to the first parent
  icinga2_client_api_url: "https://{{ icinga2_client_master_fqdn[0] }}:5665"

  # The API user of the icinga2 master
  # The user needs at least permissions to create ticket tokens.
  icinga2_client_api_user: "root"

  # The API password of the icinga2 master
  icinga2_client_api_pass: "v3rys3cur3p455"


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
