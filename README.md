# harden-linux (Enterprise Refactor)

[![ansible-lint](https://github.com/SaraIravani/harden-linux/actions/workflows/ansible-lint.yml/badge.svg)](#)
[![yamllint](https://github.com/SaraIravani/harden-linux/actions/workflows/yamllint.yml/badge.svg)](#)
[![syntax-check](https://github.com/SaraIravani/harden-linux/actions/workflows/syntax-check.yml/badge.svg)](#)
[![molecule](https://github.com/SaraIravani/harden-linux/actions/workflows/molecule.yml/badge.svg)](#)

Production-oriented Ansible automation for Linux baseline hardening with modular roles, CI validation, and safe operational controls.

## Architecture Overview
- `site.yml` orchestrates composable security roles.
- Role defaults are overridable through `group_vars` and environment inventories.
- CI enforces syntax, linting, and Molecule scenario validation.
- Structure is aligned for CIS-style controls and enterprise GitOps pipelines.

## Supported Distributions
- Ubuntu/Debian family
- RHEL-compatible family (RHEL, Rocky, AlmaLinux)

## Project Structure
- `inventories/` staging/production inventory split
- `group_vars/` global and env-specific variables
- `host_vars/` per-host overrides
- `roles/` reusable hardening controls
- `molecule/` local role/playbook validation scenario
- `tests/` compliance test placeholders
- `docs/` architecture and operations docs
- `.github/workflows/` CI gates
- `collections/` local collections path

## Execution Examples
```bash
ansible-galaxy collection install -r requirements.yml
ansible-playbook -i inventories/staging/hosts.yml site.yml --check --diff
ansible-playbook -i inventories/production/hosts.yml site.yml --limit prod-web-01
```

## Inventory Example
```yaml
all:
  children:
    linux:
      hosts:
        prod-web-01:
          ansible_host: 198.51.100.10
          ansible_user: ansible
```

## Security Warning
Apply SSH and firewall controls in maintenance windows. Always run `--check` first and ensure out-of-band access (console/IPMI) to avoid lockout during first rollout.

## Molecule
```bash
pip install ansible molecule molecule-plugins[docker] docker
molecule test
```

## CIS Alignment
This project maps to core CIS Linux concepts including SSH daemon hardening, firewall defaults, password quality, audit logging, sysctl tuning, and patch automation. Validate with your internal benchmark profile and control IDs.

## Rollback Considerations
- SSH config writes include backups.
- Prefer staged rollout by inventory group.
- Keep break-glass access and console login tested.

## Diagrams/Screenshots
- `docs/architecture-diagram.png` (placeholder)
- `docs/pipeline-screenshot.png` (placeholder)
