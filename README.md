# ansible-playbook-bootstrap

On the Ansible Controller:
Clone the playbook.

```
git clone https://github.com/UMNET-perfSONAR/ansible-playbook-bootstrap.git
cd ansible-playbook-bootstrap
```

Get the required roles.

```
ansible-galaxy install -f -r requirements.yml --ignore-errors
```

Now either create an inventory or use an existing one.

```
mkdir -p inventory/group_vars/all/
cp roles/ansible-role-bootstrap-dell/defaults/main.yml \
  inventory/group_vars/all/bootstrap.yml
vi inventory/group_vars/all/bootstrap.yml
```

Ansible ping the targets.

```
ansible all \
  --user root \
  --ask-pass \
  --inventory inventory \
  -m ping
```

Execute Ansible script to bootstrap the targets.

```
ansible-playbook \
  --user root \
  --ask-pass \
  --inventory inventory \
  bootstrap.yml
```

```
ansible-playbook \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --user root \
  --ask-pass \
  bootstrap.yml \
  --limit 198.111.224.149
```

  --limit 198.111.224.149

```
ansible-playbook \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --become \
  --become-method su \
  --become-user root \
  --ask-become-pass \
  bootstrap.yml \
  --limit 141.213.137.132
```
  --limit 198.111.224.149

RPi Bootstrap:
install ubuntu 18
ssh ubuntu@ip_addr
change password
sudo -s
passwd

```
ansible-playbook \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --user ubuntu \
  --ask-pass \
  --become \
  --become-method sudo \
  --become-user root \
  --ask-become-pass \
  bootstrap.yml \
  --limit 198.111.226.185
```
