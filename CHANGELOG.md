# CHANGELOG

## Version Update 1.5.0

- FEAT[ansible_role_homeassistant]: add get_ha_facts task, this one checks if a current homeassistant installation is available true. checks the HA version and the python version. Now it is possible to update an existing HA installation wihtout using the tag 'update_homeassistent' in your ansible-playbook run command. Also it check the desired Python Version, if only the python version in not te desired version, the python version will be updated.

- FEAT[ansible_role_homeassistant]: python3.12.2 is now the default python version for the homeassistant virtual environment and will be installed, if not available on the system.
You can change the python version with the variable `ha_python_realease`. Available versions can find here [python_versions](https://www.python.org/downloads/source)

- FEAT[ansible_role_homeassistant]: if you want to update the python version on an existing homeassistant installation, it will be create a backup of the current homeassistant installation, before the python version will be updated. Additonal information can be found here [Example](roles/ansible_role_homeassistant/README.md#update)

- DOCS: updated description to code-spell-checker update an existing homeassistant installation, [Example](roles/ansible_role_homeassistant/README.md#update-an-existing-homeassistant-installation)

- CHORE: make the ansible linter happy, resolve warnings and errors

## Version Update 1.4.0

- FEAT[ansible_role_homeassistant]: variable `ha_backup` can now set to absolutew or relative path from the playbook directory to the homeassistant backup file. [Example](roles/ansible_role_homeassistant/README.md#restore-a-backup)

## Version Update 1.3.1

- FIX: esphome service file, the esphome service would be started and loads the configuration file but you cant save your changes, or update the esp devices.

## Version Update 1.3.0

### Role specified changes

#### ansible_role_homeassistant

- set firewall rules, if ufw is installed and enabled on the system, to acceess the webinterface from other devices in the network

- Update the backup restore process, now you can download the backup file from the homeassistant instance and coud  restore it without to untar the file before to get the homeassistant.tar file

- change the ownership after installation in the virtual environment to the user who runs the homeassistant  and esphome instance

#### ansible_role_esphome

- set firewall rules, if ufw is installed and enabled on the system, to acceess the webinterface from other devices in the network

- change the ownership after installation in the virtual environment to the user who runs the instance

## Version Update 1.1.0

- remove submodules from repository and include them directly in the repository:
  - Role Homeassistant
  - Role Esphome

- reduce required ansible version to 2.13.9
- remove molecule tests form the collection, unittests available in the roles

Role Changelogs:
[Homeassistant](roles/ansible-role-homeassistant/CHANGELOG.md)
[ESPHome](roles/ansible-role-esphome/CHANGELOG.md)

## Version Update 1.0.2

- possibility to define a custom delete time for backups, per day or per keep files and combining both values, default is false

## Version Update 1.0.1

- enable service to startup on boot, for the role homeassistant and esphome
