# Sudo/su installation and configuration

Privilege escalation (sudo/su) installation and configuration.

## Requirements

None. The required packages are managed by the role.

## Role Variables

- From `defaults/main.yml`

```yml
---
## Sudo
# Set the package install state for distribution packages
# Options are 'present' and 'latest'
security_package_state: present
```

- From `vars/main.yml`

```yml
---
# RHEL 7 STIG: Packages to add/remove
stig_packages_rhel7:
  - packages:
      - sudo
    state: "{{ security_package_state }}"
    enabled: 'True'
org: 'example.com'
```

## Dependencies

This role depends on `ansible-os-hardening-selinux`.

## Example Playbook

Example of how to use this role:

```yml
    - hosts: servers
      roles:
         - { role: ansible-os-hardening-selinux }
         - { role: ansible-os-hardening-sudo }
```

## License

GPLv3

## Author Information

[David Sastre](david.sastre@redhat.com)
