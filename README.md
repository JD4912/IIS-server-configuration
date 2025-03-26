IIS Management Ansible Role
Automates the installation and configuration of Microsoft IIS on Windows servers.

Overview
This Ansible role sets up IIS, configures websites, manages application pools, and optionally applies SSL certificates for web hosting.

Requirements
Ansible 2.9+
Windows Server (2016/2019/2022)
Windows modules (win_feature, win_iis_website, etc.)
Role Variables
Defaults in defaults/main.yml:

yaml

Collapse

Wrap

Copy
iis_sites:
  - name: "MyApp"
    port: 80
    path: "C:\\inetpub\\wwwroot\\myapp"
    ssl: false
Usage
Example playbook:

yaml

Collapse

Wrap

Copy
- hosts: windows_servers
  roles:
    - role: iis_management
      vars:
        iis_sites:
          - name: "MyApp"
            port: 80
            path: "C:\\inetpub\\myapp"
          - name: "SecureApp"
            port: 443
            path: "C:\\inetpub\\secureapp"
            ssl: true
            cert_thumbprint: "ABC123..."
Tasks
Install IIS and required features.
Configure websites and bindings.
Manage app pools.
Apply SSL (if specified).
License
MIT
