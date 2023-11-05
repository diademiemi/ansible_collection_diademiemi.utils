Ansible Role Template
=========

[![Molecule test](https://github.com/diademiemi/ansible_collection_diademiemi.utils/actions/workflows/ansible-role-nginx_basic_configs.yml/badge.svg)](https://github.com/diademiemi/ansible_collection_diademiemi.utils/actions/workflows/ansible-role-nginx_basic_configs.yml)

This is an Ansible role to install and configure nginx_basic_configs.

Include more information about nginx_basic_configs in this section.

Requirements
------------
These platforms are supported:
- Ubuntu 20.04
- Ubuntu 22.04
- Debian 10
- Debian 11
- Debian 12
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
`nginx_basic_configs_config_dir` | `"{{ _nginx_basic_configs_config_dir }}"` | Directory for storing Nginx configuration files. Defined in distro-specific vars.
`nginx_basic_configs_config_name` | `"{{ item.config_name }}.conf"` | Name of the Nginx configuration file, derived from the item being processed in a loop.
`nginx_basic_configs_basic_rev_proxies` | `[]` | List of dictionaries describing basic reverse proxy configurations. See below for details.

### `nginx_basic_configs_basic_rev_proxies` Dictionary Description

This is a list of dictionaries, each describing a basic reverse proxy configuration in Nginx.

- `config_name`: The name of the configuration file.
- `server_name`: Server name directive for the Nginx server block.
- `cert_path`: File path of the SSL certificate.
- `key_path`: File path of the SSL certificate key.
- `external_ip`: External IP address to bind to.
- `external_http_port`: External HTTP port.
- `external_https_port`: External HTTPS port.
- `https`: Whether to use HTTPS (true or false).
- `locations`: List of location blocks. Each block is a dictionary that can have the following keys:
  - `location`: The URL pattern this block will handle.
  - `custom`: Whether to only use the `extra_lines` for custom configuration (true or false).
  - `proxy_pass`: The URL to which the traffic will be forwarded.
  - `proxy_standard_headers`: Whether to include standard proxy headers (true or false).
  - `extra_lines`: Additional custom lines for the location block.

Dependencies
------------
<!-- List dependencies on other roles or criteria -->
None

Example Playbook
----------------

```yaml
- name: Use diademiemi.nginx_basic_configs role
  hosts: "{{ target | default('nginx_basic_configs') }}"
  roles:
    - role: "diademiemi.nginx_basic_configs"
      tags: ['diademiemi', 'nginx_basic_configs', 'setup']    ```

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

