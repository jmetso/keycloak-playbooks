# Ansible playbooks for Keycloak

This repo contains [Ansible](https://www.ansible.com) [playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html) for [Keycloak](https://www.keycloak.org)

## users.yaml

Manage users in a Keycloak Realm. Supports client roles and groups.

User passwords can be defined through vault with vault_<username>_password. If user password is not defined in vault, a temporary password is set.

User definition:
```
- state: present
  username: user
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

## groups.yaml

Adds and/or deletes group(s) to/from a Keycloak Realm. 

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
        - name: test_group
          state: present
        - name: new_group
          state: absent
```

## add-client.yaml

Adds Keycloak clients to Keycloak Realm.

Realm spec:
```
keycloak_clients:
- state: present # default: present
  client_id: client
  name: <client-name>
  description: Client description
  enabled: True # default: True
  protocol: openid-connect # default: openid-connect
  client_authenticator_type: client-secret # default: client-secret
  standard_flow_enabled: True # default: True
  implicit_flow_enabled: False # default: False
  direct_access_grants_enabled: False # default: False
  root_url: "${authBaseUrl}"
  redirect_uris:
  - https://client.example.com/*
  base_url: /realms/my-realm.com/account/
  full_scope_allowed: True # default: False
```
