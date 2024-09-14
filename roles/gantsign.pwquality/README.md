Ansible Role: pwquality
=======================

[![Tests](https://github.com/gantsign/ansible_role_pwquality/workflows/Tests/badge.svg)](https://github.com/gantsign/ansible_role_pwquality/actions?query=workflow%3ATests)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-gantsign.pwquality-blue.svg)](https://galaxy.ansible.com/gantsign/pwquality)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/gantsign/ansible_role_pwquality/master/LICENSE)

Role to install and configure
[pwquality](https://github.com/libpwquality/libpwquality) for enforcing password
strength. As well as configuring pwquality itself it adds the pwquality module
to the PAM config.

Requirements
------------

* Ansible >= 2.8

* Linux Distribution

    * Debian Family

        * Ubuntu

            * Bionic (18.04)
            * Focal (20.04)

Role Variables
--------------

The following variables will change the behavior of this role (default values
are shown below):

```yaml
# Number of characters in the new password that must not be present in the
# old password.
pwquality_difok: 1

# Minimum acceptable size for the new password (plus one if
# credits are not disabled which is the default). (See pam_cracklib manual.)
# Cannot be set to lower value than 6.
pwquality_minlen: 8

# The maximum credit for having digits in the new password. If less than 0
# it is the minimum number of digits in the new password.
pwquality_dcredit: 0

# The maximum credit for having uppercase characters in the new password.
# If less than 0 it is the minimum number of uppercase characters in the new
# password.
pwquality_ucredit: 0

# The maximum credit for having lowercase characters in the new password.
# If less than 0 it is the minimum number of lowercase characters in the new
# password.
pwquality_lcredit: 0

# The maximum credit for having other characters in the new password.
# If less than 0 it is the minimum number of other characters in the new
# password.
pwquality_ocredit: 0

# The minimum number of required classes of characters for the new
# password (digits, uppercase, lowercase, others).
pwquality_minclass: 0

# The maximum number of allowed consecutive same characters in the new password.
# The check is disabled if the value is 0.
pwquality_maxrepeat: 0

# The maximum number of allowed consecutive characters of the same class in the
# new password.
# The check is disabled if the value is 0.
pwquality_maxclassrepeat: 0

# Whether to check for the words from the passwd entry GECOS string of the user.
# The check is enabled if the value is not 0.
pwquality_gecoscheck: 0

# Path to the cracklib dictionaries. Default is to use the cracklib default.
pwquality_dictpath:
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: gantsign.pwquality
      pwquality_minlen: 16
      pwquality_maxrepeat: 3
```

More Roles From GantSign
------------------------

You can find more roles from GantSign on
[Ansible Galaxy](https://galaxy.ansible.com/gantsign).

Development & Testing
---------------------

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing; the role is unit tested using
[Testinfra](http://testinfra.readthedocs.io/) and
[pytest](http://docs.pytest.org/).

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)

Because the above can be tricky to install, this project includes
[Molecule Wrapper](https://github.com/gantsign/molecule-wrapper). Molecule
Wrapper is a shell script that installs Molecule and it's dependencies (apart
from Linux) and then executes Molecule with the command you pass it.

To test this role using Molecule Wrapper run the following command from the
project root:

```bash
./moleculew test
```

Note: some of the dependencies need `sudo` permission to install.

License
-------

MIT

Author Information
------------------

John Freeman

GantSign Ltd.
Company No. 06109112 (registered in England)
