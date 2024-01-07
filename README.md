# Ansible Collection - janleshy.homeassistant

This collection installs and configures Home Assistant and ESPHome, on a remote server with all required dependencies and configures it to run as a service.

## Roles

* [homeassistant](https://github.com/JanLeshy/ansible-role-homeassistant) - Deploy and configure Home Assistant
* [esphome](https://github.com/JanLeshy/ansible-role-esphome) - Deploy and configure ESPHome

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
