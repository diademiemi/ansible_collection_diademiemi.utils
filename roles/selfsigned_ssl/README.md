Ansible Role Template
=========

[![Molecule test](https://github.com/diademiemi/ansible_collection_diademiemi.utils/actions/workflows/ansible-role-selfsigned_ssl.yml/badge.svg)](https://github.com/diademiemi/ansible_collection_diademiemi.utils/actions/workflows/ansible-role-selfsigned_ssl.yml)
This is an Ansible role to install and configure selfsigned_ssl.

Include more information about selfsigned_ssl in this section.

Requirements
------------
These platforms are supported:
- Ubuntu 20.04
- Ubuntu 22.04
- Debian 10
- Debian 11
- EL 8 (Tested on Rocky Linux 8)
- EL 9 (Tested on Rocky Linux 9)
- Fedora 38
- openSUSE Leap 15.4

<!--
- List hardware requirements here  
-->

Role Variables
--------------

Variable | Default | Description
--- | --- | ---
Variable | Default | Description
---|---|---
`utils_selfsigned_ssl_ca_name` | `'selfsigned-ca'` | Name of the self-signed Certificate Authority.
`utils_selfsigned_ssl_ca_path` | `'/etc/openssl/certs/ca'` | File path where the CA certificate will be stored.
`utils_selfsigned_ssl_ca_key_file` | `'{{ utils_selfsigned_ssl_ca_name }}.key'` | File name for the CA key.
`utils_selfsigned_ssl_ca_pem_file` | `'{{ utils_selfsigned_ssl_ca_name }}.pem'` | File name for the CA PEM certificate.
`utils_selfsigned_ssl_cert_key_path` | `'/etc/pki/tls/private/'` | Directory path where the SSL certificate key will be stored.
`utils_selfsigned_ssl_cert_pem_path` | `'/etc/pki/tls/certs/'` | Directory path where the SSL certificate will be stored.
`utils_selfsigned_ssl_cert_name` | `'generic'` | Name of the self-signed SSL certificate.
`utils_selfsigned_ssl_cert_key_file` | `'{{ utils_selfsigned_ssl_cert_name }}.key'` | File name for the SSL certificate key.
`utils_selfsigned_ssl_cert_pem_file` | `'{{ utils_selfsigned_ssl_cert_name }}.pem'` | File name for the SSL certificate PEM file.
`utils_selfsigned_ssl_ca_passphrase` | `'default_passphrase'` | Passphrase for the Certificate Authority.
`utils_selfsigned_ssl_cert_dns_name` | `"{{ ansible_fqdn }}"` | DNS name for the SSL certificate, defaults to the fully qualified domain name of the host.
`utils_selfsigned_ssl_ca_owner` | `'root'` | Owner of the CA certificate and key files.
`utils_selfsigned_ssl_ca_group` | `'root'` | Group owner of the CA certificate and key files.
`utils_selfsigned_ssl_cert_owner` | `'root'` | Owner of the SSL certificate and key files.
`utils_selfsigned_ssl_cert_group` | `'root'` | Group owner of the SSL certificate and key files.

Dependencies
------------
<!-- List dependencies on other roles or criteria -->
None

Example Playbook
----------------

```yaml
- name: Use diademiemi.selfsigned_ssl role
  hosts: "{{ target | default('selfsigned_ssl') }}"
  roles:
    - role: "diademiemi.selfsigned_ssl"
      tags: ['diademiemi', 'selfsigned_ssl', 'setup']    ```

```

License
-------

MIT

Author Information
------------------

- diademiemi (@diademiemi)

Role Testing
------------

This repository comes with Molecule that run in Podman on the supported platforms.
Install Molecule by running

```bash
pip3 install -r requirements.txt
```

Run the tests with

```bash
molecule test
```

These tests are automatically ran by GitHub Actions on push. If the tests are successful, the role is automatically published to Ansible Galaxy.

