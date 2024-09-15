# Service Management Configuration by User Group

## Introduction

This document outlines the service management configurations required for different user roles. Each group has specific service needs and restrictions to ensure optimal functionality and security.

## Table of Contents

- [Developer](#developer)
- [Public User](#public-user)
- [Manager](#manager)
- [DevOps Engineer](#devops-engineer)
- [Summary](#summary)

## Developer

### Services to Keep

- **SSH:** Useful for remote access during development.
- **Docker/Podman:** Essential for containerized development and testing.
- **Local Development Tools:** Services such as local databases or web servers needed for development.

### Services to Disable

- **CUPS:** Disable unless necessary for printing during development.
- **Bluetooth:** Generally unnecessary unless development involves Bluetooth technology.
- **Samba:** Disable unless working in a mixed-OS environment where file sharing with Windows is required.

#### Example Configuration

```yaml
unnecessary_services:
  - name: cups
  - name: bluetooth
  - name: samba
```
## Public User
### Services to Keep

- **Minimal Network Services:** Only necessary services for kiosk or public terminal functionality.
- **Web Server:** If the user needs to access or display information via a web interface.

### Services to Disable

- **SSH:** Disable unless remote management is necessary, which should be tightly controlled.
- **FTP/TFTP:** Disable as file transfers are generally not needed for public users.
- **Bluetooth:** Disable unless specifically required for the public terminal.
- **Telnet:** Should be replaced with secure alternatives like SSH if remote access is needed.

#### Example Configuration

```yaml
unnecessary_services:
  - name: ssh
  - name: ftp
  - name: tftp
  - name: bluetooth
  - name: telnet
```
## Manager

### Services to Keep

- **SSH:** For remote management and access if necessary.
- **Email Services:** For communication.
- **File Sharing Services:** If required for document sharing (e.g., Samba if working with Windows environments).

### Services to Disable

- **Bluetooth:** Disable unless needed for specific hardware interactions.
- **CUPS:** Disable if printing is not required.
- **Avahi-daemon:** Disable unless network service discovery is needed.

#### Example Configuration

```yaml
unnecessary_services:
  - name: bluetooth
  - name: cups
  - name: avahi-daemon
```
## DevOps Engineer

### Services to Keep

- **SSH:** Essential for remote access and management.
- **Docker/Podman:** For container management and orchestration.
- **Kubernetes Services:** For managing containerized applications.
- **Monitoring Tools:** Such as Prometheus, Grafana, and security tools like Trivy.

### Services to Disable

- **Bluetooth:** Generally unnecessary unless interacting with specific devices.
- **CUPS:** Disable unless necessary for printing requirements.
- **Avahi-daemon:** Disable unless network service discovery is relevant for specific DevOps tasks.
- **Telnet:** Insecure protocol, should be replaced with SSH if remote access is necessary.

#### Example Configuration

```yaml
unnecessary_services:
  - name: bluetooth
  - name: cups
  - name: avahi-daemon
  - name: telnet
```
## Summary

Each group requires a tailored approach to services:

- **Developers:**  need services for development and container management.
- **Public users:** require minimal services, focusing on functionality specific to public access.
- **Managers:** need access tools and communication services but can generally avoid more specialized or development-oriented services.
- **DevOps Engineers:** need robust management and monitoring tools but should avoid unnecessary services that could introduce security risks.

