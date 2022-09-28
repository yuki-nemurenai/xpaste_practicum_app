# xpaste_practicum_app
<br />
1. create C:\Users\username\vagrant dir include 'ansible' and 'keys' dir
<br />
2. generate ssh-keygen pair: 'ssh-keygen -t rsa -b 2048' with name 'rsa_key'in the vagrant\keys dir
<br />
3. start machines 'vagrant up'
<br />
4. connect to Ansible node 'vagrant ssh controlnode'
<br />
5. copy ansible dir 'cp -R ansible xpaste_practicum_app'
<br />
6. cnange permissions 'chmod 775 xpaste_practicum_app'
<br />
7. go to the new dir 'cd xpaste_practicum_app'
<br />
8. install ansible galaxy collections and roles: 'ansible-galaxy collection install -r requirements.yml' and 'ansible-galaxy role install -r requirements.yml'
<br />
9. run playbook with parameters: 'ansible-playbook playbook.yml -e "username=***" -e "password=***"'
