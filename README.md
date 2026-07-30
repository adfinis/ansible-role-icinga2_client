ROLE ICINGA2\_CLIENT
====================

[![image](https://img.shields.io/github/license/adfinis/ansible-role-icinga2_client.svg?style=flat-square)](https://github.com/adfinis/ansible-role-icinga2_client/blob/master/LICENSE)

[![image](https://img.shields.io/github/actions/workflow/status/adfinis/ansible-role-icinga2_client/ansible-ci.yml?style=flat-square)](https://github.com/adfinis/ansible-role-icinga2_client/actions)

[![image](https://img.shields.io/badge/galaxy-adfinis.icinga2_client-660198.svg?style=flat-square)](https://galaxy.ansible.com/adfinis/icinga2_client)

This role is used to configure the icinga2 client and request
certificates from the icinga2 master.

Role Variables
--------------

```yaml
# The icinga2 parent hosts. Only 2 allowed.
# https://github.com/Icinga/icinga2/issues/3533
icinga2_client_monitoring_parents:
  - monitoring-master1.example.com
  - monitoring-master2.example.com

# The default icinga2 parent zone
icinga2_client_parent_zone: "monitoring-master"

# How the client certificate gets signed:
#   "delegate" (legacy) -> on-demand CSR signing, runs `icinga2 ca sign` on the
#                          signing master via delegate_to
#   "ticket"            -> CSR auto-signing with a ticket fetched from the
#                          master REST API
icinga2_client_signing_method: delegate

# REST API endpoint of the CA master used to generate signing tickets
icinga2_client_ticket_api_url: "https://{{ icinga2_client_csr_signing_master }}:5665"

# ApiUser on the CA master with the "actions/generate-ticket" permission.
icinga2_client_ticket_api_user: ticket-service
# Password of the ticket ApiUser.
icinga2_client_ticket_api_password: ""

# TLS validation of the master API cert. The API cert is signed by the Icinga
# CA, which the controller usually does not trust; either set this to false,
# or keep it true and point icinga2_client_ticket_api_ca_path at a copy of the
# Icinga CA certificate (ca.crt).
icinga2_client_ticket_api_validate_certs: true
# icinga2_client_ticket_api_ca_path: /etc/ansible/icinga-ca.crt

# Where the ticket API call will be deletegated to.
icinga2_client_ticket_api_delegate: localhost
```

Ticket-based enrollment
-----------------------

With `icinga2_client_signing_method: ticket` the role fetches a signing ticket
from the CA master REST API and passes it to `icinga2 node setup --ticket`, 
so the master signs the CSR automatically.

Requirements on the master (see the icinga2\_master role):

- An `ApiUser` with the `actions/generate-ticket` permission
- The api feature must have `ticket_salt = TicketSalt` set and the
  `TicketSalt` constant must be non-empty, otherwise generate-ticket fails.
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
   - { role: adfinis.icinga2_agent }
   - { role: adfinis.icinga2_client }
```

License
-------

[GPL-3.0](https://github.com/adfinis/ansible-role-icinga2_client/blob/master/LICENSE)

Author Information
------------------

icinga2\_client role was written by:

-   Adfinis SyGroup AG \| [Website](https://www.adfinis.com/) \|
    [Twitter](https://twitter.com/adfinis) \|
    [GitHub](https://github.com/adfinis)
