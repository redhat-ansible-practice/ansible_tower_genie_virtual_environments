# ansible_tower_genie_virtual_environments
## Description
An Ansible Role to manage virtual environments in Ansible Tower.
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
    - role: "ansible_tower_genie_virtual_environments"
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
        name: "genie-prerequisites"
      vars:
        prq_pylibs:
          - "ansible-tower-cli"
          - "boto"
```
## License
[MIT](LICENSE)

## Author
[Andrew J. Huffman](https://github.com/ahuffman)
