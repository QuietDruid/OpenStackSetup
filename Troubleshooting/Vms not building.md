
Currently VMs aren't building after initial boot but error messages are a little vague on core issue.

Main contenders for issues lie in 2 services, either the nova compute or neutron networking as that was configured later.

Certain error logs of note:

- no provider configs found in /etc/nova/provider_config/ 