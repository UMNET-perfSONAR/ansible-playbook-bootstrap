# ansible-playbook-bootstrap

On the Ansible Controller:

Clone the playbook

```
git clone https://github.com/UMNET-perfSONAR/ansible-playbook-bootstrap.git
cd ansible-playbook-bootstrap
```

```
ansible all \
  --ask-pass \
  --ask-become-pass \
  --user root \
  -i inventory \
  -m ping
```

Get the required roles (note that we ignore errors so we can run this multiple times):

```
ansible-galaxy install -r  requirements.yml --ignore-errors
```


```
ansible-playbook \
  --ask-pass \
  --ask-become-pass \
  --user root \
  -i inventory \
  hosts_allow_deny.yml
```

```
ansible-playbook \
  --ask-pass \
  --ask-become-pass \
  -i inventory \
  users.yml
```







