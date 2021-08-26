# Ansible Grafana

This role is used to configure Grafana.

## Dependencies

collections:
community.grafana

## Role Variables

| Variable                    | Required | Default
| ----------------------------| -------- | ---------
| **grafana**
| url                         | yes      |
| url_username                | yes      |
| url_password                | yes      |
| **grafana_user**
| name                        | yes      |
| email                       | no       |
| login                       | yes      |
| password                    | no       |
| is_admin                    | no       |
| state                       | no       |
| **grafana_team**
| name                        | yes      |
| email                       | no       |
| members                     | no       |
| state                       | no       |
| enforce_members             | no       |
| skip_version_check          | no       |
| **grafana_datasource**
| tls_skip_verify             | no       |
| org_id                      | no       |
| name                        | yes      |
| ds_type                     | no       |
| access                      | no       |
| ds_url                      | no       |
| database                    | no       |
| with_credentials            | no       |
| is_default                  | no       |
| user                        | no       |
| password                    | no       |
| additional_json_data        | no       |
| additional_secure_json_data | no       |
| **grafana_folder**
| name                        | yes      |
| state                       | no       |
| skip_version_check          | no       |
| **grafana_dashboard**
| org_id                      | no       |
| folder                      | no       |
| state                       | no       |
| slug                        | no       |
| uid                         | no       |
| path                        | no       |
| overwrite                   | no       |
| dashboard_id                | no       |
| dashboard_revision          | no       |
| commit_message              | no       |

## Example Playbook

```bash
---
- hosts: localhost
  gather_facts: false
  collections:
    - community.grafana
  roles:
    - role: grafana
  vars:
    grafana_url: "{{ icinga_url }}/grafanaweb"
    grafana_username: "{{ icinga_user }}"
    grafana_password: "{{ icinga_pass }}"

    grafana_datasource:
      - datasource:
        - loki
        name: "Loki"
        ds_type: "loki"
        ds_url: "http://127.0.0.1:3100"
        tls_skip_verify: yes
    grafana_folder:
      - folder_object:
        - my_service
        - other_service
```
