

| VMNAME  | Hostname                | vSPECS  | Storage     | Control/STAGEnet IP | LAN IP      | ROLE                      |
| ------- | ----------------------- | ------- | ----------- | ------------------- | ----------- | ------------------------- |
| opcsax1 | opstax1.openstack.local | 4c/16gb | 50gb        | 10.0.0.15           | 172.16.1.18 | control, compute          |
| opstax2 | opstax2.openstack.local | 4c/16gb | 32gb + 75gb | 10.0.0.10           | 172.16.1.13 | control, compute, storage |
| opstax3 | --                      | --      | --          | --                  | --          | --                        |
| opstax4 | opstax3.openstack.local | 4c/8gb  | 32gb + 50gb | 10.0.0.17           | 172.16.1.20 | control, compute storage  |
| opstax5 | opstax4.openstack.local | 4c/8gb  | 50gb        | 10.0.0.16           | 172.16.1.19 | control, compute          |
|         |                         |         |             |                     |             |                           |
| node1   | admin1                  | 4c/8gb  | 32gb        | 10.0.0.19           |             |                           |
| worker1 |                         |         |             | -20                 |             |                           |
