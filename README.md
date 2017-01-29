# Ansible playbooks

Automated server setup and configuration.

## Setup

Put the SSH public key into `/root/.ssh/authorized_keys`.

Install Python 2 since Python 3 is not yet supported for ansible:

```
aptitude install ansible python2.7 python-simplejson
```

## Playbook

```
ansible-playbook site.yml
```
