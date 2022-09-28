create C:\Users\username\vagrant dir include 'ansible' and 'keys' dir
generate ssh-keygen pair: 'ssh-keygen -t rsa -b 2048' with name 'rsa_key'in the vagrant\keys dir
start machines 'vagrant up'
connect to Ansible node 'vagrant ssh controlnode'
copy ansible dir 'cp -R ansible xpaste_practicum_app'
cnange permissions 'chmod 775 xpaste_practicum_app'
go to the new dir 'cd xpaste_practicum_app'
install ansible galaxy collections and roles: 'ansible-galaxy collection install -r requirements.yml' and 'ansible-galaxy role install -r requirements.yml'
run playbook with parameters: 'ansible-playbook playbook.yml -e "username=***" -e "password=***"'
