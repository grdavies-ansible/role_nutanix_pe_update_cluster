# Nutanix Role to update the settings on a Prism Element cluster

This Ansible role get the list of available IP addresses from an AHV IPAM enabled subnet and attempts to provide the first free IP address from that range.

## Requirements

NA

## Role Variables

| Variable                                    | Required | Default         | Choices                                                                         | Comments                                                                                                                                                                                                                          |
|---------------------------------------------|----------|-----------------|---------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| nutanix_host                                | yes      |                 |                                                                                 | The IP address or FQDN for the Prism (Element only) to which you want to connect.                                                                                                                                                 |
| nutanix_username                            | yes      |                 |                                                                                 | A valid username with appropriate rights to access the Nutanix API.                                                                                                                                                               |
| nutanix_password                            | yes      |                 |                                                                                 | A valid password for the supplied username.                                                                                                                                                                                       |
| nutanix_port                                | no       | 9440            |                                                                                 | The Prism TCP port.                                                                                                                                                                                                               |
| validate_certs                              | no       | no              |                                                                                 | Whether to check if Prism UI certificates are valid.                                                                                                                                                                              |
| update_cluster_name                         | no       |                 |                                                                                 |                                                                                                                                                                                                                                   |
| update_cluster_virtual_ip                   | no       |                 |                                                                                 | Set to a valid IPv4 address in the same subnet as the CVMs                                                                                                                                                                        |
| update_data_services_ip                     | no       |                 |                                                                                 | Set to a valid IPv4 address in the same subnet as the CVMs/Cluster VIP                                                                                                                                                            |
| update_rf_level                             | no       |                 | [ 1, 2 3 ]                                                                      | Should be set to match the desired RF level; 1, 2 or 3                                                                                                                                                                            |

### Returned Variables

None

## Example Playbook

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_pe_update_cluster
  vars:
    nutanix_host: "10.42.70.37"
    nutanix_username: admin
    nutanix_password: nx2Tech075!
    update_cluster_name: NEW_CLUSTER_NAME
```

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_pe_update_cluster
  vars:
    nutanix_host: "10.42.70.37"
    nutanix_username: admin
    nutanix_password: nx2Tech075!
    update_data_services_ip: 10.42.70.38
```


## License

See LICENSE.md

## Author Information

Ross Davies
