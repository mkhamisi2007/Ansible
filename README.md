apt install software-properties-common
add-apt-repository --yes --update ppa:ansible/ansible
apt install ansible
apt install ansible-core
----------------------------
ssh-keygen -t rsa
ssh-copy-id root@192.168.1.21
----------------------------
ansible -m ping 192.168.1.21
ansible -m shell -a 'ls /home' 192.168.1.21
ansible -m setup 192.168.1.21
ansible -m setup -a 'filter=ansible_user_id' 192.168.1.21
ansible -m setup -a 'filter=ansible_user_id' app-servers
ansible -m setup -a 'filter=ansible_os_family' app-servers
ansible -m setup -a 'filter=ansible_os_family' app-servers --limit 192.168.1.21
ansible -m setup -a 'filter=ansible_os_family,ansible_user_id' my-client
ansible -m apt -a 'name=apache2 state=present' app-servers 
ansible -m apt -a 'name=apache2 state=present' app-servers --user root
ansible -m apt -a 'name=ca-certificates state=present' app-servers --useruser1 -b -K
ansible -m apt -a 'name=apache2 state=absent' my-client
ansible-config init --disabled > ansible.cfg
ansible-playbook -i inventory/hosts myproject.yaml
ansible-playbook -I inventory/hosts myproject.yaml  -v 
ansible-playbook -I inventory/hosts myproject.yaml  -v --tag create-directory,create-file
ansible-playbook -I inventory/hosts myproject.yaml  -v --skip-tags create-directory
ansible-playbook -I inventory/hosts myproject.yaml --step
ansible-playbook -I inventory/hosts myproject.yaml --list-tasks
ansible-playbook -I inventory/hosts myproject.yaml --extra-vars "myvar=123"
ansible-playbook -I inventory/hosts myproject.yaml -e myvar=test
ansible-playbook -I inventory/hosts myproject.yaml --syntax-check
ansible-playbook -I inventory/hosts myproject.yaml --check
ansible-playbook -I inventory/hosts myproject.yaml --start-at-task "create a .."
ansible-playbook -I inventory/hosts myproject.yaml --diff
ansible-vault create secret.yml
ansible-vault edit secret.yml
ansible-vault encrypt var.yml
ansible-vault decrypt secret.yml
ansible-playbook playbook.yaml --ask-vault-pass
ansible-vault encrypt vars.yaml --vault-password-file .vault_pass
ansible-galaxy search nginx
ansible-galaxy install nginxinc.nginx
ansible-galaxy init sample

