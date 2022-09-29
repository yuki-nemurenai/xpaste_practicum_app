# xpaste_practicum_app
### Create ***vagrant*** dir including ***ansible*** and ***keys*** dir:
```
mkdir vagrant
midir vagrant\ansible
mkdir vagrant\keys
```
### Generate ssh-keygen pair with name ***rsa_key*** in the ***vagrant\keys*** dir:
```
ssh-keygen -t rsa -b 2048
```
### Start machines:
```
vagrant up
```
### Connect to Ansible node: 
```
vagrant ssh controlnode
```
### Copy ansible dir:
```
cp -R ansible xpaste_practicum_app
```
### Change permissions: 
```
chmod 775 xpaste_practicum_app
```
### Go to the new dir: 
```
cd xpaste_practicum_app
```
### Install ansible galaxy collections and roles:
```
ansible-galaxy collection install -r requirements.yml
ansible-galaxy role install -r requirements.yml
```
### Run playbook with parameters (credentials to access [GitLab Slurm.io Xpaste Repository](https://gitlab.slurm.io/edu/xpaste_practicum))
```
ansible-playbook playbook.yml -e "username=my_username" -e "password=my_password"
```
