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

## add-group.yaml

Adds group(s) to a Keycloak Realm. 

Specifying groups in inventory:
```
all:
  hosts:
  children:
    keycloak:
      hosts:
        localhost:
          ansible_connection: local
      vars:
        keycloak_groups:
        - test_group
        - new_group
```