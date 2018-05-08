# genie-prerequisites
## Description
A simple Ansible role to ensure prerequisite Python libraries are installed for particular Ansible modules.  This role ensures EPEL is installed, which is a requirement to installing the python-pip package.  The python-pip packages enables the availability of a multitude of Python packages for installation.
## Variables
|Variable Name|Default Value|Required|Description|
|:---:|:---:|:---:|:---:|
|`prq_pylibs`|["ansible-tower-cli"]|yes|List of python libraries to install from pip.  This should be a list of python libraries that certain Ansible modules require to run.|
## Playbook Examples
### Standard Role Usage
```yaml
---
- hosts: all
  roles:
    - role: prerequisites
      prq_pylibs:
        - "ansible-tower-cli"
        - "boto"
```
### Imported Role
```yaml
---
- hosts: all
  vars:
    prq_pylibs:
      - "ansible-tower-cli"
      - "boto"
  roles:
    - name: Ensure Ansible Prerequisites are installed
      import_role:
        name: "prerequisites"
```
### Included Role
```yaml
---
- hosts: all
  tasks:
    - name: Ensure Ansible Prerequisites are installed
      include_role:
        name: "prerequisites"
      vars:
        prq_pylibs:
          - "ansible-tower-cli"
          - "boto"
```
## Author
[Andrew J. Huffman](mailto:ahuffman@gmail.com)
