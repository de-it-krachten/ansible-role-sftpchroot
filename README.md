[![CI](https://github.com/de-it-krachten/ansible-role-sftpchroot/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-sftpchroot/actions?query=workflow%3ACI)


# ansible-role-sftpchroot

Setup user access using sftp in a chrooted environment.



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 35
- Fedora 36

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
sftpchroot_root: /chroot

sftpchroot_group: sftpusers

sftpchroot_users: []
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'sftpchroot'
  hosts: all
  become: "yes"
  vars:
    sftpchroot_users: [{'name': 'test1', 'password': 'Abcd1234'}, {'name': 'test2', 'password': 'Abcd1234'}]
  roles:
    - openssh
  tasks:
    - name: Include role 'sftpchroot'
      ansible.builtin.include_role:
        name: sftpchroot
</pre></code>
