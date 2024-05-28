# Homeassistant

This role installs Home Assistant on a remote server with all required dependencies and configures it to run as a service.

## Requirements

No requirements

## Role Variables

| Name                          | Default Value      | Description                                                                                                                                                                                                                                                                  |
| ----------------------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ha_user`                     | homeassistant      | The user which would created and run the homeassistant installation and service                                                                                                                                                                                              |
| `ha_group`                    | homeassistant      | The group which would created                                                                                                                                                                                                                                                |
| `ha_port`                     | 8123               | the webaccess port                                                                                                                                                                                                                                                           |
| `ha_conf_dir`                 | /srv/homeassistant | The config path, where homeassistant woud be installed                                                                                                                                                                                                                       |
| `ha_ha_work_dir` | /home/`ha_user`/.homeassistant | The homeassistant work directory |
| `ha_log_dir` | /home/`ha_user`/.homeassistant | The homeassistant log directory |
| `ha_version`                  | latest             | A specified homeassistant which would be installed, recommendly use for updated to a higher version if the new version is not next version from the current installation.                                                                                                    |
| `ha_backup`                   | None               | set absolute or relative path from playbook directory to the homeassistant backup file [Restore a backup](#restore-a-backup)                                                                                                                                                 |
| `ha_additional_pi_groups`     | dialout,gpio,i2c   | addiotion requrired groups for the homeassitent installation on a rasperry pi, do not change or overwrite the values                                                                                                                                                         |
| `ha_check_delay`              | 45                 | delay in seconds for waiting if Home Assistent is available                                                                                                                                                                                                                  |
| !deprecated `ha_python` use `ha_python_realease`                  | 3.12.2             | The python version for homeassistant, if not available on the system it will be installed check recommend version [Python](https://www.home-assistant.io/installation/macos#install-home-assistant-core)                                                                     |
| `ha_backup_cron`              | false              | if set to true, it creates an cron entry for your homeassistant user, a custom delete time for backups, per day (var: `ha_backup_delete_after_days`) or per keep files (`ha_backup_delete_after_days`) and combining both values. [Example](#example-to-set-backup-policies) |
| `ha_backup_delete_after_days` | 7                  | delete all backups older definded value in days, if you want delete                                                                                                                                                                                                          |
| `ha_backup_keepfiles`         | 3                  | keep defined value files, regardless the `ha_backup_delete_after_days` value                                                                                                                                                                                                 |
|`ha_python_release`| 3.12.3  | # See <https://www.python.org/downloads/source/> |
|`ha_python_src_dir`| /tmp | download source directory |
|`ha_python_url` | <https://www.python.org/ftp/python/> | Python download URL |
| `ha_backup_ext_inst_dir` | /home/{{ `ha_user` | Backup of existing installation, in case of python backup [Info](#update-the-python-version) |
| `ansible_processor_nproc` | Number of CPU cores | Number of processors for the python build |

## Dependencies

None

## Example to set Backup policies

to config backups for your Homeassistant installation, [Backup Integration](https://www.home-assistant.io/integrations/backup/)
at the moment the backup integration does not support a delete policy, so you can use the cron job from this role to delete old backups.

If you want to delete all backups older than 7 days, and keep the last 3 backups, you can use the following configuration, default values:

```yaml
ha_backup_cron: true
```

If you want to delete all backups older than 10 days, and keep the last 5 backups, you can use the following configuration, default values:

```yaml
ha_backup_cron: true
ha_backup_delete_after_days: 10
ha_backup_keepfiles: 5
```

If you want to delete all backups older than 7 days, regardless of the number of backups, you can use the following configuration:

```yaml
ha_backup_cron: true
ha_backup_delete_after_days: 7
ha_backup_keepfiles: 0
```

## Restore a backup

if you want to get restore your homeassistant [backup](https://www.home-assistant.io/common-tasks/os/#backups), you can use the following configuration, to restore this backup in your new instance:

Example, backup file is in the playbook directory, and named `your_backup.tar`:

```yaml
ha_backup: your_backup.tar
```

Example, backup file is in the tmp dir, and named `your_backup.tar`:

```yaml
ha_backup: /tmp/your_backup.tar
```

you can set the absolute or relative path from the playbook directory to the homeassistant backup file.

## Update

### Update an existing Homeassistant installation

If you want to update your homeassistant installation to a newer version, you can use the following configuration

Example, update to version 2024.01., set `ha_version` to preferred version or leave blank to install 'Latest' available version and run the playbook:

```bash
ansible-playbook -i your_inventory your_homeassistant_playbookname.yml
```

This command will update your homeassistant installation to the specified version, in your virtual environment.

### Update the Python version

If you want to update the python version for your homeassistant installation, you can use the following configuration in your playbook:
`ha_python_release: 3.12.2`

 The desired python version would be downloaded and installed, if not available on the system. The Source for the python version is the [Python Versions]h(ttps://www.python.org/ftp/python/)

If an existing installation is available, the virtual environment will be updated to the new python version, and a backup will be created.
The Backup tored in `ha_backup_existing_installation_dir` , as tar gz File in format `homeassistant-backup-current_date.tar.gz`

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

## minimal playbook.yml example

```yaml
- hosts: homeassistant_server
  become: true

  roles:
    - homeassistant
```

## extended playbook.yml example

```yaml
- hosts: homeassistant_server
  become: true
  vars:
    ha_user: homeassistant
    ha_group: homeassistant
    ha_port: 8123
    ha_conf_dir: /srv/homeassistant
    ha_version: 2023.11.
    ha_backup: core_2022_9_7.tar
    ha_python: 3.12.2
    ha_backup_cron: true
    ha_backup_delete_after_days: 7
    ha_backup_keepfiles: 3

  roles:
    - homeassistant
```

## License

MIT

## Author Information

Jan Roepke (JanLeshy)
have fun with it, and feel free to contribute or contact me.
