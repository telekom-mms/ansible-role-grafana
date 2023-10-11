# Ansible Grafana

![telekom-mms/ansible-role-grafana](https://github.com/telekom-mms/ansible-role-grafana/workflows/test/badge.svg)
[![Ansible Role](https://img.shields.io/ansible/role/d/57215)](https://galaxy.ansible.com/telekom_mms/grafana)

Configure Grafana dashboards, folders, datasources, teams and users.

## Dependencies

collections:
community.grafana

## Role Variables

| Variable | Required | Default |
| -------- | -------- | ------- |
| grafana_url | yes |
| grafana_username | yes |
| grafana_password | yes |
| [**grafana_users**](https://docs.ansible.com/ansible/latest/collections/community/grafana/grafana_user_module.html)
| name | yes |
| email | no |
| login | yes |
| password | no |
| is_admin | no |
| state | no |
| [**grafana_organizations**](https://docs.ansible.com/ansible/latest/collections/community/grafana/grafana_organization_module.html)
| name | yes |
| state | no |
| [**grafana_teams**](https://docs.ansible.com/ansible/latest/collections/community/grafana/grafana_team_module.html)
| name | yes |
| email | no |
| members | no |
| state | no |
| enforce_members | no |
| skip_version_check | no |
| [**grafana_datasources**](https://docs.ansible.com/ansible/latest/collections/community/grafana/grafana_datasource_module.html)
| tls_skip_verify | no |
| org_id | no |
| name | yes |
| ds_type | no |
| access | no |
| ds_url | no |
| database | no |
| with_credentials | no |
| is_default | no |
| user | no |
| password | no |
| additional_json_data | no |
| additional_secure_json_data | no |
| [**grafana_folders**](https://docs.ansible.com/ansible/latest/collections/community/grafana/grafana_folder_module.html)
| name | yes |
| state | no |
| skip_version_check | no |
| [**grafana_dashboards**](https://docs.ansible.com/ansible/latest/collections/community/grafana/grafana_dashboard_module.html)
| org_id | no |
| folder | no |
| state | no |
| slug | no |
| uid | no |
| path | no |
| overwrite | no |
| dashboard_id | no |
| dashboard_revision | no |
| commit_message | no |

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

    grafana_datasources:
      - datasource_object:
        - loki
        name: "Loki"
        ds_type: "loki"
        ds_url: "http://127.0.0.1:3100"
        tls_skip_verify: yes
    grafana_folders:
      - folder_object:
        - my_service
        - other_service
```
