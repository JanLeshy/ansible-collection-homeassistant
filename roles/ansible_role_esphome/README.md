# ESPHome

This role installs ESPHome on a remote server with all required dependencies.

## Requirements

None

## Role Variables

| Name                  | Default Value | Description                                                                          |
| --------------------- | ------------- | ------------------------------------------------------------------------------------ |
| `esphome_user`        | esphome       | The user which would created and run the esphome installation and service            |
| `esphome_group`       | esphome       | The group which would created                                                        |
| `esphome_port`        | 6052          | the webaccess port                                                                   |
| `esphome_conf_dir`    | /opt/esphome/ | The config path, where ESP Home woud be installed                                    |
| `esphome_version`     |               | The specific version of ESP Home to install                                          |
| `esphome_ui_user`     |               | The username for UI authentication, if not present no authentification whill be used |
| `esphome_ui_password` |               | The password for UI authentication, depends with `esphome_ui_user`                   |

## Dependencies

None

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

minimal playbook.yml example:

---

    - hosts: espserver
      become: true

      roles:
        - ansible_role_esphome

extendet playbook.yml example:

---

    - hosts: esphomeserver
      become: true
      vars:
        esphome_user: esphome
        esphome_group: esphome
        esphome_conf_dir: /opt/esphome
        esphome_port: 6052

      roles:
        - ansible_role_esphome

## License

MIT

## Author Information

Jan Roepke (JanLeshy)
have fun with it, and feel free to contribute or contact me.
