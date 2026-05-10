# Security Decisions (Why)

- SSH template uses `validate` command to prevent service restart with invalid syntax.
- SSH config backup enabled for rollback speed.
- Firewall rules always include SSH allow before deny/default policy.
- Sysctl tuning is idempotent through `ansible.posix.sysctl` instead of shell scripts.
- Password policy centralized with strong defaults and inventory-level override support.
