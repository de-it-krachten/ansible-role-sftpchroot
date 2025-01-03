[![CI](https://github.com/de-it-krachten/ansible-role-sftpchroot/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-sftpchroot/actions?query=workflow%3ACI)


# ansible-role-sftpchroot

Setup user access using sftp in a chrooted environment.



## Dependencies

#### Roles
None

#### Collections
- ansible.posix

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 40
- Fedora 41

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
  become: 'yes'
  vars:
    sftpchroot_users:
      - name: test1
        authorized_key: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCUi6mvPuL6TerymVJWOoEQu17uXSvzu4/fbQ1T3/3sX4EV+Z1y03mIjl02cMm76fnDrBRVoUM305aJpsV+bk8XsSMMGNYSXY6NkGptInhj+VnTDJM0xNaevWR2oouJy9piaotwa3G06jE9Vg5Ey3Ryx0wM4OjNdHKbPMtx+3hU/LjuP6lOEaR8nj2unS3aPwPCrBXUYgenD+OOsx7SDldb6YQ+vtkQKCfUFVXYA8O0muYwlbUljr/kem4H85X2t7v6fR9yNuL9aflkWkX3l4dMf9R46OP0O/KvG7QdSdU9drIL5sdKSk05h83pdQ1hyJ5cqH5Yt3CXOjYgB6hFqASFvcjMQvIpleMvD5HKYQg+GuEaTjYdkCJD4WDuPokzONFJhNcrEcgh34LmBj8bp7/AGBzH5lIJd/xefrmlz5gewAvC47Dx/JXVgBf2TiBfYeTN0gV3mDJmBqlXEh7ODiI3u0FYLv02SH1z2LIY5fTnR6jkFormTS6r0K9eIwl4gjE=
          test1
      - name: test2
        authorized_key: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC7p2fKzrM+R+1iBIRcfJFiamcHuU+9JZxvpI/L4TQE6ALDjK54EZcYaTTi8pU5E//g3DcaNAJLZqBqL13NQZeDvZfQ9DRYrmTSSO34gZTgH+6C2Hhrn7gMJExkNpIDVuJbv2jL5QAR5Z1WnCWtAEXhHLw+Ku0zPdz+dSsDndqCWPTvjzjbSYxoq17uQWDTkYUlSz5LN98ES6J1yQm8dePEspsIgxZNxWxlO9Ahz8EIhMXq1NOE1XzksHyR4QIHCpp9+d/YkggSuzXIPUpSfh5amVTYiATHJOYTIk9BZo0WQzcQS8D3a7SEm8fKHQ23DncpLUzS91uV0Jg3R2MwOYxtDMDNWciBv9ihIpSBcmSob2+SYCTbzzq0uDq93K2zKjZlNZso2VgjjJ0H8UWxZ01tjv/kZcM4ime166MBWBKGGeS5Ge6fzApPUJLIcQDv6+s3yuYQyLJLIIHwRdmb2b3FIGCnHmCY3/3Rrw2lu2V0Cu2kLyFaG1k09ctrvX2TIL0=
          test2
  roles:
    - deitkrachten.openssh
  tasks:
    - name: Include role 'sftpchroot'
      ansible.builtin.include_role:
        name: sftpchroot
</pre></code>
