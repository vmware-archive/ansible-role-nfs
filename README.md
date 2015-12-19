# ansible-role-nfs

[Ansible](https://github.com/ansible/ansible) role for managing NFS exports.
Note that the role formats partitions or other block devices as necessary and
as defined by the role variables.

## Requirements

All exports must already have valid block devices, which are specified in the
role variables.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Exports to provide. Format example:
#  - { device: "/dev/sdb", mount_point: "/exports/management", fstype: "ext4", mount_opts: "noatime", nfs_opts: "172.16.69.0/24(rw,nohide,insecure,no_subtree_check,async)" }
nfs_exports: []
```

## Example playbook

```yaml
---
- hosts: nfsservers
  sudo: True
  connection: local
  roles:
    - nfs
  vars:
    nfs_exports:
      - { device: "/dev/sdb", mount_point: "/exports/management", fstype: "ext4", mount_opts: "noatime", nfs_opts: "172.16.69.0/24(rw,nohide,insecure,no_subtree_check,async)" }
```

# License and Copyright

Copyright 2015 VMware, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Author Information

This role was created in 2015 by [Tom Hite / VMware](http://www.vmware.com/).
