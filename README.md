unattended_upgrades
======================

Ansible Galaxy role [cesnet.unattended_upgrades](https://galaxy.ansible.com/cesnet/unattended_upgrades) that installs unattended-upgrades and configures them to send
errors to root.

Requirements
------------

Define the root_email_address variable to contain a valid email address
that will receive errors.

Role Variables
--------------

- origin_patterns - block of lines defining checked repositories, the default is
```yaml
origin_patterns: |2
          "origin=Debian,codename=${distro_codename}";
          "origin=Debian,codename=${distro_codename}-updates";
          "origin=meta@cesnet.cz,a=stable";
```


Example Playbook
----------------
```yaml
- hosts: all
  roles:
    - role: cesnet.unattended_upgrades
      vars:
        root_email_address: john.doe@gmail.com
        origin_patterns: |2
                  "origin=Debian,codename=${distro_codename}";
                  "origin=Debian,codename=${distro_codename}-updates";
                  "origin=meta@cesnet.cz,a=stable";
                  "origin=deb.sury.org";
                  "o=LP-PPA-webupd8team-java";
```