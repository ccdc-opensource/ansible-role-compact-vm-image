# ccdc.compact-vm-image

[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-ccdc.compact_vm_image-blue.svg)](https://galaxy.ansible.com/ccdc/compact_vm_image/)
[![Ansible Lint](https://github.com/ccdc-opensource/ansible-role-compact-vm-image/actions/workflows/lint-ansible-role.yml/badge.svg)](https://github.com/ccdc-opensource/ansible-role-compact-vm-image/actions/workflows/lint-ansible-role.yml)
[![Common CCDC PR Checks](https://github.com/ccdc-opensource/ansible-role-compact-vm-image/actions/workflows/common_ccdc_status_checks.yml/badge.svg)](https://github.com/ccdc-opensource/ansible-role-compact-vm-image/actions/workflows/common_ccdc_status_checks.yml)

An Ansible role to compact a target machine's disk for export as a virtual machine image.

## What does this role do?

- [Windows] Clean WinSXS folder and remove package files for uninstalled features
- [Windows] Remove temporary files
- [Windows] Download+Run+Delete UltraDefrag on all hard drives
- [Windows] zero free space using SDelete on all hard drives

## Requirements

This role requires the `[community.windows](https://galaxy.ansible.com/community/windows)` collection.

## Role Variables

| Variable          | Default   | Comments                                                           |
|-------------------|-----------|--------------------------------------------------------------------|
| `remove_packages` | `true`    | Whether to remove package files for uninstalled features (Windows) |
| `temporary_files` | see below | A list of directories to clear out.                                |

### Default value for `temporary_files`

```yaml
temporary_files:
  - "{{ ansible_env.LOCALAPPDATA }}\\Temp\\*"
  - "{{ ansible_env.SystemRoot }}\\Temp\\*"
  - "{{ ansible_env.SystemRoot }}\\Logs\\*"
  - "{{ ansible_env.SystemRoot }}\\Panther\\*"
  - "{{ ansible_env.SystemRoot }}\\WinSxS\\ManifestCache\\*"
  - "{{ ansible_env.SystemRoot }}\\SoftwareDistribution\\Download"
```
