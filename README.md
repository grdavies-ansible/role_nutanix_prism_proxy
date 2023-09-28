# Nutanix Role for Prism HTTP proxy server configuration

This Ansible role sets the HTTP proxy configuration for Prism Element and Prism Central.


## Input Variables

| Variable                 | Required | Default  | Choices                                                                         | Comments                                                                                                                                           |
|--------------------------|----------|----------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| role_nutanix_prism_proxy_host                | yes      |          |                                                                                 | The IP address or FQDN for the Prism (Element or Central) to which you want to connect.                                                            |
| role_nutanix_prism_proxy_host_username       | yes      |          |                                                                                 | A valid username with appropriate rights to access the Nutanix API.                                                                                |
| role_nutanix_prism_proxy_host_password       | yes      |          |                                                                                 | A valid password for the supplied username.                                                                                                        |
| role_nutanix_prism_proxy_host_port           | no       | 9440     |                                                                                 | The Prism TCP port.                                                                                                                                |
| role_nutanix_prism_proxy_host_validate_certs | no       | no       | yes / no                                                                        | Whether to check if Prism UI certificates are valid.                                                                                               |
| role_nutanix_prism_proxy_name         | yes      |          |                                                                                 | Name for the proxy server in the Prism UI                                                                                                          |
| role_nutanix_prism_proxy_address      | yes      |          |                                                                                 | FQDN or IP address for the proxy server                                                                                                            |
| role_nutanix_prism_proxy_port         | yes      |          |                                                                                 | TCP port for the proxy server                                                                                                                      |
| role_nutanix_prism_proxy_types        | no       | ['http'] | ['http', 'https']                                                               | Whether to proxy http traffic, https traffic or both                                                                                               |
| role_nutanix_prism_proxy_username     | no       |          |                                                                                 | Username to authenticate to the proxy server                                                                                                       |
| role_nutanix_prism_proxy_password     | no       |          |                                                                                 | Password for username to authenticate to the proxy server                                                                                          |
| role_nutanix_prism_proxy_whitelist    | no       | []       |                                                                                 | List of FQDNs or IP addresses to be added to the proxy whitelist                                                                                   |


## Dependencies

- grdavies.role_nutanix_prism_api

## Example Playbook

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_prism_proxy
  vars:
    role_nutanix_prism_proxy_host: 10.38.185.37
    role_nutanix_prism_proxy_host_username: admin
    role_nutanix_prism_proxy_host_password: nx2Tech165!
    role_nutanix_prism_proxy_name: my_proxy
    role_nutanix_prism_proxy_address: proxy.ntnxlab.local
    role_nutanix_prism_proxy_port: 8080
    role_nutanix_prism_proxy_types:
      - http
      - https
    role_nutanix_prism_proxy_whitelist:
      - "*.ntnxlab.local"
```


## License

See LICENSE.md

## Author Information

Ross Davies
