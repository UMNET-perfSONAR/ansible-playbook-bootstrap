vi ../ansible-playbook-perfsonar/ansible-inventory-netbasilisk-perfsonar/inventory/hosts

vi ~/.ssh/known_hosts 
ssh 198.111.224.155

ansible ilab-hosts -m ping

ansible \
  bare-metal \
  --ask-pass \
  -u ubuntu \
  -i ../ansible-inventory-pssid-ilab/inventory \
  -m ping

ansible-playbook \
  --ask-pass \
  --user ubuntu \
  --inventory ../ansible-inventory-pssid-ilab/inventory \
  --limit bare-metal \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-inventory-netbasilisk-perfsonar/inventory \
  --limit ilab-hosts \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-dc-dbn.umd.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-become-pass \
  --become \
  --become-user=root \
  --become-method=su \
  --become \
  --inventory ../ansible-playbook-perfsonar/ansible-inventory-netbasilisk-perfsonar/inventory \
  --limit ilab-hosts \
  bootstrap.yml

ansible \
  perfsonar-bin-arbl.umnet.umich.edu \
  --ask-pass \
  --ask-vault-pass \
  -u root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  -m ping

ansible-playbook \
  --ask-pass \
  --ask-vault-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-bin-arbl.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --ask-vault-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-core-cool.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --ask-vault-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-core-fxb.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --ask-vault-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-core-fxb.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --ask-vault-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-bin-seb.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --ask-vault-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-core-seb.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --ask-vault-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-core-lsa.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-pass \
  --ask-vault-pass \
  --user root \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-dc-macc.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-become-pass \
  --become \
  --become-user=root \
  --become-method=su \
  --become \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-bin-arbl.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-become-pass \
  --become \
  --become-user=root \
  --become-method=su \
  --become \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-bin-arbl.umnet.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-become-pass \
  --become \
  --become-user=root \
  --become-method=su \
  --become \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit perfsonar-dc-dbn.umd.umich.edu \
  bootstrap.yml

ansible-playbook \
  --ask-become-pass \
  --become \
  --become-user=root \
  --become-method=su \
  --become \
  --inventory ../ansible-playbook-perfsonar/ansible-umich-perfsonar-core/inventory \
  --limit 198.111.224.155 \
  bootstrap.yml


# Bootstrap iLab RPis

ansible-playbook \
  --inventory ../ansible-inventory-pssid-ilab/inventory \
  --user ubuntu \
  --ask-pass \
  --become \
  --become-method su \
  --become-user root \
  --ask-become-pass \
  bootstrap.yml
