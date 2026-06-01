# Harden Linux Project

The **Harden Linux** project is a comprehensive Ansible playbook suite designed to enhance the security and compliance of Linux systems. This project includes various configurations, automated updates, and monitoring solutions to help system administrators maintain secure environments.

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Prerequisites](#prerequisites)
4. [Installation](#installation)
5. [Playbook Steps](#playbook-steps)
6. [Monitoring](#monitoring)
7. [License](#license)
8. [Contributing](#contributing)
9. [Acknowledgments](#acknowledgments)
10. [Contact](#contact)

## Overview

This project automates Linux security hardening using Ansible by applying security best practices, compliance checks, monitoring, and system configuration controls. It is designed to help administrators consistently secure multiple Linux servers through Infrastructure as Code principles.

## Design Decisions

- **Role-based structure over a single monolithic playbook** — each security concern 
  (user access, kernel hardening, network security) is an independent role so it can 
  be run selectively, tested in isolation, and reused across projects.

- **Ordered execution matters** — playbooks run in a deliberate sequence: initial 
  assessment first, then base config, then access controls, then network, then 
  auditing. This order prevents dependency failures (e.g. auditing requires auditd 
  to be installed before rules can be applied).

- **Idempotency by design** — every task uses Ansible's declarative modules rather 
  than raw shell commands, so playbooks can be re-run safely without side effects.

- **Monitoring integrated as a final step** — Prometheus and Grafana are deployed 
  after hardening completes so you can verify security posture metrics immediately 
  after a run, not as a separate manual process.

- **Fail2Ban chosen for brute-force protection** — lightweight, no agent required, 
  works with existing sshd logs. Evaluated alternatives (CrowdSec) but Fail2Ban 
  fits better for standalone server environments without centralized log aggregation.

## Architecture

![Harden Linux Architecture]<img width="350" height="290" alt="image" src="https://github.com/user-attachments/assets/ed7a17d4-d8cb-4b1c-9356-8f22f70f3d41" />

## Features

- Initial assessment of the system
- Automated security updates
- User access management
- Password policies
- Service management
- Network security
- File permissions management
- System auditing
- Kernel OS hardening
- Advanced security configurations
- Compliance checks
- Monitoring with Prometheus and Grafana

## Prerequisites

- Ansible installed on your control machine
- Access to the target Linux systems via SSH
- Properly configured inventory file
- Required roles and collections installed (see `ansible.cfg` for details)

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/SaraIravani/harden-linux.git
   cd harden-linux
   ```

2. Edit the `inventory/hosts.ini` file to specify your target hosts.

3. Update `ansible.cfg` with your desired configurations.

## Playbook Steps

The following steps represent the playbooks available in this project:

1. **Initial Assessment**: `initial_assessment.yml`  
   Conducts a preliminary assessment of the system's security posture.

2. **Base Configuration**: `base.yml`  
   Sets up essential configurations and packages on the Linux system.

3. **User Access Management & Password Policies**: `user_access_management.yml` and `password_policies.yml`  
   Manages user access levels and implements strong password policies.

4. **Service Management**: `service_management.yml`  
   Configures services based on user group requirements.

5. **Network Security**: `network_security.yml`  
   Implements network security policies to safeguard the system.

6. **File Permissions Management**: `file_permissions.yml`  
   Ensures correct file permissions to protect sensitive data.

7. **System Auditing**: `system_auditing.yml`  
   Sets up auditing mechanisms to track system changes.

8. **Kernel OS Hardening**: `kernel_os_hardening.yml`  
   Applies kernel hardening techniques to improve security.

9. **Advanced Security Configurations**: `advanced_security.yml`  
   Configures additional security features, such as Fail2Ban.

10. **Compliance Checks**: `compliance.yml`  
    Performs compliance checks against established security benchmarks.

11. **Monitoring**: `monitoring.yml`  
    Integrates with ansible-prometheus-grafana-stack to set up monitoring for system performance and security.

12. **Automated Security Updates**: `automated_updates.yml`  
    Configures unattended upgrades for security patches and system updates.

## Monitoring

The monitoring step is crucial for maintaining an overview of your system's health and security. This step integrates with the [ansible-prometheus-grafana-stack](https://github.com/yourusername/ansible-prometheus-grafana-stack) to set up monitoring for system performance and security.

### Setup Instructions

Follow the instructions in the [ansible-prometheus-grafana-stack](https://github.com/SaraIravani/ansible-prometheus-grafana-stack.git) repository for detailed setup instructions.

### Features

- Visualize metrics from your Linux system.
- Receive alerts on potential issues.
- Monitor system performance and security.

### License

This integration is part of the Harden Linux project and follows the MIT License. See the LICENSE file for more details.


## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss improvements.

## Acknowledgments

- Inspired by the need for enhanced Linux security practices.
- Special thanks to the open-source community for their contributions.

## Contact

For questions or feedback, feel free to reach out:

- **Email**: sarairavani@outlook.com
- **LinkedIn**: (https://www.linkedin.com/in/sara-iravani)

---

Happy Hardening!
