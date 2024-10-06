# Installing and Configuring SELinux and AppArmor on Ubuntu 24

## Overview
Installing and configuring SELinux (Security-Enhanced Linux) on Ubuntu 24 can enhance system security. While SELinux is not the default security system for Ubuntu—AppArmor is primarily used—you can still install SELinux for more granular security policies. This document will guide you through the steps to install and configure SELinux, followed by a brief introduction to AppArmor.

## Part 1: Installing and Configuring SELinux on Ubuntu 24
## Overview
This document outlines the steps to install and configure SELinux (Security-Enhanced Linux) on Ubuntu 24. SELinux provides enhanced security policies for managing permissions on a system.

### Step 1: Install SELinux
Update your system’s package index:

```bash
sudo apt update
```

### Step 2: Install SELinux and Related Packages
To install SELinux and its necessary packages, run the following command:

```bash
sudo apt install selinux-basics selinux-utils selinux-policy-default auditd -y
```
### Step 2: Enable SELinux

## Initialize SELinux
Run the following command to initialize the SELinux file system:

```bash
sudo selinux-activate
```
## Configure the System to Boot with SELinux Enabled

Edit the `/etc/selinux/config` file to enable SELinux at boot:

```bash
sudo nano /etc/selinux/config
```
## SELinux Configuration

Ensure the configuration looks like this:

```plaintext
SELINUX=enforcing
SELINUXTYPE=default
```
### You can also set SELINUX=permissive to test SELinux without enforcing policies.
# Part 2: AppArmor – A More Compatible Alternative

If you're looking for a more Ubuntu-native and compatible security solution, AppArmor is easier to use and manage on Ubuntu systems, including Ubuntu 24.

## Step 1: Installing and Configuring AppArmor

AppArmor should already be installed and enabled by default on Ubuntu, but if it's not, you can install it using:

```bash
sudo apt install apparmor apparmor-utils -y
```
### You can manage profiles (which are similar to SELinux policies) for different applications. AppArmor provides predefined profiles for many common services and programs, and you can modify them as needed.

## Step 2: Check AppArmor Status
To check the status of AppArmor, run:
```bash
sudo aa-status
```
## Step 3: Enforce or Complain Mode
AppArmor profiles can be set in either enforce or complain mode:

Enforce: Strictly enforces the security policy.
Complain: Logs violations but does not enforce the policy.
You can switch a profile to complain mode to debug it:
```bash
sudo aa-complain /etc/apparmor.d/usr.sbin.mysqld
```
To enforce the profile:
```bash
sudo aa-enforce /etc/apparmor.d/usr.sbin.mysqld
```
## Step 4: Create or Modify Profiles
AppArmor profiles are located in /etc/apparmor.d/. You can create or modify profiles by editing these files directly.

For example, to modify the Apache profile:
```bash
sudo nano /etc/apparmor.d/usr.sbin.apache2
```
After modifying, reload the profile:
```bash
sudo apparmor_parser -r /etc/apparmor.d/usr.sbin.apache2
```
# Summary of SELinux vs. AppArmor
SELinux: Provides a highly granular security model with strict enforcement. It is often used in enterprise environments requiring advanced security policies. SELinux requires more manual configuration on Ubuntu.

AppArmor: Default to Ubuntu and easier to configure. It provides path-based control and is more tightly integrated with the Ubuntu ecosystem. It’s easier to manage but slightly less granular than SELinux.
