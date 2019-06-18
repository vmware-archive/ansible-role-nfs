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

Copyright 2015 VMware, Inc.  All rights reserved.

SPDX-License-Identifier: Apache-2.0 OR GPL-3.0-only

This code is Dual Licensed Apache-2.0 or GPLv3

## Author Information

This role was created in 2015 by [Tom Hite / VMware](http://www.vmware.com/).
