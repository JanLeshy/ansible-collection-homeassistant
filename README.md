# Ansible Collection - janleshy.homeassistant

This collection installs and configures Home Assistant and ESPHome, on a remote server with all required dependencies and configures it to run as a service.

## Content

* [homeassistant](https://galaxy.ansible.com/ui/repo/published/janleshy/homeassistant/content/role/ansible_role_homeassistant) - Deploy and configure Home Assistant
* [esphome](https://galaxy.ansible.com/ui/repo/published/janleshy/homeassistant/content/role/ansible_role_esphome/) - Deploy and configure ESPHome

## Requirements

Ansible v2.13.9 or newer must be installed, [official install instruction](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Use the collection

Install the collection from Ansible Galaxy:

```bash
ansible-galaxy collection install janleshy.homeassistant
```

to update the collection from Ansible Galaxy:

```bash
ansible-galaxy collection install janleshy.homeassistant --upgrade
```

you can also install from tarball, after downloading the tarball from Ansible Galaxy:

```bash
ansible-galaxy collection install janleshy.homeassistant-1.0.0.tar.gz -p ./collections
```

## USe the Roles

To use the roles check the role README files.
