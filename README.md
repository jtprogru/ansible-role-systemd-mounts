# jtprogru.systemd_mounts

[![Ansible Molecule](https://github.com/jtprogru/ansible-role-systemd-mounts/actions/workflows/molecule.yml/badge.svg)](https://github.com/jtprogru/ansible-role-systemd-mounts/actions/workflows/molecule.yml)
[![Release to Ansible Galaxy](https://github.com/jtprogru/ansible-role-systemd-mounts/actions/workflows/galaxy.yml/badge.svg)](https://github.com/jtprogru/ansible-role-systemd-mounts/actions/workflows/galaxy.yml)
[![TODO 2 Issue](https://github.com/jtprogru/ansible-role-systemd-mounts/actions/workflows/todo.yml/badge.svg)](https://github.com/jtprogru/ansible-role-systemd-mounts/actions/workflows/todo.yml)
![GitHub](https://img.shields.io/github/license/jtprogru/ansible-role-systemd-mounts)
[![Ansible Role](https://img.shields.io/ansible/role/54362)](https://galaxy.ansible.com/jtprogru/ansible-role-systemd-mounts/)
[![GitHub tag](https://img.shields.io/github/tag/jtprogru/ansible-role-systemd-mounts.svg)](https://github.com/jtprogru/ansible-role-systemd-mounts/tags)

Setup mounts as sysemd Service. So you can use mounts as system Servie.

## Role Variables

See [`defaults/main.yml`](defaults/main.yml).

## Example Playbook

This Playbook creates a Systemd Service for mounting Shares. Example playbook:

```yaml
    - hosts: all
      roles:
        - role: jtprogru.systemd_mounts
          mounts:
            myLogDir: # description of the Service
              share: //logserver.local/logs$ # Share to mount from
              mount: /mnt/logs  # Folder to mount in
              type: cifs # mount type (look at mount man page)
              options: domain=local,username=user,password=password,uid=1000,gid=1000 # Options, username...
              automount: true  # If false: the service will mount at boot
                               # if true: Mount when access on the Folder and on boot
            Appdir:
              share: //apps.local/apps$
              mount: /opt/app
              type: nfs
              options: uid=1000
              automount: false
```

## Authors

- Michael Savin
  - :octocat: [@jtprogru](https://www.github.com/jtprogru)
  - :bird: [@jtprogru](https://www.twitter.com/jtprogru)
  - :moneybag: [s11l.me](https://s11l.me)

## License

See [LICENSE](LICENSE.md)
