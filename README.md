
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

This project aims to automate the hardening of Linux systems using Ansible. The playbooks included in this repository help in the implementation of security best practices, configuration management, and compliance requirements.

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
   git clone https://github.com/yourusername/harden-linux.git
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

The monitoring step is crucial for maintaining an overview of your system's health and security. This step integrates with the **Prometheus** and **Grafana** stack, allowing you to visualize metrics and receive alerts on potential issues. Follow the instructions in the ansible-prometheus-grafana-stack repository for detailed setup instructions.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss improvements.

## Acknowledgments

- Inspired by the need for enhanced Linux security practices.
- Special thanks to the open-source community for their contributions.

## Contact

For questions or feedback, feel free to reach out:

- **Email**: sarairavani@outlook.com
- **LinkedIn**: (https://www.linkedin.com/in/sara-iravan)

---

Happy Hardening!
