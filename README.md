# Ansible Grafana

This role is used to configure Grafana.

## Dependencies

collections:
community.grafana

## Role Variables

| Variable                 | Required | Default  |
| -------------------------| -------- | ---------|
| **grafana**
| url                      | yes      |
| url_username             | yes      |
| url_password             | yes      |
| **grafana_folder**
| grafana_folder           | no       |
| title                    | yes      |
| **grafana_datasource**
| grafana_datasource       | no       |
| name                     | yes      |
| ds_type                  | no       |
| ds_url                   | no       |
| tls_skip_verify          | no       |

## Example Playbook

```bash
---
- hosts: localhost
  gather_facts: false
  roles:
    - grafana
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
      - myservice
```
