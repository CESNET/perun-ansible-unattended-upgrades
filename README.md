unattended_upgrades
======================

Ansible Galaxy role [cesnet.unattended_upgrades](https://galaxy.ansible.com/cesnet/unattended_upgrades) that installs unattended-upgrades and configures them to send
errors to root.

Use "--tags config" to run only config.

Requirements
------------

Define the root_email_address variable to contain a valid email address
that will receive errors.

Role Variables
--------------

- unattended_upgrades_origin_patterns - block of lines defining checked repositories, the default is
```yaml
unattended_upgrades_origin_patterns: |2
          "origin=Debian,codename=${distro_codename}";
          "origin=Debian,codename=${distro_codename}-updates";
          "origin=meta@cesnet.cz,a=stable";
```
- unattended_upgrades_blacklist - block of lines defining packages blacklisted from upgrading, default empty

Example Playbook
----------------
```yaml
- hosts: all
  roles:
    - role: cesnet.unattended_upgrades
      vars:
        root_email_address: john.doe@gmail.com
        unattended_upgrades_origin_patterns: |2
                  "origin=Debian,codename=${distro_codename}";
                  "origin=Debian,codename=${distro_codename}-updates";
                  "origin=meta@cesnet.cz,a=stable";
                  "origin=deb.sury.org";
                  "o=LP-PPA-webupd8team-java";
                  "origin=apt.postgresql.org,codename=${distro_codename}-pgdg";
        unattended_upgrades_blacklist: |2
                  "postgresql-11";
                  "slapd";
```
