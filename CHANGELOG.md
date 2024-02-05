# CHANGELOG

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
