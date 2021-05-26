# ansible-playbook-bootstrap

On the Ansible Controller:

Clone the playbook

```
git clone https://github.com/UMNET-perfSONAR/ansible-playbook-bootstrap.git
cd ansible-playbook-bootstrap
```

```
ansible-playbook \
  --ask-pass \
  --ask-become-pass \
  -i inventory \
  users.yml
```
