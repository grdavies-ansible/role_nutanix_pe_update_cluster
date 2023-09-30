# Nutanix Role to update the settings on a Prism Element cluster

This Ansible role get the list of available IP addresses from an AHV IPAM enabled subnet and attempts to provide the first free IP address from that range.

## Role Variables

| Variable                                           | Required | Default         | Choices                                                                         | Comments                                                                                                                                                                                                                          |
|----------------------------------------------------|----------|-----------------|---------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| role_nutanix_pe_update_cluster_host                | yes      |                 |                                                                                 | The IP address or FQDN for the Prism (Element only) to which you want to connect.                                                                                                                                                 |
| role_nutanix_pe_update_cluster_host_username       | yes      |                 |                                                                                 | A valid username with appropriate rights to access the Nutanix API.                                                                                                                                                               |
| role_nutanix_pe_update_cluster_host_password       | yes      |                 |                                                                                 | A valid password for the supplied username.                                                                                                                                                                                       |
| role_nutanix_pe_update_cluster_host_port           | no       | 9440            |                                                                                 | The Prism TCP port.                                                                                                                                                                                                               |
| role_nutanix_pe_update_cluster_host_validate_certs | no       | no              |                                                                                 | Whether to check if Prism UI certificates are valid.                                                                                                                                                                              |
| role_nutanix_pe_update_cluster_name                | no       |                 |                                                                                 |                                                                                                                                                                                                                                   |
| role_nutanix_pe_update_cluster_virtual_ip          | no       |                 |                                                                                 | Set to a valid IPv4 address in the same subnet as the CVMs                                                                                                                                                                        |
| role_nutanix_pe_update_data_services_ip            | no       |                 |                                                                                 | Set to a valid IPv4 address in the same subnet as the CVMs/Cluster VIP                                                                                                                                                            |
| role_nutanix_pe_update_rf_level                    | no       |                 | [ 1, 2 3 ]                                                                      | Should be set to match the desired RF level; 1, 2 or 3                                                                                                                                                                            |

### Returned Variables

None

## Dependencies

- grdavies.role_nutanix_prism_api
- grdavies.role_nutanix_prism_monitor_task

## Example Playbook

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_pe_update_cluster
  vars:
    role_nutanix_pe_update_cluster_host: "10.42.70.37"
    role_nutanix_pe_update_cluster_host_username: admin
    role_nutanix_pe_update_cluster_host_password: nx2Tech075!
    role_nutanix_pe_update_cluster_name: NEW_CLUSTER_NAME
```

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_pe_update_cluster
  vars:
    role_nutanix_pe_update_cluster_host: "10.42.70.37"
    role_nutanix_pe_update_cluster_host_username: admin
    role_nutanix_pe_update_cluster_host_password: nx2Tech075!
    role_nutanix_pe_update_data_services_ip: 10.42.70.38
```


## License

See LICENSE.md

## Author Information

Ross Davies
