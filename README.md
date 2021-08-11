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
