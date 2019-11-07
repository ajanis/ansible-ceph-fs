# Ansible-CephFS

This roles installs CephFS client configurations

<!-- MarkdownTOC -->

- Dependencies
- Requirements
- Role Variables
  - defaults/main.yml
- Example Playbooks
    - Configure CephFS Client
- License
- Author Information

<!-- /MarkdownTOC -->


## Dependencies

None

## Requirements

This role requires Ansible 2.8 or higher, and platform requirements are listed
in the metadata file.

You will need a Ceph storage cluster set up with an appropriate CephFS volume created.

*Note: Ceph Server and CephFS Volume configuration is beyond the scope of this doc*

The ```mdss``` group must be defined in Ansible

If you have an OpenLDAP server deployed via the [ansible-openldap][] role, then you can configure AutoFS (automount) mount options for your NFS shares.

## Role Variables

The variables that can be passed to this role and a brief description about
them are as follows:

### defaults/main.yml
```
use_ldap_automount: False
data_mount_root: /cephdata

```


## Example Playbooks

##### Configure CephFS Client

```
- name: Deploy CephFS client configurations
  hosts: all
  become: True
  tasks:
    - include_role:
        name: common
    - include_role:
        name: ceph-fs
      when:
        - shared_storage
        - storage_backend == "cephfs"

```

## License

MIT

## Author Information

Created by Alan Janis
