# Ansible playbooks for Keycloak

This repo contains [Ansible](https://www.ansible.com) [playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html) for [Keycloak](https://www.keycloak.org)

## add-user.yaml

Adds user(s) to a Keycloak Realm. Supports adding client roles and groups.

User definition:
```
- username: user
  firstname: user
  lastname: name
  email: example@example.org
  enabled: true
  clientroles:
  - client: client-name
    role: role-name
  groups:
  - group
```
