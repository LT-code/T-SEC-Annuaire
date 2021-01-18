# Ansible playbook to setup a LDAP infrastructure

#
This is an Ansible-Playbook for the great mail server setup described in this tutorial: https://thomas-leister.de/mailserver-debian-stretch/ written by Thomas Leister.

## Run

```
ansible-playbook -i ./hosts site.yml --ask-vault-pass
```

## Requirements

- Ansible >= 2.7
- Debian Stretch server
- SSH key to login to the server
- Public domain resolving to the server

## Mail Server

#### Variables

All variables are stored in `group_vars/all/vars.yml`. Set the values according to your server.

#### Credentials

Credentials are stored in [group_vars/all/vault.yml](group_vars/all/vault.yml).

#### Keys

- The DKIM-Key ist stored as vault file [roles/rspamd/files/2019.key](roles/rspamd/files/2019.key). The key was generated with :
```
rspamadm dkim_keygen -b 2048 -s 2019 -k 2019.key > 2019.txt
```


